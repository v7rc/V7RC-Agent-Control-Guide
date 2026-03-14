# Tank Basic Profile

## Metadata
- profile_name: tank_basic
- profile_version: 1.0.0
- robot_name: V7RC Tank Robot
- robot_type: tank_car
- transport: BLE
- firmware_compatibility: >=1.0.0
- supported_protocols: CMD, SRT, SRV, LED

## Control priority
1. CMD
2. SRT
3. SRV
4. SS8

## Motion model
- drive_type: differential_tank_semantic_channels
- neutral_value: 1500
- safe_range: 1200-1800
- hard_range: 1000-2000
- motion_notes:
  - This profile assumes a tank or differential-drive robot.
  - Channel1 controls the left drive side.
  - Channel2 controls the right drive side.
  - Channel3 is reserved or unused unless defined by firmware.
  - Channel4 is reserved or unused unless defined by firmware.

## Channel mapping
- C1: left_drive
- C2: right_drive
- C3: reserved
- C4: reserved

## Direction notes
- 1500 means neutral / stop
- For Channel1:
  - values above 1500 = left side forward
  - values below 1500 = left side backward
- For Channel2:
  - values above 1500 = right side forward
  - values below 1500 = right side backward
- Actual motion direction depends on motor polarity and firmware mapping, and must be verified on real hardware.

## Preferred high-level commands
- CMDSTOP
- CMDFWD1
- CMDBWD1
- CMDTURNL
- CMDTURNR

Note:
These are example logical command names.
Only use the commands that are actually implemented in firmware.

## LED mapping
- LED: front status LEDs
- LE2: rear status LEDs

## Status patterns
- ready_led: solid green
- waiting_led: blinking blue
- error_led: solid red
- active_led: solid white

## Supported intents

### stop
- preferred method: CMD
- fallback method: SRT
- example fallback command: `SRT1500150015001500#`

### neutral_motion
- method: SRT
- command: `SRT1500150015001500#`

### move_forward_slow
- method: SRT
- command example: `SRT1600160015001500#`
- notes: both drive sides forward at low speed

### move_forward
- method: SRT
- command example: `SRT1700170015001500#`

### move_backward
- method: SRT
- command example: `SRT1400140015001500#`

### turn_left
- method: SRT
- command example: `SRT1400160015001500#`
- notes: left side backward, right side forward

### turn_right
- method: SRT
- command example: `SRT1600140015001500#`
- notes: left side forward, right side backward

### arc_left_forward
- method: SRT
- command example: `SRT1550165015001500#`
- notes: left side slower than right side

### arc_right_forward
- method: SRT
- command example: `SRT1650155015001500#`
- notes: right side slower than left side

## Safety notes
- first_connect_action: `SRT1500150015001500#`
- emergency_action: `SRT1500150015001500#`
- do not assume Channel3 or Channel4 has a valid function
- do not exceed hard range values
- do not jump directly from full backward to full forward

## Examples

### Stop robot
- intent: stop
- method: SRT
- command: `SRT1500150015001500#`

### Move forward slowly
- intent: move_forward_slow
- method: SRT
- command: `SRT1600160015001500#`

### Turn left in place
- intent: turn_left
- method: SRT
- command: `SRT1400160015001500#`

### Turn right in place
- intent: turn_right
- method: SRT
- command: `SRT1600140015001500#`

### Show error status
- intent: error_led
- method: LED
- command: `LEDF00AF00AF00AF00A#`

### Reset robot
- intent: reset_robot
- method: CMD
- command: `CMDRESET          #`
