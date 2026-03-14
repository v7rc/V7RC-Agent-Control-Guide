# Safety Rules

## Core Principles

1. If robot state is unknown, prefer STOP or neutral output.
2. Do not invent unsupported commands.
3. Do not exceed hard limits.
4. Prefer high-level safe commands over low-level raw output.
5. Move incrementally when mechanical state is uncertain.

## Required Agent Behavior

### On first connection
The agent should:
- send STOP if supported, or
- send a neutral command, or
- send a profile-defined safe pose

### On ambiguous intent
- prefer no movement
- use a safe fallback
- do not guess a high-risk action

### On servo or PWM control
- never exceed hard limits
- avoid sudden large jumps
- respect profile-defined neutral values

### On motion control
- avoid full-speed movement unless explicitly requested
- start slow when possible
- prefer profile-defined intents to raw synthesis

### On LED control
- use documented LED groups only
- use semantic status patterns when defined

## Safety Levels

### Low risk
- stop
- neutral motion
- ready LED
- waiting LED

### Medium risk
- low-speed movement
- normal turn
- moderate servo movement

### High risk
- full-speed movement
- extreme servo travel
- calibration
- undocumented mode switching

## Prohibited Behaviors

Agents must not:
- send undocumented `CMD` payloads
- exceed hard limits
- assume a wheel layout without a profile
- use undefined channels or LED groups
- combine unrelated control modes blindly
