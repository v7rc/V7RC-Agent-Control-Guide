# OpenClaw 連携ガイド

AI Agent に渡すもの：
1. system prompt
2. active robot profile
3. safety rules
4. intent dictionary
5. 必要なら runtime state

推奨手順：
1. profile を特定
2. 対応 protocol を確認
3. control priority を確認
4. intent を解決
5. コマンド生成
6. 検証
7. 安全に送信または拒否
