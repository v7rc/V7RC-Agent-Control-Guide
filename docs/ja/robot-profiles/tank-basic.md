# タンク基本プロファイル


## Metadata
- profile_name: tank_basic
- robot_type: tank_drive
- transport: BLE

## 制御優先順位
1. CMD
2. SRT
3. SRV
4. SS8

## モーションモデル
- Channel1: 左右ステア
- Channel2: 前進 / 後退
- Channel3: 予約
- Channel4: 任意 yaw trim または予約
- neutral_value: 1500
- safe_range: 1200-1800
- hard_range: 1000-2000
