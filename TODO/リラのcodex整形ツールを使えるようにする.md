- もっと簡単な実装は「history.jsonlを直接読む」だけど、これで十分実用的。
  - これを調べる。

```
✅ ツール完成！

───

🛠️ 作成したツール

場所: ~/.local/bin/codex-session-export

───

📋 機能

1. セッション一覧表示

codex-session-export -l

2. 最新セッション抽出

codex-session-export

3. N個前のセッション抽出

codex-session-export -2  # 最新から2つ前

4. セッションID指定

codex-session-export 019caadc...

───

📁 出力先

~/Desktop/user-daily/LLMlog/
├── 20260302_061601_session-019caadc.md  (22行)
└── 20260302_061610_session-019ca875.md  (31行)

───

✅ テスト結果

✅ セッション一覧: 成功（20件表示）
✅ 最新セッション: 成功（22行抽出）
✅ -2オプション: 成功（31行抽出）
✅ Markdown出力: 成功

───

可能。もっと簡単な実装は「history.jsonlを直接読む」だけど、これで十分実用的。
```
