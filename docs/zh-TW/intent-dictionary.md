# Intent 字典

## Motion Intent

### `stop`
意義：
- 以最安全方式停止移動

### `neutral_motion`
意義：
- 將運動相關輸出設回 neutral

### `move_forward_slow`
意義：
- 低速前進

### `move_backward`
意義：
- 後退

### `turn_left`
意義：
- 向左轉

### `turn_right`
意義：
- 向右轉

### `strafe_left`
意義：
- 向左平移
只適用於支援全向移動的機器人

### `strafe_right`
意義：
- 向右平移
只適用於支援全向移動的機器人

## LED Intent

### `ready_led`
表示 ready 狀態

### `waiting_led`
表示等待 / idle 狀態

### `error_led`
表示錯誤狀態

### `active_led`
表示運作中狀態

## Device Intent

### `reset_robot`
重設裝置或內部狀態

### `calibrate`
執行校正
風險：高
