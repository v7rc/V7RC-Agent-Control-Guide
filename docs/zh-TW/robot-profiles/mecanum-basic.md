# 麥克納姆基本 Profile


## Metadata
- profile_name: mecanum_basic
- robot_type: mecanum_car
- transport: BLE

## 控制優先順序
1. CMD
2. SRT
3. SRV
4. SS8

## 運動模型
- Channel1：左右平移
- Channel2：前進 / 後退
- Channel3：保留
- Channel4：轉向 / 旋轉
- neutral_value：1500
- safe_range：1200-1800
- hard_range：1000-2000

## 方向規則
- C1 > 1500：向右
- C1 < 1500：向左
- C2 > 1500：前進
- C2 < 1500：後退
- C4 > 1500：右轉
- C4 < 1500：左轉

## 常用命令
- neutral：`SRT1500150015001500#`
- 前進：`SRT1500160015001500#`
- 左移：`SRT1400150015001500#`
- 右轉：`SRT1500150015001600#`

## 安全註記
- 首次連線建議先送 neutral
- 不可假設 C3 有功能
- 不可超出 hard_range
