# 能力边界说明

## 已实现能力

| 能力 | 实现方式 | 代码路径 |
|------|---------|---------|
| 话单导入 | Webhook + 定时拉取 | `WebhookController`, `CallRecordPullJob` |
| 录音归档 | 下载到服务器本地磁盘 | `CallRecordingStorageService` |
| ASR 转写 | 讯飞 REST ASR API | `ASRService` (Python) |
| LLM 分析 | DeepSeek Chat JSON Mode | `LLMService` (Python) |
| 两阶段 Pipeline | RabbitMQ 4 队列拓扑 | `RabbitMqConfig`, `mq_consumer` |
| 任务自动生成 | Java 规则引擎 | `FollowTaskServiceImpl` |
| 任务状态机 | Java if 条件判断 | `FollowTaskServiceImpl` |
| 客户状态回写 | Java 直接更新 | `FollowTaskServiceImpl.completeTask()` |
| 销售工作台 | Vue 3 + 后端 API | `workbench/index.vue` |
| 人工任务处理 | 开始/完成/延期/取消 | `FollowTaskController` |

## 尚未实现 / 下一阶段

| 能力 | 当前状态 | 规划方式 |
|------|---------|---------|
| Agent Runtime | 未实现 | AgentRun / Step / ToolCall 数据结构 |
| 动态工具选择 | 未实现 | Tool Registry + Function Calling |
| 长期 Memory | 数据库已有历史数据 | 向量检索 + 长期摘要 |
| RAG | 未实现 | 产品知识库 + 话术库 |
| Agent Eval | 未实现 | 结构有效率 + 建议采纳率 |
| 统一上下文接口 | 数据分散在各 Service | Customer Context Builder |
| 状态机框架 | if 条件判断 | 统一状态机定义 |
| DLQ | 未实现 | 死信队列 + 延迟重试 |
| 消费幂等 | 部分实现 | 消息 ID 去重 |

## 架构边界

- **模型职责**：通话理解和跟进建议（一次性结构化输出）
- **规则职责**：任务生成、优先级映射、状态流转、客户回写
- **人工职责**：任务开始、完成、延期、取消、跟进内容填写
- **当前不包含**：动态多步规划、模型自主选择工具、Agent 运行轨迹记录
