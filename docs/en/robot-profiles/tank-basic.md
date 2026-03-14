# Tank Basic Profile

## Metadata
- profile_name: tank_basic
- profile_version: 1.0.0
- robot_name: V7RC Tank Robot
- robot_type: tank_drive
- transport: BLE
- firmware_compatibility: >=1.0.0
- supported_protocols: CMD, SRV, SRT, LED

## Control Priority
1. CMD
2. SRT
3. SRV
4. SS8

## Motion Model
- drive_type: differential_semantic_channels
- neutral_value: 1500
- safe_range: 1200-1800
- hard_range: 1000-2000
- motion_notes:
  - This profile uses semantic motion channels instead of direct per-track PWM mapping.
  - Channel1 controls steering left/right.
  - Channel2 controls forward/backward motion.
  - Channel4 may be used as rotation trim or reserved, depending on firmware.
  - Channel3 is reserved unless defined by firmware.

## Channel Mapping
- C1: steer_left_right
- C2: forward_backward
- C3: reserved
- C4: optional_yaw_or_reserved

## Direction Notes
- 1500 = neutral / stop
- C1 > 1500 = steer right
- C1 < 1500 = steer left
- C2 > 1500 = move forward
- C2 < 1500 = move backward
- C4 should only be used if firmware explicitly documents it

## LED Mapping
- LED: front status LEDs
- LE2: rear status LEDs

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

### turn_left
- method: SRT
- command: `SRT1400150015001500#`

### turn_right
- method: SRT
- command: `SRT1600150015001500#`

### forward_left
- method: SRT
- command: `SRT1400160015001500#`

### forward_right
- method: SRT
- command: `SRT1600160015001500#`

## Safety Notes
- first_connect_action: `SRT1500150015001500#`
- emergency_action: `SRT1500150015001500#`
- do not use Channel4 unless firmware documents its meaning
- do not exceed hard range values
