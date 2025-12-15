# 終業報告生成 (Daily Report Generator)

ユーザーの終業報告を収集・作成し、Slackにコピペできる形式で出力する。

## 情報収集

1. 今日のGit Activity（自分のコミットのみ）:
   ```bash
   git log --oneline --since="midnight" --author="Eiji-Kudo"
   ```

2. 今日マージされたPR:
   ```bash
   gh pr list --state merged --author Eiji-Kudo --search "merged:>=$(date +%Y-%m-%d)"
   ```

3. 今日クローズされたIssue:
   ```bash
   gh issue list --assignee Eiji-Kudo --state closed --search "closed:>=$(date +%Y-%m-%d)"
   ```

4. 進行中のPR/Issue:
   ```bash
   gh pr list --author Eiji-Kudo --state open
   gh issue list --assignee Eiji-Kudo --state open
   ```

## 出力フォーマット

Slackにそのままコピペできる形式で出力する。マークダウン記法（**など）は使用しない。

---

終業報告 - YYYY/MM/DD

【今日の成果とハイライト】

• 完了した作業内容（ビジネス視点で説明）
  - 詳細があれば箇条書きで補足
• クローズした課題
  - #番号 課題タイトル（平易な言葉で）

【明日への引き継ぎと課題】

レビュー待ちのPR:
• #番号 内容（機能の目的を簡潔に）

今後対応予定の課題:
• #番号 課題タイトル（平易な言葉で）

【今日の学びと振り返り】（任意）

• 学びや気づきがあれば記載

【チームへの共有事項】（任意）

• 共有すべき情報があれば記載

---

## 注意事項

- 技術用語を避け、ビジネスの人にもわかりやすい表現を使う
- 機能の目的や利用者への影響を中心に記載する
- 箇条書きは「•」を使用（Slack対応）
- 見出しは【】で囲む
- 具体的なPR番号やissue番号を含める
- 成果がない場合は正直に「進捗なし」と記載して良い
- 任意の項目は、特に記載がなければ省略可能

## 最後に

作成した報告を `documents/daily-report-YYYY-MM-DD.md` に保存する。
