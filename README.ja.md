# V7RC ロボット AI Agent 制御ガイド

このリポジトリは、V7RC エコシステムで開発されたロボットを AI Agent が安全かつ一貫して制御するためのガイドを提供します。

以下を追加します。
- ロボットのハードウェアマッピング
- モーションインテント定義
- AI Agent の安全ルール
- OpenClaw 統合ガイド
- YAML 形式のロボットプロファイル

## 言語版

| 言語 | ファイル |
|---|---|
| English | `README.md` |
| 繁體中文 | `README.zh-TW.md` |
| 日本語 | `README.ja.md` |
| ภาษาไทย | `README.th.md` |
| Bahasa Melayu | `README.ms.md` |

## 構成

- `docs/` 言語別ドキュメント
- `profiles/` AI / ソフトウェア向け YAML プロファイル
- `schemas/` 検証用 JSON Schema
- `examples/` プロンプトとコマンド例
- `assets/` 図と補助ファイル

## 含まれるプロファイル

- `mecanum_basic`
- `tank_basic`

## 元のプロトコル

公式 V7RC Protocol：
- https://github.com/v7rc/V7RC-Protocol

## ライセンス

MIT
