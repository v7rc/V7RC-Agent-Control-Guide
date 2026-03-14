# V7RC Agent Control Guide

This repository provides a structured control guide for AI agents that connect to robots developed with the V7RC ecosystem.

It extends the original V7RC protocol with:
- robot hardware mapping
- motion intent definitions
- safety rules for AI agents
- OpenClaw integration guidance
- machine-readable robot profiles

## Language Versions

| Language | File |
|---|---|
| English | `README.md` |
| 繁體中文 | `README.zh-TW.md` |
| 日本語 | `README.ja.md` |
| ภาษาไทย | `README.th.md` |
| Bahasa Melayu | `README.ms.md` |

## Repository Structure

- `docs/` human-readable documentation by language
- `profiles/` machine-readable robot profiles in YAML
- `schemas/` JSON Schema for validation
- `examples/` prompt and command examples
- `assets/` diagrams and repo structure notes

## Design Goals

1. Keep the raw V7RC protocol separate from robot-specific mapping.
2. Give AI agents a deterministic, safety-first control layer.
3. Support multiple robot types and multiple countries.
4. Make documentation readable for humans and parseable for software.

## Included Profiles

- `mecanum_basic`
- `tank_basic`

## Recommended Reading Order

1. `docs/en/overview.md`
2. `docs/en/protocol-reference.md`
3. `docs/en/safety-rules.md`
4. `docs/en/intent-dictionary.md`
5. `docs/en/integration-openclaw.md`
6. the relevant profile in `docs/en/robot-profiles/`
7. the corresponding YAML file in `profiles/`

## Source Protocol

Official V7RC Protocol:
- https://github.com/v7rc/V7RC-Protocol

## License

MIT
