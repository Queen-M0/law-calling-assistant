<p align="center">
  <img src="./docs/assets/readme-hero.svg" width="100%" alt="Law Calling Assistant — AI-native outbound sales infrastructure" />
</p>

<h1 align="center">Law Calling Assistant</h1>

<p align="center">
  <strong>面向法律服务、商标与企业服务销售场景的私有化智能外呼与客户经营平台</strong>
</p>

<p align="center">
  把每一次通话转化为结构化洞察，把每一个 AI 结论转化为可执行任务，<br/>
  把分散的销售动作沉淀为可度量、可追踪、可持续经营的数据资产。
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
  <img src="https://img.shields.io/badge/Deployment-Private-0B7285?style=flat-square" alt="Private Deployment" />
  <img src="https://img.shields.io/badge/Status-Active_Development-FF8C00?style=flat-square" alt="Active Development" />
  <img src="https://img.shields.io/badge/AI-ASR_%2B_LLM-5A67D8?style=flat-square" alt="ASR and LLM" />
</p>

<p align="center">
  <a href="#项目定位">项目定位</a> ·
  <a href="#核心业务闭环">业务闭环</a> ·
  <a href="#系统架构">系统架构</a> ·
  <a href="#当前能力与完成度">能力矩阵</a> ·
  <a href="#本地开发">快速开始</a> ·
  <a href="#演进路线">演进路线</a>
</p>

---

## ✨ 从录音归档，到智能经营

Law Calling Assistant 最初用于解决第三方外呼 SaaS **录音保存周期短、业务数据不私有、销售复盘依赖人工** 等问题。项目现已从“话单导入 + 录音自动下载 + AI 分析”逐步演进为由管理端、业务后端和 AI 微服务构成的销售运营平台。

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
  <strong>自有通信外呼平台&nbsp;&nbsp;×&nbsp;&nbsp;AI 销售运营平台&nbsp;&nbsp;×&nbsp;&nbsp;ERP 经营集成平台</strong>
</p>

<a id="项目定位"></a>

## 🎯 项目定位

当前项目更准确的定位是 **AI 外呼运营前台**：它已经具备客户与通话数据管理、录音归档、ASR/LLM 分析、跟进任务和销售工作台等基础能力，但完整的自有通信底座、ERP 经营集成和企业级智能自动化仍在规划与建设中。

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
      <h3>🤖 AI Decision Support</h3>
      <p>输出跟进等级、建议动作、建议时间和参考话术，辅助销售做出下一步决策。</p>
    </td>
  </tr>
  <tr>
    <td width="33%" valign="top">
      <h3>✅ Follow-up Orchestration</h3>
      <p>将 AI 建议转化为可分配、可延期、可取消、可完成、可审计的业务任务。</p>
    </td>
    <td width="33%" valign="top">
      <h3>🧑‍💻 Sales Workspace</h3>
      <p>聚合今日待办、高优客户、即将超时和最近完成，让销售围绕任务而非页面工作。</p>
    </td>
    <td width="33%" valign="top">
      <h3>📊 Revenue Operations</h3>
      <p>把通话、客户、任务和销售行为汇总为可观测指标，为主管和管理层提供经营视角。</p>
    </td>
  </tr>
</table>

<a id="核心业务闭环"></a>

## 🔄 核心业务闭环

<table>
  <tr align="center">
    <td width="22%"><strong>01 · 数据沉淀</strong><br/><sub>客户、通话与录音</sub></td>
    <td width="4%">→</td>
    <td width="22%"><strong>02 · 智能理解</strong><br/><sub>内容、意向与机会</sub></td>
    <td width="4%">→</td>
    <td width="22%"><strong>03 · 行动编排</strong><br/><sub>任务、策略与协同</sub></td>
    <td width="4%">→</td>
    <td width="22%"><strong>04 · 经营反馈</strong><br/><sub>跟进、转化与洞察</sub></td>
  </tr>
</table>

当前 AI 决策采用“分析判断 + 业务规则”两层模型：AI 输出通话有效性、客户意向等级、跟进等级、跟进必要性、建议时间、建议动作和参考话术；Java 后端再根据有效性、等级、时间与去重规则决定是否真正创建业务任务。AI 负责推理，业务后端负责确定性约束、状态流转和数据一致性。

<a id="系统架构"></a>

## 🏗️ 系统架构

项目采用前后端分离与 AI 微服务解耦架构，将用户体验、核心业务和智能推理划分为可独立演进的能力层。架构重点不是堆叠组件，而是隔离变化：前端围绕销售工作流演进，业务后端维护规则与数据一致性，AI 服务专注非结构化内容理解，并为通信、模型和企业系统扩展保留边界。

> **Experience Layer** 负责业务体验，**Domain Layer** 负责确定性规则，**Intelligence Layer** 负责认知与推理，三者通过稳定契约协作。

### 服务职责

| 子项目 | 核心职责 | 主要技术 |
| --- | --- | --- |
| `law-calling-admin` | 客户、通话、分析、跟进任务、销售工作台与坐席等运营界面 | Vue 3、TypeScript、Vite、Element Plus、Pinia、Vue Router、Axios、Less |
| `law-calling-api/LawCallingAI` | 业务规则、数据一致性、接口聚合、Excel 导入导出、录音归档、任务状态机与 AI 调度 | Java 17、Spring Boot、Spring Data JPA、MySQL、Redis、RabbitMQ、EasyExcel、OpenAPI |
| `law-calling-ai-service/ai_microservice` | 音频预处理、ASR、LLM 分析、结构化输出以及消息队列消费 | Python、FastAPI、Pydantic、aio-pika、HTTPX、pydub |

