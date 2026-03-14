# V7RC Agent Control Guide

This repository provides a structured control guide for AI agents that connect to robots developed with the V7RC ecosystem.

It is designed for:
- OpenClaw agents
- LLM-based robot controllers
- custom orchestration systems
- developers who need a safe and reusable robot control specification

## Why this repository exists

The original V7RC protocol defines the low-level command format used to control V7RC-compatible devices.
However, AI agents usually need more than raw protocol syntax.

An agent also needs:
- robot type information
- channel-to-hardware mapping
- preferred control priority
- safe operating ranges
- fallback behavior
- high-level intent to command mapping

This repository adds that missing layer.

## Repository structure

- `docs/overview.md`  
  Overall design concept and usage model.

- `docs/protocol-reference.md`  
  Agent-friendly summary of the V7RC protocol.

- `docs/safety-rules.md`  
  Safety constraints that every agent should follow.

- `docs/intent-dictionary.md`  
  Standard action intents and how they should map to protocol commands.

- `docs/integration-openclaw.md`  
  Suggested method for integrating these documents with OpenClaw.

- `docs/robot-profiles/`  
  Human-readable robot-specific control guides.

- `profiles/`  
  Machine-readable robot profiles in YAML.

- `schemas/`  
  JSON schema definitions for validating profile files.

- `examples/`  
  Ready-to-use prompt and command examples.

## Design goals

1. Keep the original V7RC protocol intact.
2. Add an agent-friendly abstraction layer.
3. Separate raw protocol from robot-specific hardware mapping.
4. Prefer safe, deterministic, inspectable behaviors.
5. Make it easy to support multiple robot types.

## Recommended control hierarchy

Agents should prefer the following control order:

1. High-level custom command (`CMD`) if explicitly supported by the device firmware
2. Robot-specific mapped motion control (`SRT`, `SRV`, `SR2`)
3. Simplified fallback control (`SS8`) if precision is not required
4. Stop / neutral fallback when state is uncertain

## Included robot profiles

Current example profiles:
- mecanum_basic
- tank_basic
- quadruped_basic
- humanoid_basic

## Important note

This repository does not replace the official V7RC protocol reference.
It extends it with:
- safety guidance
- intent modeling
- profile normalization
- AI agent usage conventions

## Source protocol

Official V7RC protocol reference:
- https://github.com/v7rc/V7RC-Protocol/blob/main/protocol.md

## License

See `LICENSE`.
