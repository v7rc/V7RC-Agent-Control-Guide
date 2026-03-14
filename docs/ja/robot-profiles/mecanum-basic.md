# メカナム基本プロファイル


## Metadata
- profile_name: mecanum_basic
- robot_type: mecanum_car
- transport: BLE

## 制御優先順位
1. CMD
2. SRT
3. SRV
4. SS8

## モーションモデル
- Channel1: 左右移動
- Channel2: 前進 / 後退
- Channel3: 予約
- Channel4: 旋回
- neutral_value: 1500
- safe_range: 1200-1800
- hard_range: 1000-2000

## 方向ルール
- C1 > 1500: 右
- C1 < 1500: 左
- C2 > 1500: 前進
- C2 < 1500: 後退
- C4 > 1500: 右旋回
- C4 < 1500: 左旋回