## 💡 为什么它不只是一个“AI 套壳”

真正的难点不在于调用一次模型，而在于让概率性的 AI 输出安全、稳定地进入确定性的业务系统。本项目跨越音频处理、模型推理、消息驱动、事务数据和人工操作五类边界，重点解决以下工程问题：

| 工程问题 | 设计方案 | 架构价值 |
| --- | --- | --- |
| ASR/LLM 调用耗时长且可能失败 | RabbitMQ 异步编排，同时保留 HTTP 分析与补偿入口 | 解耦核心业务请求与长耗时推理，支持失败重试和人工补偿 |
| 模型输出具有不确定性 | Pydantic 响应模型 + Java DTO 双层契约，对等级、时间和字段进行归一化 | 防止自由文本直接污染业务库，稳定跨语言服务边界 |
| “AI 建议”不等于“业务动作” | 模型负责意向与建议，Java 规则负责有效性、去重、优先级和建单条件 | 将概率推理与确定性规则分离，保证业务可解释、可审计 |
| 多阶段处理容易产生部分成功 | 分析状态、错误原因、结果监听、持久化服务与补偿接口分层 | 能够定位任务停在哪一阶段，降低异步链路排障成本 |
| 跟进任务与客户历史语义不同 | `AiFollowTask` 与 `CustomerFollowRecord` 分离建模 | 同时支持未来待办状态机和已发生事实时间线 |
| 音频来源和部署环境不一致 | 支持远程录音 URL、本地路径、转写文本和结构化对话多种输入 | 兼容本地、服务器和历史数据补跑场景 |

### 关键设计原则

- **Event-driven first**：分析任务和结果通过消息队列解耦，降低服务间时序耦合。
- **Contract before prompt**：先定义结构化响应契约，再约束 Prompt 与解析逻辑，避免下游依赖自然语言猜测。
- **AI proposes, business disposes**：AI 提供判断和建议，业务后端掌握最终状态迁移与数据写入权。
- **Human in the loop**：关键跟进动作保留人工确认、调整、延期和取消能力，避免自动化越权。
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
| 真实外呼平台 | 🧭 规划 / 试验接入 | 面向 SIP/线路、号码、坐席、呼叫策略、实时状态、录音与计费的一体化自有通信能力 |
| ERP 经营集成 | 🧭 规划中 | 打通组织、人员、客户、合同、订单、回款、结算与成本，形成 Call to Cash 经营链路 |
| 高级 AI 与 RAG | 🧭 规划中 | 扩展销售质检、情绪分析、风险识别、成交预测、经营问答与受控智能执行 |

## 🌐 产品蓝图：企业增长智能中枢

当前能力只是起点。Law Calling Assistant 的目标形态，是在统一客户与通话数据之上继续连接通信资源、经营系统和企业智能体，形成覆盖“触达—理解—执行—成交—复盘”的增长基础设施。

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
┌─────────────────────────────────────────────────────────────┐
│ Experience   Vue 3 管理端 · 销售工作台 · 运营看板           │
├─────────────────────────────────────────────────────────────┤
│ Domain       客户域 · 通话域 · 分析域 · 跟进任务状态机       │
├─────────────────────────────────────────────────────────────┤
│ Intelligence ASR · LLM · Prompt · Schema · 规则决策          │
├─────────────────────────────────────────────────────────────┤
│ Integration  REST · RabbitMQ · 外呼供应商 · 未来 ERP / RAG   │
├─────────────────────────────────────────────────────────────┤
│ Data         MySQL · Redis · 私有录音存储 · 审计与指标        │
└─────────────────────────────────────────────────────────────┘
```

项目覆盖的不只是前端页面或单个模型接口，而是一条从外部数据采集、跨语言服务通信、智能推理到核心业务状态迁移的完整链路，适合作为 AI 工程化、Java 业务建模和全栈系统设计的综合实践。

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
        ├── app/services/             # ASR、LLM 与分析编排
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

涉及 AI 结果的测试应区分两类：一类是可重复的结构、规则与状态机测试；另一类是依赖外部 ASR/LLM 的集成评测。生产验收不应只看模型返回成功，还应验证字段完整性、等级一致性、任务去重、失败补偿、客户回写和人工可解释性。

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
2. **建设真实外呼 V1**：接入线路与号码，完成拨号、状态事件、录音回传、话单入库及现有 AI 链路复用。
3. **打通 ERP 基础数据**：优先统一组织、人员、部门、合同、订单、回款、结算和财务成本口径。
4. **扩展高级 AI 能力**：建设销售质检、情绪分析、企业画像、风险识别、客户经营和成交预测。
5. **建设企业智能层**：在统一权限与可信数据之上，引入 RAG 经营问答、自动简报与经过审批的动作执行。

路线遵循“先形成可运行闭环，再扩展通信与经营底座，最后增加高级智能”的依赖关系，避免在业务数据和状态规则尚未稳定时堆叠展示型 AI 功能。

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

Law Calling Assistant 希望建立的不是一个孤立的拨号页面，而是一套连接“客户触达、通话理解、销售执行与经营结果”的业务基础设施：

> 让每一次通话都能被安全沉淀，让每一个 AI 结论都能进入可控流程，让每一个销售动作最终都能被经营数据验证。
