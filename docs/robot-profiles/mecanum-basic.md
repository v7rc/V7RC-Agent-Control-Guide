# Mecanum Basic Profile

## Metadata
- profile_name: mecanum_basic
- profile_version: 1.0.1
- robot_name: V7RC Mecanum Robot
- robot_type: mecanum_car
- transport: BLE
- firmware_compatibility: >=1.0.0
- supported_protocols: CMD, SRV, SRT, LED

## Control priority
1. CMD
2. SRT
3. SRV
4. SS8

## Motion model
- drive_type: mecanum_semantic_channels
- neutral_value: 1500
- safe_range: 1200-1800
- hard_range: 1000-2000
- motion_notes:
  - This profile uses semantic motion channels instead of direct per-wheel mapping.
  - Channel1 controls left/right movement.
  - Channel2 controls forward/backward movement.
  - Channel4 controls rotation / turning.
  - Channel3 is reserved or unused unless the firmware defines it otherwise.

## Channel mapping
- C1: strafe_left_right
- C2: forward_backward
- C3: reserved
- C4: yaw_turn

## Direction notes
- 1500 means neutral / stop
- For Channel1:
  - values above 1500 = move right
  - values below 1500 = move left
- For Channel2:
  - values above 1500 = move forward
  - values below 1500 = move backward
- For Channel4:
  - values above 1500 = turn right
  - values below 1500 = turn left
- Actual behavior still depends on firmware implementation and should be verified on hardware.

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
- fallback method: SRT
- example fallback command: `SRT1500150015001500#`

### neutral_motion
- method: SRT
- command: `SRT1500150015001500#`

### move_forward_slow
- method: SRT
- command example: `SRT1500160015001500#`
- notes: Channel2 above neutral means forward

### move_backward
- method: SRT
- command example: `SRT1500140015001500#`

### strafe_left
- method: SRT
- command example: `SRT1400150015001500#`
- notes: Channel1 below neutral means left

### strafe_right
- method: SRT
- command example: `SRT1600150015001500#`
- notes: Channel1 above neutral means right

### turn_left
- method: SRT
- command example: `SRT1500150015001400#`
- notes: Channel4 below neutral means rotate left

### turn_right
- method: SRT
- command example: `SRT1500150015001600#`
- notes: Channel4 above neutral means rotate right

### move_forward_left
- method: SRT
- command example: `SRT1400160015001500#`
- notes: combine Channel1 left + Channel2 forward

### move_forward_right
- method: SRT
- command example: `SRT1600160015001500#`
- notes: combine Channel1 right + Channel2 forward

## Safety notes
- first_connect_action: `SRT1500150015001500#`
- emergency_action: `SRT1500150015001500#`
- do not assume Channel3 has a valid function
- do not exceed hard range values
- do not jump directly from full reverse to full forward or from full left turn to full right turn

## Examples

### Stop robot
- intent: stop
- method: SRT
- command: `SRT1500150015001500#`

### Move forward
- intent: move_forward_slow
- method: SRT
- command: `SRT1500160015001500#`

### Strafe left
- intent: strafe_left
- method: SRT
- command: `SRT1400150015001500#`

### Turn right
- intent: turn_right
- method: SRT
- command: `SRT1500150015001600#`

### Show ready status
- intent: ready_led
- method: LED
- command: `LED0F0A0F0A00000000#`
- notes: example only, depends on actual LED grouping rules

### Reset robot
- intent: reset_robot
- method: CMD
- command: `CMDRESET          #`
