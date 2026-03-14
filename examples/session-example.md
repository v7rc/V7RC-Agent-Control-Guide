# Session Example

## Input context
- profile_name: mecanum_basic
- robot_name: V7RC Mecanum Robot
- transport: BLE
- current_mode: manual

## User request
Move the robot slowly to the left.

## Agent reasoning summary
- The active profile is `mecanum_basic`.
- The intended action maps to `strafe_left`.
- Preferred method is `SRT`.
- The documented command is `SRT1400150015001500#`.
- This action is medium risk and within safe range.

## Output
- intent: strafe_left
- selected_method: SRT
- command: SRT1400150015001500#
- safety_check: passed
- notes: using documented mecanum semantic channel mapping
