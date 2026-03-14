# OpenClaw Integration Guide

This document suggests how to use this repository with OpenClaw or other LLM-driven agent systems.

## Integration model

The AI agent should receive:
1. a system prompt
2. the relevant robot profile
3. the safety rules
4. the intent dictionary
5. optional recent robot state

The agent should not rely only on raw protocol syntax.

## Recommended input set

For each connected robot, load:
- `docs/safety-rules.md`
- `docs/intent-dictionary.md`
- one file from `docs/robot-profiles/`
- one file from `profiles/`

## Recommended OpenClaw behavior

The agent should follow this sequence:

1. Identify robot profile name
2. Read supported protocols
3. Read preferred control order
4. Read valid intents
5. Resolve user request into one defined intent
6. Generate command
7. Validate command against safety constraints
8. Send command

## Recommended system prompt rules

The agent should be instructed:

- never invent protocol names
- never exceed safe limits
- prefer documented intents
- if uncertain, use stop or neutral
- do not assume channel meaning without a profile
- do not use unsupported LED groups
- do not use undocumented custom commands

## Suggested runtime context

At minimum, supply the following runtime fields:
- robot_name
- robot_type
- profile_name
- firmware_version
- transport
- supported_protocols
- current_mode
- battery_state (optional)
- last_command (optional)

## Best practice

Use YAML profile files for parsing and markdown files for explanation.
This keeps the agent both interpretable and structured.

## Failure handling

If the profile is missing a required action:
- do not guess
- respond with unsupported action
- fall back to a safe alternative if one exists

## Versioning recommendation

Use semantic versioning for each profile:
- profile_version: 1.0.0
- firmware_compatibility: ">=1.0.0"

This helps prevent mismatched robot-control assumptions.
