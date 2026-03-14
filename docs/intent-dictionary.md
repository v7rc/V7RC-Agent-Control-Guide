# Intent Dictionary

This document defines standard semantic intents for V7RC-compatible robots.

Each robot profile may implement only a subset of these intents.

## Motion intents

### `stop`
Meaning:
- stop all drive output as safely and quickly as possible

Preferred behavior:
- use `CMD STOP` if firmware supports it
- otherwise use neutral motion command

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
- rotate or steer left according to the robot drive model

### `turn_right`
Meaning:
- rotate or steer right according to the robot drive model

### `strafe_left`
Meaning:
- lateral left movement
Only valid for robots that support omnidirectional motion such as mecanum.

### `strafe_right`
Meaning:
- lateral right movement
Only valid for robots that support omnidirectional motion such as mecanum.

### `neutral_motion`
Meaning:
- set motion-related outputs to neutral values

## Servo / pose intents

### `neutral_pose`
Meaning:
- set all defined joints or servos to their profile neutral positions

### `pose_home`
Meaning:
- move robot to profile-defined home pose

### `pose_stand`
Meaning:
- set profile-defined standing pose

### `pose_sit`
Meaning:
- set profile-defined sitting pose

## LED intents

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
- show activity or working status

## Device intents

### `reset_robot`
Meaning:
- reset the device or internal control state

### `enable_auto_mode`
Meaning:
- enable autonomous mode

### `disable_auto_mode`
Meaning:
- disable autonomous mode

### `calibrate`
Meaning:
- run profile-defined calibration command
Risk level: high

## Intent resolution rule

When mapping an intent to a command:
1. use the robot profile
2. prefer the profile's `preferred_control_order`
3. check safety rules
4. ensure the target command is explicitly documented

## Example structure

Each profile should define intent resolution like this:

- intent: `stop`
  method: `CMD`
  command: `CMDSTOP           #`
  risk: low

- intent: `neutral_motion`
  method: `SRV`
  command: `SRV1500150015001500#`
  risk: low
