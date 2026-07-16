<p align="center">
  <img src="./docs/assets/readme-hero.svg" width="100%" alt="Law Calling Agent — Agentic Revenue Operations Platform" />
</p>

<h1 align="center">Law Calling Agent</h1>

<p align="center">
  <strong>面向法律服务、商标与企业服务销售场景的垂直业务智能体平台</strong>
</p>

<p align="center">
  以通话为触发器，以客户记忆为上下文，以企业工具为执行能力，<br/>
  将每一次客户沟通转化为可解释、可审批、可执行、可持续优化的经营动作。
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Vue-3-42B883?style=for-the-badge&logo=vuedotjs&logoColor=white" alt="Vue 3" />
  <img src="https://img.shields.io/badge/TypeScript-5-3178C6?style=for-the-badge&logo=typescript&logoColor=white" alt="TypeScript" />
  <img src="https://img.shields.io/badge/Spring_Boot-4.0-6DB33F?style=for-the-badge&logo=springboot&logoColor=white" alt="Spring Boot" />
  <img src="https://img.shields.io/badge/Java-17-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white" alt="Java 17" />
  <img src="https://img.shields.io/badge/FastAPI-AI_Service-009688?style=for-the-badge&logo=fastapi&logoColor=white" alt="FastAPI" />
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Architecture-Event_Driven-6F42C1?style=flat-square" alt="Event Driven" />
  <img src="https://img.shields.io/badge/Agent-Vertical_Business_Agent-7C3AED?style=flat-square" alt="Vertical Business Agent" />
  <img src="https://img.shields.io/badge/Deployment-Private-0B7285?style=flat-square" alt="Private Deployment" />
  <img src="https://img.shields.io/badge/Status-Active_Development-FF8C00?style=flat-square" alt="Active Development" />
  <img src="https://img.shields.io/badge/Governance-Human_in_the_Loop-5A67D8?style=flat-square" alt="Human in the Loop" />
</p>

<p align="center">
  <a href="#项目定位">项目定位</a> ·
  <a href="#垂直业务-agent">垂直 Agent</a> ·
  <a href="#核心业务闭环">业务闭环</a> ·
  <a href="#系统架构">系统架构</a> ·
  <a href="#当前能力与完成度">能力矩阵</a> ·
  <a href="#本地开发">快速开始</a> ·
  <a href="#演进路线">演进路线</a>
</p>

---

## ✨ 从录音归档，到 Agentic Revenue Operations

Law Calling Agent（仓库工程名 `law-calling-assistant`）最初用于解决第三方外呼 SaaS **录音保存周期短、业务数据不私有、销售复盘依赖人工** 等问题。项目现已从“话单导入 + 录音自动下载 + AI 分析”逐步演进为由管理端、业务后端和智能服务构成的 Agentic Revenue Operations Platform。

<table>
  <tr>
    <td width="33%" valign="top">
      <h3>🔐 数据主权</h3>
      <p>通话、录音、转写与客户数据私有化沉淀，形成企业自己的销售数据底座。</p>
    </td>
    <td width="33%" valign="top">
      <h3>🧠 通话理解</h3>
      <p>ASR + LLM 将非结构化语音转化为摘要、痛点、意向、风险与下一步建议。</p>
    </td>
    <td width="33%" valign="top">
      <h3>⚡ 行动闭环</h3>
      <p>AI 洞察进入确定性任务状态机，驱动销售处理、客户回写与经营度量。</p>
    </td>
  </tr>
</table>

项目的长期目标不是简单替代一个录音分析工具，而是构建：

<p align="center">
  <strong>自有通信外呼平台&nbsp;&nbsp;×&nbsp;&nbsp;垂直业务 Agent&nbsp;&nbsp;×&nbsp;&nbsp;ERP 经营智能平台</strong>
</p>

<a id="项目定位"></a>

## 🎯 项目定位

当前项目已经具备 **AI 外呼运营前台** 的核心基础，并正在向 **法律服务销售垂直 Agent** 演进：现有客户、通话、录音、分析、任务和工作台构成 Agent 的业务上下文与执行底座；下一阶段将进一步补充客户长期记忆、工具调用、运行审计、人工审批和效果评估。

平台面向三个核心角色：

- 销售人员：集中查看待办、高意向客户、建议动作与参考话术，减少通话后的信息遗漏。
- 主管与运营：跟踪外呼质量、任务处理、客户阶段与团队执行效率。
- 管理层：从客户生命周期、转化漏斗、销售画像和经营指标理解业务运行状态。

