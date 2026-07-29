# MCP Agent 工具总线 MVP：实现与知识手册

> 本文对应仓库中的真实实现，不是未来架构设想。实现时间：2026-07-29。

## 1. 交付边界

本次目标不是建设完整的企业 Agent 平台，而是交付一个可运行、可审计、可演示的 MCP 闭环：

```text
Vue 发起 Agent Run
  → Python Agent Runtime 发现 MCP Tools
  → Mock/DeepSeek 多轮选择并调用工具
  → Java MCP Server 调用既有领域 Service
  → Agent 生成跟进任务草案
  → 人工批准或拒绝
  → Java 校验审批并幂等创建/复用正式任务
  → Python SQLite 保存 Run、Step、ToolCall、Approval 轨迹
```

明确不包含：

- Agent 自动发起真实外呼；
- 完整 OAuth 2.1、RBAC 或多租户权限平台；
- Memory、RAG、Agent Eval；
- 对现有 ASR、固定 JSON 通话分析和 RabbitMQ 流程的改造；
- `complete_follow_task`、`cancel_follow_task`、`update_customer_stage` 等高风险写工具。

## 2. MCP 到底是什么

MCP（Model Context Protocol）是 Agent/模型应用连接外部能力的标准协议。它定义了能力发现、参数 Schema、调用请求和结果返回方式。

本项目中三个核心角色是：

| MCP 角色 | 本项目实现 | 职责 |
| --- | --- | --- |
| Host | Python Agent Runtime | 管理模型、对话、步骤上限、工具策略和运行轨迹 |
| Client | Python 官方 `mcp` SDK | 连接 Java Server，执行初始化、`tools/list` 和 `tools/call` |
| Server | Java 官方 MCP SDK | 声明工具 Schema，接收调用并转发到 Java 领域 Service |

MCP 和模型 Function Calling 不是一回事：

- MCP 解决“应用如何标准化发现和调用外部工具”；
- Function Calling 解决“模型如何表达它想调用哪个函数及参数”；
- Python Runtime 是二者之间的桥：将 MCP Tool Schema 转成 DeepSeek function tools，再把模型工具调用转发给 MCP Client。

## 3. 版本与传输协议

- Java：官方 `io.modelcontextprotocol.sdk:mcp-spring-webmvc:0.17.2`；
- Python：官方 `mcp==1.29.0`；
- 传输：Streamable HTTP；
- MCP Endpoint：`POST/GET/DELETE /mcp`，由 SDK RouterFunction 承载；
- Java 版本：17；
- Spring Boot：现有工程的 4.0.6。

选择 Streamable HTTP 而不是 stdio 的原因：Java 和 Python 是两个长期运行的独立微服务，部署后可能位于不同容器或主机。stdio 更适合桌面客户端拉起本地子进程；旧 SSE 传输也不是本项目新服务的首选。

一次连接的核心协议过程：

```text
Python Client                      Java MCP Server
     |---- initialize ------------------->|
     |<--- serverInfo/capabilities --------|
     |---- notifications/initialized ---->|
     |---- tools/list -------------------->|
     |<--- 7 tools + JSON Schema ----------|
     |---- tools/call(name, arguments) --->|
     |<--- content + structuredContent ----|
```

## 4. 代码结构

### Java MCP Server

```text
law-calling-api/LawCallingAI/src/main/java/org/lawcase/lawcallingai/mcp/
├─ config/McpServerConfiguration.java
├─ controller/McpApprovalController.java
├─ dto/ApprovedFollowTaskCreateDTO.java
├─ entity/McpTaskApproval.java
├─ entity/McpIdempotencyRecord.java
├─ repository/
├─ security/McpInternalAuthFilter.java
├─ McpCallContext.java
├─ McpDomainToolService.java
├─ McpToolException.java
└─ McpToolSchemas.java
```

### Python Agent Runtime

```text
law-calling-ai-service/ai_microservice/app/agent/
├─ runtime.py             # Mock/DeepSeek 多轮工具循环
├─ mcp_client.py          # 官方 MCP Python Client
├─ schemas.py             # Run、NBA、审批契约
├─ tool_policy.py         # 工具 allowlist 和写工具隔离
├─ approval_service.py    # Java 审批决策 + 批准后执行
├─ trace_store.py         # SQLite 轨迹持久化
├─ redaction.py           # 日志/轨迹脱敏
└─ service.py             # API 应用服务
```

