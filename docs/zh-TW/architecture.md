# V7RC AI 機器人控制架構

## 主要元件

- 使用者介面
- OpenClaw / LLM Agent
- V7RC Agent Control Guide Repository
- Runtime / App Server
- BLE / 傳輸層
- V7RC Robot Firmware
- 機器人硬體
- 選用的感測 / 回傳資料

## 控制流程

1. 使用者送出指令
2. OpenClaw 解讀需求
3. Agent 讀取 profile 與安全規則
4. 將 intent 轉為命令
5. Runtime 經 BLE 傳送命令
6. 韌體解讀命令
7. 馬達、伺服與 LED 執行
8. 選用的 telemetry 回傳
