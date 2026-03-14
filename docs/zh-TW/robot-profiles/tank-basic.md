# 履帶車基本 Profile


## Metadata
- profile_name: tank_basic
- robot_type: tank_drive
- transport: BLE

## 控制優先順序
1. CMD
2. SRT
3. SRV
4. SS8

## 運動模型
- Channel1：左右轉向
- Channel2：前進 / 後退
- Channel3：保留
- Channel4：選用 yaw trim 或保留
- neutral_value：1500
- safe_range：1200-1800
- hard_range：1000-2000

## 方向規則
- C1 > 1500：向右轉向
- C1 < 1500：向左轉向
- C2 > 1500：前進
- C2 < 1500：後退

## 常用命令
- neutral：`SRT1500150015001500#`
- 前進：`SRT1500160015001500#`
- 左轉：`SRT1400150015001500#`
- 右前：`SRT1600160015001500#`

## 安全註記
- 未有 firmware 文件前不要使用 C4
- 首次連線先送 neutral
- 不可超出 hard_range
