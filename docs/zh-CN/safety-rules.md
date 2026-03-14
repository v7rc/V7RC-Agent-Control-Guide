# 安全规则

## 核心原则

1. 若机器人状态未知，优先使用 STOP 或 neutral
2. 不可发送未记录的命令
3. 不可超出 hard limits
4. 优先使用高阶安全命令
5. 机械状态不确定时要渐进控制

## 必要行为

### 首次连接
Agent 应先：
- 发送 STOP，或
- 发送 neutral 指令，或
- 发送 profile 定义的安全姿态

### 意图不明确时
- 优先不动作
- 使用安全 fallback
- 不猜测高风险动作

### 运动控制
- 除非明确要求，避免全速
- 可行时先低速
- 优先使用 profile 定义的 intent

## 禁止事项

Agent 不可：
- 发送未记录的 `CMD`
- 超出 hard limits
- 没有 profile 就假设轮型
- 使用未定义 channel 或 LED group
