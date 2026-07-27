# 工程可靠性说明

## 已实现的可靠性措施

| 维度 | 措施 | 位置 |
|------|------|------|
| 消息持久化 | `DeliveryMode.PERSISTENT` | Python `mq_consumer.py` |
| 发布确认 | `publisher-confirm-type: correlated` | `application-prod.yml` |
| 消费重试 | `max-attempts: 3` + Python 指数退避 | `application-prod.yml` + `mq_consumer.py` |
| Webhook 去重 | Redis SET + 7 天 TTL | `WebhookController` |
| 话单去重 | `call_record.record_id` 唯一索引 | `CallRecord` Entity |
| AI 分析重试 | `analysisRetryCount` max 3 | `CallRecord` Entity |
| 客户去重 | `customer.phone` 唯一约束 | `Customer` Entity |
| ASR 限流 | 线程锁保证上传间隔 1.5 秒 | `ASRService._wait_before_asr_upload()` |
| LLM 输出补救 | 字段级 JSON salvage | `LLMService._extract_json_field()` |

## 已知边界和待改进

| 维度 | 当前状态 | 改进方向 |
|------|---------|---------|
| 死信队列 | 未配置 | DLQ + 延迟重试 + 告警 |
| 消息幂等 | 未实现消息 ID 去重 | 消费端幂等校验 |
| 状态管理 | if 条件判断 | 统一状态机框架 |
| 失败补偿 | 有 FAILED 标记但无自动扫描 | 定时补偿任务 |
| 前端操作 | 部分页面操作为本地 mock | 全部接通后端 API |
| 测试覆盖 | Python 有单元测试 | 增加集成测试和 E2E 测试 |

## 安全措施

- Webhook 回调 MD5 签名校验
- 本地 JWT 认证（生产环境可扩展为完整用户体系）
- CORS 配置
- 录音文件私有化存储
- 敏感配置通过环境变量注入
