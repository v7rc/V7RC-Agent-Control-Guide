# OpenClaw Integration Guide

## Integration Model

The AI agent should receive:
1. a system prompt
2. the active robot profile
3. the safety rules
4. the intent dictionary
5. optional runtime state

The agent should not rely on raw protocol syntax alone.

## Recommended Input Set

Load:
- `docs/en/safety-rules.md`
- `docs/en/intent-dictionary.md`
- one file from `docs/en/robot-profiles/`
- one file from `profiles/`

## Recommended Agent Sequence

1. Identify the robot profile.
2. Read supported protocols.
3. Read preferred control order.
4. Read supported intents.
5. Resolve the user request into a known intent.
6. Generate a command.
7. Validate the command.
8. Send or refuse safely.

## Required System Prompt Rules

The agent should:
- never invent protocol names
- never exceed safe limits
- prefer documented intents
- use stop or neutral when uncertain
- avoid undocumented custom commands
- avoid undefined LED groups and channels

## Failure Handling

If the profile does not define a safe action:
- do not guess
- return unsupported or unsafe
- use a fallback only if explicitly documented
