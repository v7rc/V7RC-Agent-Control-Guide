# Protocol Reference for Agents

This document summarizes the V7RC command protocol in an agent-friendly form.

## Base Rules

- The first 3 characters are the command code.
- The command must end with `#`.
- Standard packets are built around 20-byte BLE-friendly commands.
- Unused numeric fields should be padded with `0`.
- `CMD` payloads should be padded with spaces if shorter than the maximum.

## Command Families

### `SRV`
Standard PWM control for 4 channels.

Example:
- `SRV1500150015001500#`

### `SR2`
Secondary PWM control for channels C5-C8.

### `SS8`
Simplified 8-channel PWM control using hexadecimal values.

### `SRT`
Semantic motion control or transformed PWM control.
In some robots, firmware interprets C1-C4 as abstract motion channels rather than direct wheel outputs.

### `LED`
First LED group.

### `LE2`
Second LED group.

### `LE?`
Nth LED group supported by firmware.

### `CMD`
Custom firmware-defined command.
Example:
- `CMDRESET          #`

## LED Encoding

Each LED uses `RGBM`:

- `R`: red level from `0` to `F`
- `G`: green level from `0` to `F`
- `B`: blue level from `0` to `F`
- `M`: mode / blink timing

Examples:
- `F00A` = solid red
- `0F0A` = solid green
- `00F5` = blue blinking
- `FFF5` = white blinking

## Important Guidance

A syntactically valid packet may still be unsafe or unsupported for a specific robot.
Always verify:
- profile support
- channel mapping
- safe range
- hard limits
- intent availability