### Vue

```text
law-calling-admin/src/
├─ api/agent.ts
└─ views/agent/index.vue
```

## 5. 已实现的 MCP Tools

| Tool | 类型 | 复用的 Java Service | 关键约束 |
| --- | --- | --- | --- |
| `get_customer_context` | 读 | `CustomerService` | 校验客户归属；手机号脱敏；跟进记录限 5 条 |
| `list_customer_calls` | 读 | `CallRecordService` | `limit` 为 1～20；不返回录音 URL、路径或完整转写 |
| `get_call_analysis` | 读 | `CallRecordService` + `CallRecordAnalysisService` | 只取最新分析；转写最多 1000 字符 |
| `list_follow_tasks` | 读 | `FollowTaskService` | 按客户和状态查询；`limit` 为 1～20 |
| `get_follow_task_detail` | 读 | `FollowTaskService` | 清理客户、通话和跟进记录中的敏感字段 |
| `draft_follow_task` | 受控草案 | `CustomerService`、`CallRecordService`、`FollowTaskService` | 只写审批草案，不写 `ai_follow_task` |
| `create_follow_task` | 受控写 | `FollowTaskService.createApprovedAgentTask` | 必须 APPROVED；悲观锁；幂等键；正式事务写入 |

Tool Schema 使用 JSON Schema 描述必填字段、类型、枚举、长度与 `limit` 范围。业务错误不会伪装成成功结果，返回统一结构：

```json
{
  "ok": false,
  "error": {
    "code": "MCP_APPROVAL_REQUIRED",
    "message": "approval must be APPROVED before execution"
  }
}
```

## 6. 为什么工具不能直接操作 Repository

MCP 只是新的调用入口，不应该变成绕过业务内核的后门。因此：

- MCP Tool 先做参数、上下文和数据归属检查；
- 查询与写入调用既有 Java Service；
- 正式任务仍由 `FollowTaskService` 管理状态、去重和事务；
- Python 不复制 Java 的任务状态码或数据库写入规则；
- 外呼供应商 API 没有暴露为 Tool。

`FollowTaskService.createApprovedAgentTask` 会再次验证客户与来源通话归属、到期时间和已有开放任务。若已有开放任务则复用，而不是制造重复待办。

## 7. 多轮 Agent Runtime

### DeepSeek 模式

`runtime.py` 的循环为：

1. MCP `tools/list`；
2. 检查 Server 是否完整提供 7 个预期工具；
3. 只把 5 个读工具和 `draft_follow_task` 转换成 DeepSeek function tools；
4. 调用 DeepSeek；
5. 解析模型返回的 tool calls；
6. 校验工具 allowlist；
7. MCP `tools/call`；
8. 将结果作为 `role=tool` 消息返回模型；
9. 重复至模型给出结构化 NBA 或达到 6 步上限。

模型永远看不到可直接执行的 `create_follow_task`。该工具只允许 `ApprovalService` 在人工批准后调用，即使 Prompt 被注入也无法绕过代码策略。

### Mock 模式

Mock LLM 不是伪造 MCP 返回值。它使用确定性计划真实执行：

```text
get_customer_context
→ list_customer_calls
→ get_call_analysis（存在通话时）
→ list_follow_tasks
→ draft_follow_task
```

因此没有 DeepSeek Key、网络或模型额度时，仍能演示 MCP 握手、工具发现、多个工具调用、真实 MySQL 查询、审批和幂等写入。

## 8. 审批为什么由 Java 保存

Python 保存 Agent 轨迹，但 Java 是正式业务写操作的事实源。若审批只存在 Python，攻击者可以绕开 Python 直接调用 Java 写工具并伪造 `approval_id`。

真实流程如下：

