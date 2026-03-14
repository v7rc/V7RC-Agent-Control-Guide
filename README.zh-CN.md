# V7RC 机器人 AI Agent 控制指南

这个 Repository 提供一套可供 AI Agent 使用的 V7RC 机器人控制文档。

它在原始 V7RC Protocol 之上补充了：
- 机器人硬件映射
- 动作语义定义
- AI Agent 安全规则
- OpenClaw 集成指引
- 可机器读取的 YAML robot profile

## 语言版本

| 语言 | 文件 |
|---|---|
| English | `README.md` |
| 繁體中文 | `README.zh-TW.md` |
| 简体中文 | `README.zh-CN.md` |
| 日本語 | `README.ja.md` |
| ภาษาไทย | `README.th.md` |
| Bahasa Melayu | `README.ms.md` |

## 目录结构

- `docs/` 按语言分类、供人阅读的文档
- `profiles/` 供 AI Agent / 程序使用的 YAML 配置
- `schemas/` 用于校验的 JSON Schema
- `examples/` prompt 与命令示例
- `assets/` 架构图与辅助资源

## 内含 Profile

- `mecanum_basic`
- `tank_basic`

## 建议阅读顺序

1. `docs/zh-CN/overview.md`
2. `docs/zh-CN/protocol-reference.md`
3. `docs/zh-CN/safety-rules.md`
4. `docs/zh-CN/intent-dictionary.md`
5. `docs/zh-CN/integration-openclaw.md`
6. `docs/zh-CN/robot-profiles/` 中的机型文档
7. `profiles/` 中对应的 YAML 文件

## 原始协议

官方 V7RC Protocol：
- https://github.com/v7rc/V7RC-Protocol

## 授权

MIT
