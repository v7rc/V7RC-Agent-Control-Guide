# Safety Rules

This document defines the minimum safety requirements for AI agents controlling V7RC-based robots.

## Core principles

1. If robot state is unknown, prefer STOP or neutral output.
2. Do not invent unsupported commands.
3. Do not exceed hard limits.
4. Prefer high-level safe commands over low-level direct output.
5. Move incrementally when mechanical state is uncertain.

## Required agent behavior

### 1. On first connection
The agent should do one of the following before any aggressive movement:
- send a STOP command if supported
- send a neutral motion command
- set servos to neutral pose if the robot profile provides one

### 2. On ambiguous intent
If the requested action is unclear:
- prefer no movement
- use a safe fallback
- do not guess a high-risk action

### 3. On unsupported command
If a command is not defined in the robot profile:
- do not send it
- fall back to a documented alternative if available

### 4. On servo control
- never exceed the profile hard limits
- avoid sudden large jumps
- if step size is defined, respect it
- if no step size is defined, keep transitions conservative

### 5. On motion control
- avoid full-speed movement unless explicitly requested
- when possible, start with low or medium speed
- prefer profile-defined motion intents to direct PWM synthesis

### 6. On LED control
- use documented LED groups only
- use semantic status patterns when defined
- do not assume that all robots expose the same LED count

## Safety levels

### Low risk
- set ready LED
- set waiting LED
- read profile
- send neutral pose

### Medium risk
- low-speed movement
- normal turning
- moderate servo movement

### High risk
- full-speed motion
- extreme servo travel
- calibration without confirmation
- custom firmware commands that change operating mode

## Recommended fail-safe actions

The robot profile should define at least one of:
- `stop_command`
- `neutral_command`
- `safe_pose_command`

Agents should prefer them in emergency order:
1. stop_command
2. neutral_command
3. safe_pose_command

## Prohibited behaviors

Agents must not:
- send undocumented `CMD` payloads
- exceed hard PWM limits
- assume a wheel layout without profile confirmation
- combine unrelated control modes blindly
- issue repeated aggressive commands without stabilization logic