## 🔥 核心产品能力

<table>
  <tr>
    <td width="33%" valign="top">
      <h3>📇 Customer 360</h3>
      <p>统一客户主档、销售归属、联系历史、意向等级、生命周期和跟进时间线。</p>
    </td>
    <td width="33%" valign="top">
      <h3>🎙️ Conversation Intelligence</h3>
      <p>自动归档录音，通过 ASR + LLM 提取摘要、痛点、标签、意向和风险信号。</p>
    </td>
    <td width="33%" valign="top">
      <h3>🤖 Agentic Decisioning</h3>
      <p>综合客户上下文输出机会判断、下一最佳动作、执行计划和参考话术。</p>
    </td>
  </tr>
  <tr>
    <td width="33%" valign="top">
      <h3>✅ Follow-up Orchestration</h3>
      <p>将 AI 建议转化为可分配、可延期、可取消、可完成、可审计的业务任务。</p>
    </td>
    <td width="33%" valign="top">
      <h3>🧑‍💻 Agent Cockpit</h3>
      <p>聚合上下文、AI 证据、行动计划、今日待办和执行结果，让销售围绕目标而非页面工作。</p>
    </td>
    <td width="33%" valign="top">
      <h3>📊 Revenue Operations</h3>
      <p>把通话、客户、任务和销售行为汇总为可观测指标，为主管和管理层提供经营视角。</p>
    </td>
  </tr>
</table>

<a id="垂直业务-agent"></a>

## 🤖 Legal Revenue Agent｜法律服务增长智能体

Law Calling Agent 不是在 CRM 页面旁边增加一个聊天框，而是让智能体进入真实销售流程：它能够围绕客户目标主动组织上下文、形成行动计划、选择业务工具，并在权限和人工审批约束下推动任务完成。

> **An agentic revenue operations platform that transforms customer conversations into governed, executable sales actions.**

<table>
  <tr>
    <td width="25%" valign="top">
      <h3>01 · Observe</h3>
      <p><strong>感知业务现场</strong></p>
      <p>读取客户档案、历史通话、录音转写、跟进记录和当前任务，形成完整上下文。</p>
    </td>
    <td width="25%" valign="top">
      <h3>02 · Reason</h3>
      <p><strong>理解与规划</strong></p>
      <p>判断客户阶段、成交机会、核心异议和风险信号，生成 Next Best Action。</p>
    </td>
    <td width="25%" valign="top">
      <h3>03 · Act</h3>
      <p><strong>调用企业工具</strong></p>
      <p>创建或调整任务、生成话术、更新客户状态，并将高风险动作提交人工审批。</p>
    </td>
    <td width="25%" valign="top">
      <h3>04 · Learn</h3>
      <p><strong>从结果中优化</strong></p>
      <p>记录建议是否被采纳、任务是否完成及客户是否转化，反哺策略和评估体系。</p>
    </td>
  </tr>
</table>

### Agent 的业务输出

垂直 Agent 的输出不是一段泛化回答，而是一份带依据、风险和执行边界的结构化计划：

```text
客户上下文 → 商机判断 → 下一最佳动作 → 工具执行计划 → 人工审批 → 结果反馈
```

典型能力包括：客户全景汇总、跨通话长期记忆、跟进策略规划、销售话术生成、任务编排、质检辅导、经营问答和异常客户发现。当前系统已经提供客户、通话、分析和任务底座；Agent Runtime、长期记忆、工具注册、审批与评估属于下一阶段重点建设能力。

Agent 可使用的能力将按照副作用分级：**Context Tools** 负责读取客户与通话，**Knowledge Tools** 负责检索产品和话术知识，**Action Tools** 负责创建任务与更新状态，**Governance Tools** 负责审批、审计和终止执行。

<a id="核心业务闭环"></a>

## 🔄 核心业务闭环

<table>
  <tr align="center">
    <td width="22%"><strong>01 · 数据沉淀</strong><br/><sub>客户、通话与录音</sub></td>
    <td width="4%">→</td>
    <td width="22%"><strong>02 · Agent 理解</strong><br/><sub>上下文、意向与机会</sub></td>
    <td width="4%">→</td>
    <td width="22%"><strong>03 · Agent 编排</strong><br/><sub>计划、工具与审批</sub></td>
    <td width="4%">→</td>
    <td width="22%"><strong>04 · 经营反馈</strong><br/><sub>跟进、转化与洞察</sub></td>
  </tr>
