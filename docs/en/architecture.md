# V7RC AI Robot Control Architecture

This document explains the recommended architecture for connecting AI agents, OpenClaw, and V7RC-based robots.

## Main Components

- User Interface
- OpenClaw / LLM Agent
- V7RC Agent Control Guide Repository
- Runtime Orchestrator / App Server
- BLE / Transport Layer
- V7RC Robot Firmware
- Robot Hardware
- Optional telemetry and sensor feedback

## Control Flow

1. The user sends an instruction.
2. OpenClaw interprets the request.
3. The agent reads the active robot profile and safety rules.
4. The agent resolves an intent into a command.
5. The runtime sends the command over BLE or another transport.
6. Robot firmware interprets the command.
7. Motors, servos, LEDs, and sensors react.
8. Optional telemetry returns to the runtime and agent.

## Why this structure works

- Documentation stays separate from firmware.
- Profiles can evolve without rewriting prompts.
- Different countries can localize docs without changing YAML.
- Safety logic remains visible and auditable.
