# commands

Claude Code / Cursor用のカスタムコマンド集。PRレビュー、CI、コード分析などのワークフローを自動化する。

## コマンド一覧

### PRレビュー関連

| コマンド | 説明 |
|---------|------|
| `/diff` | 現在開いているファイルのPRでの差分を解説 |
| `/critics-reviewer` | PRの変更内容を批判的にレビューし、懸念点をmdに保存 |
| `/review-comment-analysis` | PRの未解決レビューコメントを分析し、修正要否を判断 |
| `/reply-reviews` | PRの未解決レビューコメントに返信 |
| `/pr-cleanup` | PR内の不要コード調査（不要なoptional、未使用エクスポート） |

### PR作成・管理

| コマンド | 説明 |
|---------|------|
| `/pr-description` | 現在のブランチに対応するPRの内容をMarkdownファイルとして保存 |
| `/pr-issue` | 現在のブランチのPRに対応するissueのドラフトをMarkdownで作成 |

### CI・品質チェック

| コマンド | 説明 |
|---------|------|
| `/ci` | Lint、型チェック、テストを順次実行し、問題があれば修正 |

## 使い方

Claude CodeまたはCursorで `/<コマンド名>` を入力して実行。

`~/.claude/commands/` に配置されたコマンドは両方の環境で利用可能。

```
/ci
/diff
/critics-reviewer 123
```

一部のコマンドはPR番号を引数として受け取る。未指定の場合は現在のブランチに紐づくPRを自動取得する。

## 出力ファイル

一部のコマンドは結果をMarkdownファイルとして保存する:

- `/critics-reviewer` → `documents/critics-review-pr-<PR番号>.md`
- `/review-comment-analysis` → `documents/review-decisions-pr-<PR番号>.md`
- `/pr-description` → `pr-<PR番号>.md`
