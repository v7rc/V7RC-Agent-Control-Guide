# V7RC Protocol Reference for Agents

This document summarizes the V7RC command protocol in an agent-friendly form.

## Base rules

The V7RC protocol is designed around BLE packet size constraints.
Commands are limited to 20 bytes in the main format.
Older 16-byte variants are not recommended for modern integrations.

### Common formatting rules
- The first 3 characters represent the command code.
- The command must end with `#`.
- Unused numeric fields should be padded with `0`.
- `CMD` payloads should be padded with spaces if shorter than the maximum payload size.

## Supported command families

### 1. `SRV`
Standard PWM control for 4 channels.

Example:
- `SRV1500150015001500#`

Typical use:
- C1, C2, C3, C4 servo or PWM outputs

### 2. `SR2`
Secondary PWM control for channels C5-C8.

Example:
- `SR21500100018002000#`

Typical use:
- additional servos or outputs when the board supports more than 4 PWM channels

### 3. `SS8`
Simplified 8-channel PWM control using hexadecimal values.
Each 2-digit hex value is converted to decimal, then multiplied by 10.

Example:
- `SS896969696969696#`

### 4. `SRT`
Tank-style transformed PWM control.
CH1 and CH2 are interpreted by firmware as tank motion input.

Example:
- `SRT1500150015001500#`

Typical use:
- differential drive
- tank robot
- joystick-style motion abstraction on firmware side

### 5. `LED`
First LED group, typically 4 LEDs.

### 6. `LE2`
Second LED group, typically another set of 4 LEDs.

### 7. `LE?`
Nth LED group where `?` is the group number.

### 8. `CMD`
Custom device-defined command.
Payload length is up to 16 characters excluding prefix and trailing `#`.
If shorter than the maximum, pad with spaces.

Example:
- `CMDRESET          #`

## LED encoding

Each LED uses 4 characters: `RGBM`

- `R`: red level from `0` to `F`
- `G`: green level from `0` to `F`
- `B`: blue level from `0` to `F`
- `M`: lighting mode / blink timing

Behavior of `M`:
- `0` = off
- `1` = on for 100 ms per second
- ...
- `9` = on for 900 ms per second
- `A` and above = always on

Example:
- `F00A` = solid red
- `FFF5` = white blinking, about 500 ms on / 500 ms off

## Agent usage guidance

Agents should not treat raw protocol support as proof that every robot supports every behavior.
A robot profile must define:
- which command families are supported
- which channels map to which hardware
- safe ranges
- preferred control order
- forbidden or unsupported commands

## Important limitation

A valid V7RC packet can still be semantically invalid for a specific robot.
For example:
- a servo value may be outside safe limits
- a channel may not exist
- a command may be supported by protocol but disabled in firmware

Always check the robot profile before sending commands.