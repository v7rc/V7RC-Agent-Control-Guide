# 履带车基础 Profile

## Metadata
- profile_name: tank_basic
- robot_type: tank_drive
- transport: BLE

## 控制优先顺序
1. CMD
2. SRT
3. SRV
4. SS8

## 运动模型
- Channel1：左右转向
- Channel2：前进 / 后退
- Channel3：保留
- Channel4：可选 yaw trim 或保留
- neutral_value：1500
- safe_range：1200-1800
- hard_range：1000-2000

## 方向规则
- C1 > 1500：向右转向
- C1 < 1500：向左转向
- C2 > 1500：前进
- C2 < 1500：后退

## 常用命令
- neutral：`SRT1500150015001500#`
- 前进：`SRT1500160015001500#`
- 左转：`SRT1400150015001500#`
- 右前：`SRT1600160015001500#`

## 安全注记
- 在没有 firmware 文档前不要使用 C4
- 首次连接先发送 neutral
- 不可超出 hard_range