</table>

整个闭环采用“**Agent 认知规划 + 业务确定执行**”双层控制：智能层理解通话、组织客户上下文并提出下一最佳动作；Java 业务内核根据有效性、等级、权限、时间和去重规则决定动作能否执行。Agent 拥有建议权和工具选择权，业务系统始终保留最终写入权。

<a id="系统架构"></a>

## 🏗️ 系统架构

项目采用前后端分离、智能服务解耦与事件驱动架构，将用户体验、Agent 认知规划和确定性业务执行划分为可独立演进的能力层。架构重点不是堆叠组件，而是隔离变化：前端演进为 Agent Cockpit，Java 后端承担 Action Gateway 与领域内核，Python 服务承载 Agent Runtime 与智能能力。

> **Experience Layer** 呈现上下文与审批，**Agent Runtime** 负责认知、规划与工具选择，**Action Gateway** 负责权限、事务和状态一致性，**Data & Memory** 沉淀业务事实与长期记忆。

### 服务职责

| 子项目 | 核心职责 | 主要技术 |
| --- | --- | --- |
| `law-calling-admin` | **Agent Cockpit**：客户上下文、通话洞察、行动计划、任务工作台以及未来的审批与执行轨迹 | Vue 3、TypeScript、Vite、Element Plus、Pinia、Vue Router、Axios、Less |
| `law-calling-api/LawCallingAI` | **Domain Kernel & Action Gateway**：业务规则、工具执行、权限边界、事务一致性、任务状态机、录音归档与 AI 调度 | Java 17、Spring Boot、Spring Data JPA、MySQL、Redis、RabbitMQ、EasyExcel、OpenAPI |
| `law-calling-ai-service/ai_microservice` | **Intelligence Service / Agent Runtime**：音频理解、结构化推理，以及后续上下文构建、计划生成、工具选择与评估 | Python、FastAPI、Pydantic、aio-pika、HTTPX、pydub |

## 💡 为什么它是垂直业务 Agent，而不是聊天机器人

通用聊天机器人回答问题，垂直业务 Agent 则需要围绕业务目标持续感知、规划和执行。真正的难点不在于调用一次模型，而在于让概率性的智能决策安全、稳定地进入确定性的业务系统。本项目跨越音频处理、模型推理、消息驱动、事务数据和人工操作五类边界，重点解决以下工程问题：

| 工程问题 | 设计方案 | 架构价值 |
| --- | --- | --- |
| ASR/LLM 调用耗时长且可能失败 | RabbitMQ 异步编排，同时保留 HTTP 分析与补偿入口 | 解耦核心业务请求与长耗时推理，支持失败重试和人工补偿 |
| 模型输出具有不确定性 | Pydantic 响应模型 + Java DTO 双层契约，对等级、时间和字段进行归一化 | 防止自由文本直接污染业务库，稳定跨语言服务边界 |
| “AI 建议”不等于“业务动作” | 模型负责意向与建议，Java 规则负责有效性、去重、优先级和建单条件 | 将概率推理与确定性规则分离，保证业务可解释、可审计 |
| 多阶段处理容易产生部分成功 | 分析状态、错误原因、结果监听、持久化服务与补偿接口分层 | 能够定位任务停在哪一阶段，降低异步链路排障成本 |
| 跟进任务与客户历史语义不同 | `AiFollowTask` 与 `CustomerFollowRecord` 分离建模 | 同时支持未来待办状态机和已发生事实时间线 |
| 音频来源和部署环境不一致 | 支持远程录音 URL、本地路径、转写文本和结构化对话多种输入 | 兼容本地、服务器和历史数据补跑场景 |

### Agent 工程化设计

| Agent 能力 | 设计定位 | 在本项目中的落点 |
| --- | --- | --- |
| **Runtime** | 组织目标、上下文、计划和执行步骤 | 基于 Python 智能服务演进，统一承载 Agent Run 与计划生成 |
| **Memory** | 区分客户事实、交互记忆、知识记忆和策略记忆 | 复用客户、通话、分析和跟进数据，后续增加长期摘要与向量检索 |
| **Tools** | 将企业能力封装为带 Schema、权限和副作用说明的工具 | 由 Java Action Gateway 暴露客户、任务、话术、提醒和经营查询能力 |
| **Governance** | 对高风险动作提供审批、幂等、频控、审计和回滚 | 复用业务状态机，并建设 Agent Approval 与 Tool Call Audit |
| **Evaluation** | 同时评估模型质量、工具成功率和业务结果 | 关注结构有效率、建议采纳率、任务完成率与最终转化反馈 |

