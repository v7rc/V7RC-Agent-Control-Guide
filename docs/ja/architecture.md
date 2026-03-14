# V7RC AI ロボット制御アーキテクチャ

主な構成要素：
- User Interface
- OpenClaw / LLM Agent
- V7RC Agent Control Guide Repository
- Runtime / App Server
- BLE / Transport
- V7RC Robot Firmware
- Robot Hardware

制御フロー：
ユーザー指示 → Agent 解釈 → profile 読み込み → command 生成 → BLE 送信 → firmware 実行
