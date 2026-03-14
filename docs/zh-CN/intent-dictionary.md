# Intent 字典

## Motion Intent

### `stop`
含义：
- 以最安全方式停止移动

### `neutral_motion`
含义：
- 将运动相关输出恢复为 neutral

### `move_forward_slow`
含义：
- 低速前进

### `move_backward`
含义：
- 后退

### `turn_left`
含义：
- 向左转

### `turn_right`
含义：
- 向右转

### `strafe_left`
含义：
- 向左平移
仅适用于支持全向移动的机器人

### `strafe_right`
含义：
- 向右平移
仅适用于支持全向移动的机器人

## LED Intent

### `ready_led`
表示 ready 状态

### `waiting_led`
表示等待 / idle 状态

### `error_led`
表示错误状态

### `active_led`
表示运行中状态

## Device Intent

### `reset_robot`
重置设备或内部状态

### `calibrate`
执行校准
风险：高