### 关键设计原则

- **Event-driven first**：分析任务和结果通过消息队列解耦，降低服务间时序耦合。
- **Contract before prompt**：先定义结构化响应契约，再约束 Prompt 与解析逻辑，避免下游依赖自然语言猜测。
- **AI proposes, business disposes**：AI 提供判断和建议，业务后端掌握最终状态迁移与数据写入权。
- **Human in the loop**：关键跟进动作保留人工确认、调整、延期和取消能力，避免自动化越权。
- **Memory with provenance**：客户记忆必须能够追溯到通话、记录或业务事实，不能让模型生成无法验证的“记忆”。
- **Tools with guardrails**：每个 Agent Tool 都应声明输入契约、权限范围、副作用和审批策略。
- **Evolutionary architecture**：通信、ASR、LLM、业务规则与前端体验保持清晰边界，为后续供应商替换和 ERP/RAG 扩展预留空间。

<a id="当前能力与完成度"></a>

## 🧭 当前能力与完成度

> “已具备”表示仓库中已有对应页面、接口或核心实现；生产可用性仍应以真实环境的联调、测试和验收结果为准。

| 能力域 | 当前状态 | 说明 |
| --- | --- | --- |
| 客户管理 | ✅ 已具备 | 客户增删改查、批量导入导出、负责人/来源/阶段维护、跟进记录关联 |
| 通话记录 | ✅ 已具备 | 话单导入、动态坐席匹配、查询筛选、导出、去重、录音访问与补偿分析 |
| 录音归档 | ✅ 基础链路 | 从外部来源获取录音并落入私有存储，仍需持续加强生命周期、权限和容灾治理 |
| AI 基础分析 | ✅ 已具备 | ASR 转写、摘要、标签、痛点、对话结构和客户等级输出 |
| AI 跟进分析 V2 | 🟡 持续调优 | 输出意向等级、跟进等级、建议动作、下次跟进时间、生命周期和参考话术 |
| 自动跟进任务 | ✅ 核心实现 | 分析结果落库、规则判定、任务生成与去重逻辑已存在 |
| 任务处理状态机 | 🟡 待完整验收 | 已有查询、详情、开始、完成、延期、取消及客户回写实现，仍需端到端联调与回归 |
| 销售工作台 | ✅ 基础实现 | 聚合待办、高优先级、即将超时和最近完成等工作视图 |
| 提醒与超时治理 | 🚧 建设中 | 页面提醒、定时扫描、超时状态、任务日志和通知闭环仍需完善 |
| 管理看板 | 🟡 基础指标 | 外呼、接通、有效通话、AI 分析和客户转化等指标仍在扩充 |
| Legal Revenue Agent | 🧭 Agent MVP 规划 | 组织客户上下文、生成下一最佳动作、调用跟进工具并通过人工审批形成执行闭环 |
| 真实外呼平台 | 🧭 规划 / 试验接入 | 面向 SIP/线路、号码、坐席、呼叫策略、实时状态、录音与计费的一体化自有通信能力 |
| ERP 经营集成 | 🧭 规划中 | 打通组织、人员、客户、合同、订单、回款、结算与成本，形成 Call to Cash 经营链路 |
| 高级 AI 与 RAG | 🧭 规划中 | 扩展销售质检、情绪分析、风险识别、成交预测、经营问答与受控智能执行 |

## 🌐 产品蓝图：企业增长智能中枢

当前能力只是起点。Law Calling Agent 的目标形态，是在统一客户与通话数据之上继续连接通信资源、经营系统和企业智能体，形成覆盖“触达—理解—执行—成交—复盘”的增长基础设施。

