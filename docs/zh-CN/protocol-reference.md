# 面向 Agent 的 Protocol 参考

## 基本规则

- 前 3 个字符是命令代码
- 命令必须以 `#` 结尾
- 标准封包以 20-byte BLE 友好格式为主
- 未使用的数值字段以 `0` 补齐
- `CMD` 载荷不足时以空格补齐

## 命令家族

### `SRV`
4 通道 PWM 控制

### `SR2`
C5-C8 的次级 PWM 控制

### `SS8`
8 通道简化十六进制 PWM 控制

### `SRT`
语义化运动控制或经 firmware 转换的 PWM 控制

### `LED`
第一组 LED

### `LE2`
第二组 LED

### `LE?`
更多 LED 组

### `CMD`
自定义固件命令
例如：
- `CMDRESET          #`

## LED 编码

每颗 LED 使用 `RGBM`：

- `R`：红色 0-F
- `G`：绿色 0-F
- `B`：蓝色 0-F
- `M`：模式 / 闪烁时间

## 重要提醒

语法正确，不代表对某台机器人就是安全或可用。
一定要检查：
- profile 是否支持
- channel 映射
- safe range
- hard limits
- 是否有对应 intent
