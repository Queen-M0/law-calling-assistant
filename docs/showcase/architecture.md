# 系统架构说明

## 三端协作架构

```text
┌──────────────────────────────────────────────────────────────┐
│                    Vue 3 前端 (law-calling-admin)              │
│  Element Plus · Vue Router · Axios                            │
│  销售工作台 · 跟进任务 · 通话记录 · 客户管理 · 数据看板        │
└──────────────────────────┬───────────────────────────────────┘
                           │ HTTP (/api → port 8081)
┌──────────────────────────▼───────────────────────────────────┐
│              Java Spring Boot 后端 (law-calling-api)           │
│  Spring Data JPA · MySQL · Redis · RabbitMQ                   │
│  Controller · Service · Repository · MQ Listener · Job        │
└──────────┬───────────────────────────────────┬───────────────┘
           │ RabbitMQ (4 queues)               │ HTTP
           ▼                                    ▼
┌─────────────────────────┐        ┌─────────────────────────┐
│  Python AI 微服务         │        │  第三方外呼平台           │
│  (law-calling-ai-service) │        │  话单拉取 + 外呼发起       │
│  FastAPI · 讯飞 ASR       │        └─────────────────────────┘
│  · DeepSeek LLM           │
│  · aio_pika MQ Consumer   │
└──────────────────────────┘
```

## 事件驱动拓扑

```text
外呼平台 ──Webhook──→ Java 后端
                      │
                      ├─→ ai.analysis.queue ──→ Python ASR + LLM
                      │         ↓
                      │   ai.result.queue ←── Python 结果回传
                      │         ↓
                      ├─→ ai.followup.v2.queue ──→ Python 深度分析
                      │         ↓
                      │   ai.followup.v2.result.queue ←── Python 结果回传
                      │         ↓
                      └─→ 任务自动生成 + 客户状态回写
```

## 数据流

```text
话单导入 → 录音归档 → ASR 转写 → LLM 分析 → 结果落库
                                              ↓
                            跟进任务自动生成 ← 意向/跟进等级判断
                                              ↓
                            销售处理任务 → 客户状态回写 → 跟进记录生成
```
