# 安全規則

## 核心原則

1. 若機器人狀態未知，優先使用 STOP 或 neutral
2. 不可發送未記錄的命令
3. 不可超出 hard limits
4. 優先用高階安全命令
5. 機械狀態不確定時要漸進控制

## 必要行為

### 首次連線
Agent 應先：
- 發送 STOP，或
- 發送 neutral 指令，或
- 發送 profile 定義的安全姿態

### 意圖不明確時
- 優先不動作
- 使用安全 fallback
- 不猜測高風險動作

### 運動控制
- 除非明確要求，避免全速
- 可行時先低速
- 優先使用 profile 定義的 intent

## 禁止事項

Agent 不可：
- 發送未記錄的 `CMD`
- 超出 hard limits
- 沒有 profile 就假設輪型
- 使用未定義 channel 或 LED group
