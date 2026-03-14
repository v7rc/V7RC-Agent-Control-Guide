# 總覽

## 目的

本 Repository 定義 AI Agent 應如何安全且一致地控制 V7RC 機器人。

原始 V7RC Protocol 著重於底層訊息格式。
本專案補上：
- 語意化控制說明
- 硬體映射
- 安全邊界
- 可重用的 robot profile
- OpenClaw 等系統的整合方式

## 三層結構

### 第 1 層：Raw protocol
例如：
- `SRT1500150015001500#`
- `SRV1500150015001500#`
- `CMDSTOP           #`

### 第 2 層：硬體映射
例如：
- C1 = 左右移動
- C2 = 前進後退
- C4 = 轉向
- LED = 前方狀態燈

### 第 3 層：Agent Intent
例如：
- `stop`
- `move_forward_slow`
- `turn_left`
- `ready_led`

## 設計原則

1. 安全優先
2. 優先使用明確映射，不做猜測
3. Profile 需可供機器解析
4. 允許不同機型差異
5. 不允許 AI 自創未支援命令