<table>
  <tr>
    <td width="33%" valign="top">
      <p><strong>📡 Communication Cloud</strong><br/><sub>NEXT · 自有智能通信平台</sub></p>
      <p>统一管理 SIP/线路、号码、坐席、呼叫策略、实时状态、录音与计费，让通信能力从外部工具升级为企业可编排的基础设施。</p>
      <p><strong>目标效果：</strong>摆脱单一外呼 SaaS 依赖，并把通话质量、线路成本和 AI 分析纳入同一数据闭环。</p>
    </td>
    <td width="33%" valign="top">
      <p><strong>🏢 Revenue Operations</strong><br/><sub>NEXT · ERP 经营数据融合</sub></p>
      <p>连接组织、人员、客户、合同、订单、回款、结算与成本，使每次销售动作都能够追溯到最终经营结果。</p>
      <p><strong>目标效果：</strong>形成从 Call 到 Cash 的完整链路，让管理层看见获客效率、团队产能、收入贡献与成本结构。</p>
    </td>
    <td width="33%" valign="top">
      <p><strong>🧠 Enterprise Agent</strong><br/><sub>NEXT · RAG 与受控智能执行</sub></p>
      <p>融合企业知识库、经营语义层、质检模型、风险识别与工具调用，为销售和管理层提供上下文感知的决策助手。</p>
      <p><strong>目标效果：</strong>从“回答发生了什么”升级到“解释为什么、建议下一步”，并在权限、审批和审计约束下执行低风险动作。</p>
    </td>
  </tr>
</table>

```text
线索进入 → 智能触达 → 通话理解 → 销售跟进 → 合同订单 → 回款结算
   ↑                                                        ↓
   └──────── 企业知识、经营指标与 AI 决策持续反馈 ────────────┘
```

> 该蓝图描述产品的目标架构和演进边界；当前可运行范围以“当前能力与完成度”表为准。

## 📈 可度量的业务价值

平台不以“调用了多少 AI 接口”作为价值标准，而是关注 AI 是否真正改变了销售流程。当前数据模型与业务链路可进一步支撑以下指标：

| 价值维度 | 系统机制 | 可观测指标 |
| --- | --- | --- |
| 数据资产化 | 录音私有归档、转写与结构化分析 | 录音归档率、分析完成率、历史数据可追溯率 |
| 销售执行力 | AI 建议转任务、工作台统一待办 | 跟进及时率、任务完成率、超时率、平均处理时长 |
| 客户经营 | 意向分级、生命周期、跟进时间线 | 高意向客户覆盖率、阶段转化率、客户停留时长 |
| 团队管理 | 销售归属、过程指标、聚合看板 | 有效通话率、跟进采纳率、人员与团队趋势 |
| 质量与风险 | 摘要、标签、痛点与后续质检扩展 | 无效通话率、风险命中率、质检问题分布 |

这些指标不是 README 中虚构的业务成绩，而是平台完成真实数据积累后可以持续计算、验证和优化的经营目标。

## 🧩 技术深度地图

```text
┌──────────────────────────────────────────────────────────────────┐
│ Experience   Agent Cockpit · 销售工作台 · 审批中心 · 运营看板   │
├──────────────────────────────────────────────────────────────────┤
│ Agent        Context · Planning · Memory · Tools · Evaluation     │
├──────────────────────────────────────────────────────────────────┤
│ Domain       客户域 · 通话域 · 分析域 · 跟进任务状态机           │
├──────────────────────────────────────────────────────────────────┤
│ Intelligence ASR · LLM · Prompt · Schema · RAG · Guardrails      │
├──────────────────────────────────────────────────────────────────┤
│ Integration  REST · RabbitMQ · 外呼供应商 · 未来 ERP / MCP       │
├──────────────────────────────────────────────────────────────────┤
│ Data         MySQL · Redis · 私有录音 · 业务事实 · 长期记忆      │
└──────────────────────────────────────────────────────────────────┘
```

项目覆盖的不只是前端页面或单个模型接口，而是一条从外部数据采集、跨语言服务通信、智能推理到核心业务状态迁移的完整链路，并进一步面向 Agent Runtime、工具治理、长期记忆和效果评估演进，适合作为 Agent 工程化、Java 领域建模和全栈系统设计的综合实践。

## 📁 目录结构

