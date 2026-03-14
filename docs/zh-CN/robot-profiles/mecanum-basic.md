# 麦克纳姆基础 Profile

## Metadata
- profile_name: mecanum_basic
- robot_type: mecanum_car
- transport: BLE

## 控制优先顺序
1. CMD
2. SRT
3. SRV
4. SS8

## 运动模型
- Channel1：左右平移
- Channel2：前进 / 后退
- Channel3：保留
- Channel4：转向 / 旋转
- neutral_value：1500
- safe_range：1200-1800
- hard_range：1000-2000

## 方向规则
- C1 > 1500：向右
- C1 < 1500：向左
- C2 > 1500：前进
- C2 < 1500：后退
- C4 > 1500：右转
- C4 < 1500：左转

## 常用命令
- neutral：`SRT1500150015001500#`
- 前进：`SRT1500160015001500#`
- 左移：`SRT1400150015001500#`
- 右转：`SRT1500150015001600#`

## 安全注记
- 首次连接建议先发送 neutral
- 不可假设 C3 有功能
- 不可超出 hard_range
