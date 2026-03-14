# OpenClaw 集成指引

## 集成模型

AI Agent 应取得：
1. system prompt
2. 启用中的 robot profile
3. 安全规则
4. intent dictionary
5. 可选的 runtime 状态

## 建议加载

- `docs/zh-CN/safety-rules.md`
- `docs/zh-CN/intent-dictionary.md`
- `docs/zh-CN/robot-profiles/` 内对应文档
- `profiles/` 中对应的 YAML

## 建议流程

1. 识别 robot profile
2. 读取支持的 protocol
3. 读取控制优先顺序
4. 读取支持的 intent
5. 将用户需求转换为已知 intent
6. 生成命令
7. 验证命令
8. 安全发送或拒绝

## 必要规则

Agent 应：
- 不可自创 protocol 名称
- 不可超出 safe limits
- 优先使用已记录的 intent
- 不确定时使用 stop 或 neutral
