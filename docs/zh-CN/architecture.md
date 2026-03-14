# V7RC AI 机器人控制架构

## 主要组件

- 用户界面
- OpenClaw / LLM Agent
- V7RC Agent Control Guide Repository
- Runtime / App Server
- BLE / 传输层
- V7RC Robot Firmware
- 机器人硬件
- 可选的传感 / 回传数据

## 控制流程

1. 用户发出指令
2. OpenClaw 解读需求
3. Agent 读取 profile 与安全规则
4. 将 intent 转为命令
5. Runtime 通过 BLE 发送命令
6. 固件解析命令
7. 马达、舵机与 LED 执行
8. 可选的 telemetry 回传
