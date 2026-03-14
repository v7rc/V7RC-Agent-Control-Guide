# OpenClaw 整合指引

## 整合模型

AI Agent 應取得：
1. system prompt
2. 啟用中的 robot profile
3. 安全規則
4. intent dictionary
5. 選用的 runtime 狀態

## 建議載入

- `docs/zh-TW/safety-rules.md`
- `docs/zh-TW/intent-dictionary.md`
- `docs/zh-TW/robot-profiles/` 內對應文件
- `profiles/` 中對應 YAML

## 建議流程

1. 識別 robot profile
2. 讀取支援的 protocol
3. 讀取控制優先順序
4. 讀取支援的 intent
5. 將使用者需求轉為已知 intent
6. 產生命令
7. 驗證命令
8. 安全送出或拒絕

## 必要規則

Agent 應：
- 不可自創 protocol 名稱
- 不可超出 safe limits
- 優先使用已記錄的 intent
- 不確定時用 stop 或 neutral