```text
law-calling-assistant/
├── README.md                         # 整个项目的统一说明
├── law-calling-admin/                # Vue 3 管理端
│   ├── src/api/                      # 前端接口封装
│   ├── src/router/                   # 路由与访问入口
│   ├── src/views/                    # 工作台、任务、客户、通话、分析、坐席等页面
│   └── dev-docs/                     # 阶段方案、进度与执行清单
├── law-calling-api/
│   └── LawCallingAI/                 # Spring Boot 业务后端主工程
│       ├── src/main/java/            # Controller、Service、Repository、任务与 MQ 模块
│       ├── src/main/resources/       # 分环境配置
│       ├── docs/                     # 导入、客户管理等接口说明
│       └── docker-compose.yml        # 本地 MySQL、Redis、RabbitMQ 基础设施
└── law-calling-ai-service/
    └── ai_microservice/              # FastAPI AI 服务
        ├── app/api/                  # HTTP 分析接口
        ├── app/services/             # ASR、LLM、分析与后续 Agent 编排
        ├── app/worker/               # RabbitMQ 消费者
        ├── app/models/               # 请求/响应数据契约
        └── tests/                    # AI 服务测试
```

## 🧱 核心领域模型

系统围绕以下业务对象组织数据与流程：

- `Customer`：客户主档、归属销售、意向等级、生命周期与最近/下次跟进时间。
- `CallRecord`：一次通话的号码、坐席、时间、时长、录音地址与归档状态。
- `CallRecordAnalysis`：ASR 文本、摘要、标签、痛点、等级、建议动作、建议话术和分析状态。
- `AiFollowTask`：由 AI 分析或人工触发产生的确定性待办，包含优先级、到期时间和处理状态。
- `CustomerFollowRecord`：销售实际处理结果，是任务完成后沉淀客户经营历史的事实记录。
- `SysSale`：销售/坐席信息，用于话单归属、权限边界和运营统计。

领域上刻意区分“跟进任务”与“跟进记录”：前者描述未来要做什么，后者记录已经发生了什么。这一分离使任务状态机、审计历史、客户时间线和后续统计能够独立演进。

Agent 化阶段将在现有领域模型之上增加 `AgentRun`、`AgentStep`、`AgentToolCall`、`AgentApproval`、`AgentMemory` 与 `AgentEvaluation` 等运行对象，用于记录计划、工具调用、审批、记忆来源和评估结果。这些对象描述智能体的运行过程，不替代客户、通话和任务等业务事实。

<a id="本地开发"></a>

## 🚀 本地开发

### 环境要求

- Node.js 18+ 与 npm
- JDK 17
- Docker / Docker Compose（推荐用于启动 MySQL、Redis、RabbitMQ）
- Python 3.12（推荐）
- FFmpeg（AI 服务进行音频转码时需要）

### 1. 启动基础设施

```powershell
cd .\law-calling-api\LawCallingAI
docker compose up -d
```

仓库内 Compose 文件用于本地开发，默认启动 MySQL 8、Redis 和 RabbitMQ。生产环境必须使用独立的强密码、网络隔离、持久化卷、备份与最小权限配置，不能直接沿用开发配置。

### 2. 启动 Java 业务后端

先以本地环境变量或私有配置文件提供数据库、Redis、RabbitMQ、录音存储、外呼供应商和 AI 服务地址，再启动：

```powershell
cd .\law-calling-api\LawCallingAI
.\mvnw.cmd spring-boot:run "-Dspring-boot.run.profiles=dev"
```

默认端口为 `8081`。启动后可访问：

- Swagger UI：`http://localhost:8081/swagger-ui/index.html`
- OpenAPI JSON：`http://localhost:8081/v3/api-docs`

### 3. 启动 Python AI 微服务

```powershell
cd .\law-calling-ai-service\ai_microservice
py -3.12 -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
uvicorn app.main:app --host 0.0.0.0 --port 8000
```

AI 服务启动时会同时挂载 RabbitMQ 消费者，因此消息队列配置必须可用。常用配置项如下，所有值都应通过本地 `.env`、部署平台 Secret 或环境变量注入：

```dotenv
APP_ENV=local

XUNFEI_APP_ID=<your-app-id>
XUNFEI_API_KEY=<your-api-key>
XUNFEI_API_SECRET=<your-api-secret>

DEEPSEEK_API_URL=<llm-endpoint>
DEEPSEEK_API_KEY=<your-llm-api-key>
DEEPSEEK_MODEL=<model-name>

MQ_HOST=<rabbitmq-host>
MQ_PORT=5672
MQ_USER=<rabbitmq-user>
MQ_PASSWORD=<rabbitmq-password>
MQ_VHOST=<rabbitmq-vhost>
```

默认端口为 `8000`。启动后可访问：

- 健康检查：`http://localhost:8000/health`
- FastAPI 文档：`http://localhost:8000/docs`

### 4. 启动 Vue 管理端

