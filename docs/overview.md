# Overview

## Purpose

This repository defines how an AI agent should control a V7RC-based robot safely and consistently.

The original V7RC protocol is a low-level message protocol.
This repository adds:
- semantic control guidance
- hardware mapping
- safety boundaries
- reusable robot profiles
- integration suggestions for LLM-driven systems

## The three layers

### Layer 1: Raw protocol
Examples:
- `SRV1500150015001500#`
- `SRT1500150015001500#`
- `CMDRESET          #`
- `LEDF00AF00AF00AF00A#`

This layer defines the actual messages sent to the robot.

### Layer 2: Hardware mapping
Examples:
- C1 = front_left_motor
- C2 = front_right_motor
- C3 = rear_left_motor
- C4 = rear_right_motor
- LED group 1 = front LEDs

This layer defines what the robot channels really mean.

### Layer 3: Agent intent
Examples:
- move_forward_slow
- stop
- turn_left
- ready_led
- neutral_pose
- reset_robot

This layer allows the AI agent to reason in semantic actions instead of only raw packets.

## Design principles

1. Safety first
2. Prefer explicit mappings over assumptions
3. Keep profiles machine-readable
4. Allow robot-specific differences
5. Avoid letting the AI invent unsupported commands

## Recommended workflow for AI agents

1. Identify the current robot profile
2. Read supported protocols
3. Read safety rules
4. Resolve user intent into a known action
5. Choose the preferred control method
6. Generate the final command string
7. Send command
8. Observe result and fall back safely if uncertain

## Scope

This repository currently focuses on:
- BLE-based V7RC robots
- motion control
- servo control
- LED control
- custom command control

Future versions may also include:
- telemetry conventions
- acknowledgment protocol
- capability negotiation
- battery / IMU / sensor exposure