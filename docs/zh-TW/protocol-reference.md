# 給 Agent 的 Protocol 參考

## 基本規則

- 前 3 個字元是命令代碼
- 命令必須以 `#` 結尾
- 標準封包以 20-byte BLE 友善格式為主
- 未使用的數值欄位以 `0` 補齊
- `CMD` 載荷不足時以空白補齊

## 命令家族

### `SRV`
4 通道 PWM 控制

### `SR2`
C5-C8 的次要 PWM 控制

### `SS8`
8 通道簡化十六進位 PWM 控制

### `SRT`
語意化運動控制或經 firmware 轉換的 PWM 控制

### `LED`
第一組 LED

### `LE2`
第二組 LED

### `LE?`
更多 LED 群組

### `CMD`
自訂韌體命令
例如：
- `CMDRESET          #`

## LED 編碼

每顆 LED 使用 `RGBM`：

- `R`：紅色 0-F
- `G`：綠色 0-F
- `B`：藍色 0-F
- `M`：模式 / 閃爍時間

## 重要提醒

語法正確，不代表對某台機器人就是安全或可用。
一定要檢查：
- profile 是否支援
- channel 映射
- safe range
- hard limits
- 是否有對應 intent
