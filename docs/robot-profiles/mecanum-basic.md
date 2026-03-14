# Mecanum Basic Profile

## Metadata
- profile_name: mecanum_basic
- profile_version: 1.0.0
- robot_name: V7RC Mecanum Robot
- robot_type: mecanum_car
- transport: BLE
- firmware_compatibility: >=1.0.0
- supported_protocols: CMD, SRV, SRT, LED

## Control priority
1. CMD
2. SRV
3. SRT
4. SS8

## Motion model
- drive_type: mecanum_4wd
- neutral_value: 1500
- safe_range: 1200-1800
- hard_range: 1000-2000
- motion_notes:
  - This profile assumes direct motor channel control is available.
  - The firmware may optionally implement higher-level drive commands using CMD.
  - Lateral movement is supported only if the wheel direction mapping matches this profile.

## Channel mapping
- C1: front_left_motor
- C2: front_right_motor
- C3: rear_left_motor
- C4: rear_right_motor

## Direction notes
- 1500 means neutral / stop
- values above 1500 indicate forward drive on that channel
- values below 1500 indicate reverse drive on that channel
- exact direction depends on motor wiring and firmware mapping
- verify this profile against the real robot before enabling autonomous motion

## Preferred high-level commands
- CMDSTOP
- CMDFWD1
- CMDBWD1
- CMDLEFT1
- CMDRIGHT1
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
- fallback method: SRV
- example fallback command: `SRV1500150015001500#`

### neutral_motion
- method: SRV
- command: `SRV1500150015001500#`

### move_forward_slow
- method: SRV
- command example: `SRV1600140016001400#`
- notes: verify polarity on real hardware

### move_backward
- method: SRV
- command example: `SRV1400160014001600#`

### turn_left
- method: SRV
- command example: `SRV1400140016001600#`

### turn_right
- method: SRV
- command example: `SRV1600160014001400#`

### strafe_left
- method: SRV
- command example: `SRV1400160016001400#`
- notes: only valid if wheel installation and firmware mapping match mecanum geometry

### strafe_right
- method: SRV
- command example: `SRV1600140014001600#`

## Safety notes
- first_connect_action: `SRV1500150015001500#`
- emergency_action: `SRV1500150015001500#`
- do not use strafe commands unless mapping is verified
- do not assume the wheel polarity without hardware test
- do not jump directly from full reverse to full forward

## Examples

### Stop robot
- intent: stop
- method: SRV
- command: `SRV1500150015001500#`

### Show ready status
- intent: ready_led
- method: LED
- command: `LEDF00A0F0A00000000#`
- notes: example only, depends on actual LED grouping rules

### Show error status
- intent: error_led
- method: LED
- command: `LEDF00AF00AF00AF00A#`

### Reset robot
- intent: reset_robot
- method: CMD
- command: `CMDRESET          #`