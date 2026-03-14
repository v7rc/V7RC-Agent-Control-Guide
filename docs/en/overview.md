# Overview

## Purpose

This repository defines how an AI agent should control a V7RC-based robot safely and consistently.

The original V7RC protocol explains low-level messages.
This repository adds:
- semantic control guidance
- hardware mapping
- safety boundaries
- reusable robot profiles
- integration suggestions for OpenClaw and similar systems

## Three Layers

### Layer 1: Raw protocol
Examples:
- `SRT1500150015001500#`
- `SRV1500150015001500#`
- `CMDSTOP           #`
- `LEDF00AF00AF00AF00A#`

### Layer 2: Hardware mapping
Examples:
- C1 = left/right motion
- C2 = forward/backward motion
- C4 = turning
- LED = front status LEDs

### Layer 3: Agent intent
Examples:
- `stop`
- `move_forward_slow`
- `turn_left`
- `ready_led`
- `neutral_pose`

## Design Principles

1. Safety first
2. Prefer explicit mappings over assumptions
3. Keep profiles machine-readable
4. Allow robot-specific differences
5. Never let the AI invent unsupported commands

## Recommended Agent Workflow

1. Identify the active robot profile.
2. Read supported protocols.
3. Read safety rules.
4. Resolve the user request into a defined intent.
5. Choose the preferred control method.
6. Generate a command string.
7. Validate the command against the profile.
8. Send the command or refuse safely.

## Scope

Current scope:
- BLE-based V7RC robots
- motion control
- servo / PWM control
- LED status control
- custom `CMD` actions

Planned future scope:
- telemetry
- acknowledgements
- capability discovery
- sensor feedback
