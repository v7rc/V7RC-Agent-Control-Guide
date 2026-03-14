# Intent Dictionary

This document defines common semantic intents for V7RC-compatible robots.

## Motion Intents

### `stop`
Meaning:
- stop all drive output as safely as possible

### `neutral_motion`
Meaning:
- set motion-related outputs to neutral values

### `move_forward_slow`
Meaning:
- move forward at low speed

### `move_forward`
Meaning:
- move forward at normal speed

### `move_backward`
Meaning:
- move backward at normal speed

### `turn_left`
Meaning:
- rotate or steer left according to the robot profile

### `turn_right`
Meaning:
- rotate or steer right according to the robot profile

### `strafe_left`
Meaning:
- move laterally left
Only valid for robots that support omnidirectional motion.

### `strafe_right`
Meaning:
- move laterally right
Only valid for robots that support omnidirectional motion.

## Pose / Servo Intents

### `neutral_pose`
Meaning:
- move all documented joints to neutral values

### `pose_home`
Meaning:
- move to the profile-defined home pose

## LED Intents

### `ready_led`
Meaning:
- show ready status

### `waiting_led`
Meaning:
- show waiting or idle status

### `error_led`
Meaning:
- show error status

### `active_led`
Meaning:
- show active / working status

## Device Intents

### `reset_robot`
Meaning:
- reset the device or internal state

### `enable_auto_mode`
Meaning:
- enable autonomous mode

### `disable_auto_mode`
Meaning:
- disable autonomous mode

### `calibrate`
Meaning:
- run calibration if explicitly supported
Risk level: high

## Intent Resolution Rule

1. Use the active robot profile.
2. Prefer the profile's `preferred_control_order`.
3. Check safety rules.
4. Use only explicitly documented commands.