```text
draft_follow_task
  → Java 写 mcp_task_approval(PENDING)
  → Python 写 agent_approval(PENDING)
  → Vue 点击批准
  → Python 调 Java 内部审批 API
  → Java 锁定审批记录并改为 APPROVED
  → Python 调 MCP create_follow_task
  → Java 再次锁定审批记录
  → 校验 saleId、状态和幂等键
  → FollowTaskService 创建/复用任务
  → 写 mcp_idempotency_record
  → 审批改为 EXECUTED
```

拒绝后状态为 `REJECTED`，后续调用写工具会得到 `MCP_APPROVAL_REJECTED`。

## 9. 幂等与并发

`create_follow_task` 同时使用三层保护：

1. `mcp_idempotency_record.idempotency_key` 是主键；
2. 读取审批时使用数据库悲观写锁；
3. 一个审批记录只能关联一个 `task_id`。

同一 `idempotency_key` 重放会返回第一次的 `taskId` 和 `idempotentReplay=true`。同一个 Key 被用于另一个审批则返回 `MCP_IDEMPOTENCY_KEY_CONFLICT`。

## 10. 最小内部认证和权限边界

本地 MVP 使用：

- `X-MCP-Internal-Token`：Python 到 Java 的服务间共享凭据；
- `X-User-Id`：当前操作用户；
- `X-Sale-Id`：当前销售；
- `X-Trace-Id`：Agent Run ID。

Java Filter 使用常量时间比较内部 Token。每个 Tool 再检查客户、通话、任务或审批的 `saleId`。

这是内网 MVP，不是完整生产认证：

- Header 身份由可信 Python 服务传递；
- Vue 当前手工输入 saleId，适合演示，不适合生产；
- 正式部署需要从 JWT/SSO 派生 userId、saleId 和 scopes；
- 服务间凭据需要进入 Secret Manager，并启用 TLS、Token 轮换和网络 ACL。

## 11. 脱敏和轨迹

Java Tool 输出：

- 手机号统一为 `138****0000` 形式；
- 不返回录音地址、服务器路径、供应商 URL；
- 完整 ASR 不返回，只提供最多 1000 字符摘要片段；
- 列表均有硬性 `limit`。

Python 写 SQLite 前递归脱敏：

- Token、Authorization、API Key、Secret、Password → `[REDACTED_SECRET]`；
- Transcript、ASR、Dialogue → `[REDACTED_TRANSCRIPT]`；
- 文本中的大陆手机号自动遮蔽；
- 输入/输出摘要有长度上限。

轨迹表：

| 表 | 内容 |
| --- | --- |
| `agent_run` | 用户目标、客户、销售、模式、最终状态和 NBA |
| `agent_step` | MCP 发现、模型步骤、工具步骤、审批执行步骤 |
| `agent_tool_call` | 工具名、脱敏输入/输出、耗时、状态、错误码、幂等键 |
| `agent_approval` | 草案预览、审批状态、任务 ID |

Java 另外保存 `mcp_task_approval` 与 `mcp_idempotency_record`，作为业务审批和幂等事实源。

## 12. 本地启动

### 12.1 MySQL

本地演示配置默认连接 `127.0.0.1:3306` 的空密码 root。先创建数据库：

```powershell
mysqlsh --sql --user=root --password= --host=127.0.0.1 --port=3306 `
  -e "CREATE DATABASE IF NOT EXISTS law_calling_ai CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci"
```

如果本机账号不同，请只在 `application-mcp-local.yml` 的本地副本或环境变量中覆盖，不要提交密码。

### 12.2 Java MCP Server

```powershell
cd law-calling-api\LawCallingAI
.\mvnw.cmd -DskipTests package
java -jar .\target\LawCallingAI-0.0.1-SNAPSHOT.jar --spring.profiles.active=mcp-local
```

`mcp-local` 会通过 `data-mcp-local.sql` 幂等写入完全虚构的演示数据：

- customerId：`900000000000000001`
- callRecordId：`900000000000000002`
- saleId：`1001`

### 12.3 Python Agent Runtime

```powershell
cd law-calling-ai-service
.\venv\Scripts\python.exe -m pip install -r .\ai_microservice\requirements-agent.txt
$env:APP_DEBUG='false'
$env:MQ_CONSUMER_ENABLED='false'
cd ai_microservice
..\venv\Scripts\python.exe -m uvicorn app.main:app --host 127.0.0.1 --port 8000
```

`MQ_CONSUMER_ENABLED=false` 只用于 Agent-only 本地演示；默认仍为 `true`，原 RabbitMQ 分析消费者行为不变。

### 12.4 Vue

```powershell
cd law-calling-admin
pnpm install
pnpm run dev
```

打开登录后的 `/agent`，填写演示 ID，优先选择 `Mock 演示`。

## 13. 验证命令

```powershell
# Java 全量自动测试；真实讯飞测试默认跳过
cd law-calling-api\LawCallingAI
.\mvnw.cmd test

