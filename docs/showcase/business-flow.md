# 核心业务流程

## 全链路时序

```text
1. 外呼平台产生通话 → Webhook 回调 / 定时拉取
2. Java 后端接收话单 → 匹配销售坐席 → 录音下载归档
3. 投递到 RabbitMQ ai.analysis.queue
4. Python 消费：下载音频 → 讯飞 ASR 转写 → DeepSeek LLM 初步分析
5. 结果回传 ai.result.queue → Java 落库 (CallRecordAnalysis)
6. 投递到 ai.followup.v2.queue（携带转写文本 + 对话结构）
7. Python 消费：DeepSeek LLM 深度跟进分析（7级意向 + 4级跟进 + 建议话术）
8. 结果回传 ai.followup.v2.result.queue → Java 落库
9. Java 规则引擎判断是否生成任务（4个抑制条件）
10. 计算优先级和到期时间 → 创建/更新 AiFollowTask
11. 更新 Customer 快照（意向等级、生命周期、下次跟进时间）
12. 销售在工作台查看待办 → 开始处理 → 完成任务
13. 完成时自动写入 CustomerFollowRecord + 更新 Customer
```

## 任务生成规则

| 意向等级 | 跟进等级 | 优先级 | 默认到期时间 | 是否生成任务 |
|---------|---------|--------|------------|------------|
| A (高意向) | A | HIGH | 24 小时 | ✅ |
| B (强需求) | B | MEDIUM | 3 天 | ✅ |
| C (可培育) | C | LOW | 7 天 | ✅ |
| D (低频再拨) | D | LOW | 7 天 | 条件性 |
| E (弱意向) | D | LOW | 7 天 | 条件性 |
| F (无效/强拒绝) | - | - | - | ❌ |
| G (已成交) | - | - | - | ❌ |

## 任务状态流转

```text
PENDING ──start──→ PROCESSING ──complete──→ DONE
   │                   │
   │                   └──cancel──→ CANCELLED
   │
   └──超时──→ EXPIRED ──start/delay──→ PROCESSING
```

## 客户生命周期

```text
新线索 → 初步接触 → 意向确认 → 需求确认 → 方案沟通 → 商务谈判 → 已成交
                                                              → 已流失
```