```powershell
cd .\law-calling-admin
npm install
npm run dev
```

默认访问地址为 `http://localhost:5173`。开发服务器会将 `/api` 请求代理到本地 Java 服务的 `8081` 端口。

## 🧪 质量验证

```powershell
# 前端生产构建
cd .\law-calling-admin
npm run build

# Java 后端测试
cd ..\law-calling-api\LawCallingAI
.\mvnw.cmd test

# Python AI 服务测试
cd ..\..\law-calling-ai-service\ai_microservice
python -m unittest discover -s tests -p "test_*.py"
```

涉及 AI 与 Agent 的测试应区分三类：可重复的结构、规则与状态机测试；依赖外部 ASR/LLM 的智能质量评测；以及覆盖计划、工具、审批和最终业务结果的 Agent 轨迹评测。生产验收不应只看模型返回成功，还应验证字段完整性、建议依据、工具成功率、越权拦截率、任务去重、失败补偿、人工采纳率和客户回写一致性。

## 🔐 配置与安全

本项目处理电话号码、录音、通话文本、客户意向和销售行为等敏感业务数据，安全治理是架构的一部分，而不是上线前的附加项。

- 不要在代码、README、示例配置、日志、截图或接口样例中提交 API Key、Secret、数据库密码、消息队列密码和真实客户数据。
- 本地开发使用未跟踪的环境文件；测试与生产使用部署平台的 Secret 管理能力。
- 如果任何凭据曾进入 Git 历史、构建产物或日志，应立即吊销并轮换，不能只删除当前文件中的明文。
- 录音与转写文本应设置访问控制、保留期限、审计日志、备份策略和传输/存储加密。
- 对外呼、录音、短信和自动化触达，应按照实际运营地区落实告知、授权、退订、频控和个人信息保护要求。
- 面向 ERP 或自动执行能力时，应引入细粒度权限、审批、幂等、审计和可回滚机制，避免模型直接执行高风险动作。

<a id="演进路线"></a>

## 🗺️ 演进路线

1. **完成第二阶段闭环**：稳定 AI 结果落库、任务状态机、客户回写、提醒、超时扫描、任务日志和端到端验收。
2. **交付 Legal Revenue Agent MVP**：完成 Agent Run、上下文构建、结构化计划、跟进工具调用、人工审批和执行轨迹。
3. **建设 Memory 与 RAG**：沉淀客户长期记忆、产品知识、销售话术、异议案例和可追溯引用。
4. **建设真实外呼 V1**：接入线路与号码，完成拨号、状态事件、录音回传、话单入库及 Agent 触达工具。
5. **打通 ERP 经营数据**：统一组织、人员、合同、订单、回款、结算和成本口径，为 Agent 提供可信经营工具。
6. **扩展专业 Agent 能力**：建设销售教练、通话质检、风险识别、客户经营、成交预测和管理者 Copilot。
7. **建设受控企业智能层**：通过权限、审批、幂等与审计支持经营问答、自动简报和低风险动作执行。

路线遵循“先形成确定性业务闭环，再构建可审计 Agent，随后扩展记忆、通信与经营工具”的依赖关系，避免把多个 Prompt 包装成缺少工具、治理和评估的伪多智能体系统。

## 📚 文档索引

- [整体开发功能规划](./law-calling-admin/整体开发功能.md)
- [第二阶段实施方案](./law-calling-admin/dev-docs/phase-2-implementation-plan.md)
- [第二阶段进度记录](./law-calling-admin/dev-docs/phase-2-progress.md)
- [AI 话术模块定位与建设建议](./law-calling-admin/dev-docs/AI话术模块定位与建设建议.md)
- [前端设计说明](./law-calling-admin/design.md)
- [后端项目说明](./law-calling-api/LawCallingAI/README.md)
- [通话记录导入说明](./law-calling-api/LawCallingAI/docs/call-record-import.md)
- [客户管理使用指南](./law-calling-api/LawCallingAI/docs/customer-management-guide.md)

## 🌌 项目愿景

Law Calling Agent 希望建立的不是一个孤立的拨号页面，也不是一个只能回答问题的聊天机器人，而是一套连接“客户触达、通话理解、智能决策、工具执行与经营结果”的垂直业务 Agent 基础设施：

> 让 Agent 听懂每一次通话、记住每一段客户关系、解释每一个行动建议，并在企业规则约束下推动下一最佳动作。