# 如需手工运行真实讯飞集成测试
$env:RUN_LIVE_ASR_TEST='true'
.\mvnw.cmd -Dtest=LawCallingAiApplicationTests test

# Python 单元测试（含原 ASR/响应模型测试）
cd law-calling-ai-service\ai_microservice
..\venv\Scripts\python.exe -m unittest discover -s tests -p 'test_*.py' -v

# Java 正在以 mcp-local 运行时，执行真实 MCP 闭环验证
..\venv\Scripts\python.exe .\scripts\verify_mcp_mvp.py

# Vue 构建
cd ..\..\law-calling-admin
pnpm run build
```

`verify_mcp_mvp.py` 会验证：7 个工具发现、真实测试数据读取、手机号脱敏、销售越权拒绝、未审批拒绝、批准执行、拒绝分支、幂等重放和轨迹。

## 14. 如何在面试中讲这套实现

建议按以下顺序：

1. 原系统已有 Java 领域服务与 Python LLM 分析，但模型不能动态发现业务能力；
2. 使用 MCP 把客户、通话、分析、跟进任务包装成标准化工具；
3. Java 作为 Server，避免 Python 复制权限、事务和状态规则；
4. Python 作为 Host/Client，把 MCP Schema 桥接成 DeepSeek Function Calling；
5. 模型只允许读和生成草案，正式写入由人工审批触发；
6. 用数据库锁、唯一幂等键和审批状态机解决重复点击与并发执行；
7. 用 SQLite 记录可审计轨迹，并在写入前做字段级脱敏；
8. 用 Mock LLM 保证无模型网络时仍能真实演示 MCP 链路。

容易被追问的知识点：

- MCP Host、Client、Server 的区别；
- MCP Tool Calling 与模型 Function Calling 的区别；
- 为什么使用 Streamable HTTP；
- 为什么审批不能只存在 Python；
- Prompt Injection 为什么不能只靠系统提示词防御；
- 幂等键、数据库唯一约束和悲观锁分别解决什么问题；
- MCP 本身为什么不能替代领域权限；
- 为什么 Mock LLM 仍然可以证明 MCP 链路真实可用。

## 15. 当前真实限制

- DeepSeek 多轮 Tool Calling 代码已实现，但自动验收使用 Mock 模式，未把真实模型调用计入通过结果；
- Python SQLite 适合单机 MVP，多实例部署需迁移至 MySQL/PostgreSQL；
- Vue 的 saleId 为手工输入，生产环境必须从登录身份中获取；
- 内部认证是共享 Token，不是 OAuth；
- 没有 Tool 指标看板、分布式 Trace、Eval、Memory 和 RAG；
- 尚未开放任何真实外呼工具。

## 16. 简历候选描述

> 基于官方 MCP Java/Python SDK为智能外呼平台构建 Agent 工具总线，采用 Streamable HTTP 将 5 个客户/通话/任务只读能力与 2 个受控任务工具标准化；实现 DeepSeek 多轮 Tool Calling、人工审批、销售数据隔离、数据库悲观锁与幂等执行，并以 AgentRun/Step/ToolCall/Approval 轨迹及 Mock LLM 模式完成可审计、可离线演示的端到端闭环。

## 17. 安全提醒

仓库现有配置中仍有历史硬编码的模型和第三方凭据。按照当前本地开发决定，本次没有删除这些值，但它们已经出现在 Git 历史中，应视为泄露。正式展示或推送仓库前必须：撤销旧凭据、生成新凭据、迁移至环境变量/Secret Manager，并对 Git 历史做密钥清理。
