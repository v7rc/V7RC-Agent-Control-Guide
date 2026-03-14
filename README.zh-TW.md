# V7RC 機器人 AI Agent 控制指南

這個 Repository 提供一套可供 AI Agent 使用的 V7RC 機器人控制文件。

它在原始 V7RC Protocol 之上補上：
- 機器人硬體映射
- 動作語意定義
- AI Agent 安全規則
- OpenClaw 整合指引
- 可機器讀取的 YAML robot profile

## 語言版本

| 語言 | 檔案 |
|---|---|
| English | `README.md` |
| 繁體中文 | `README.zh-TW.md` |
| 簡體中文 | `README.zh-CN.md` |
| 日本語 | `README.ja.md` |
| ภาษาไทย | `README.th.md` |
| Bahasa Melayu | `README.ms.md` |

## 目錄結構

- `docs/` 依語言分類的人類閱讀文件
- `profiles/` 給 AI Agent / 程式使用的 YAML 設定
- `schemas/` 驗證用 JSON Schema
- `examples/` prompt 與命令範例
- `assets/` 架構圖與輔助資產

## 內含 Profile

- `mecanum_basic`
- `tank_basic`

## 建議閱讀順序

1. `docs/zh-TW/overview.md`
2. `docs/zh-TW/protocol-reference.md`
3. `docs/zh-TW/safety-rules.md`
4. `docs/zh-TW/intent-dictionary.md`
5. `docs/zh-TW/integration-openclaw.md`
6. `docs/zh-TW/robot-profiles/` 中的機型文件
7. `profiles/` 中對應的 YAML 檔案

## 原始協定

官方 V7RC Protocol：
- https://github.com/v7rc/V7RC-Protocol

## 授權

MIT
