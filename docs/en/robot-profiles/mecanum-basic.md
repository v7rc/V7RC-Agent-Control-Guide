# Mecanum Basic Profile

## Metadata
- profile_name: mecanum_basic
- profile_version: 1.1.0
- robot_name: V7RC Mecanum Robot
- robot_type: mecanum_car
- transport: BLE
- firmware_compatibility: >=1.0.0
- supported_protocols: CMD, SRV, SRT, LED

## Control Priority
1. CMD
2. SRT
3. SRV
4. SS8

## Motion Model
- drive_type: mecanum_semantic_channels
- neutral_value: 1500
- safe_range: 1200-1800
- hard_range: 1000-2000
- motion_notes:
  - This profile uses semantic motion channels instead of direct per-wheel mapping.
  - Channel1 controls left/right movement.
  - Channel2 controls forward/backward movement.
  - Channel4 controls rotation / turning.
  - Channel3 is reserved or unused unless firmware defines it otherwise.

## Channel Mapping
- C1: strafe_left_right
- C2: forward_backward
- C3: reserved
- C4: yaw_turn

## Direction Notes
- 1500 = neutral / stop
- C1 > 1500 = move right
- C1 < 1500 = move left
- C2 > 1500 = move forward
- C2 < 1500 = move backward
- C4 > 1500 = turn right
- C4 < 1500 = turn left

## LED Mapping
- LED: front status LEDs
- LE2: rear status LEDs

## Status Patterns
- ready_led: solid green
- waiting_led: blinking blue
- error_led: solid red
- active_led: solid white

## Supported Intents

### stop
- preferred method: CMD
- fallback method: SRT
- fallback command: `SRT1500150015001500#`

### neutral_motion
- method: SRT
- command: `SRT1500150015001500#`

### move_forward_slow
- method: SRT
- command: `SRT1500160015001500#`

### move_backward
- method: SRT
- command: `SRT1500140015001500#`

### strafe_left
- method: SRT
- command: `SRT1400150015001500#`

### strafe_right
- method: SRT
- command: `SRT1600150015001500#`

### turn_left
- method: SRT
- command: `SRT1500150015001400#`

### turn_right
- method: SRT
- command: `SRT1500150015001600#`

### move_forward_left
- method: SRT
- command: `SRT1400160015001500#`

### move_forward_right
- method: SRT
- command: `SRT1600160015001500#`

## Safety Notes
- first_connect_action: `SRT1500150015001500#`
- emergency_action: `SRT1500150015001500#`
- do not assume Channel3 has a valid function
- do not exceed hard range values
