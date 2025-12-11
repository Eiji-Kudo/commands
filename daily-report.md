# 終業報告生成 (Daily Report Generator)

あなたは以下の情報を収集し、ユーザーの終業報告を作成してください。

## 情報収集

1. **今日のGit Activity**を確認:
   ```bash
   git log --oneline --since="midnight" --author="$(git config user.email)"
   ```

2. **今日マージ/クローズされたPR**を確認:
   ```bash
   gh pr list --state merged --author @me --search "merged:>=$(date +%Y-%m-%d)"
   gh pr list --state closed --author @me
   ```

3. **今日クローズされたIssue**を確認:
   ```bash
   gh issue list --assignee @me --state closed --search "closed:>=$(date +%Y-%m-%d)"
   ```

4. **進行中のPR/Issue**を確認:
   ```bash
   gh pr list --author @me --state open
   gh issue list --assignee @me --state open
   ```

5. **現在の作業ブランチの状態**を確認:
   ```bash
   git status
   git diff --stat
   ```

## 出力フォーマット

収集した情報を基に、以下の形式で報告を作成してください：

---

### 今日の成果とハイライト（Today's Wins & Highlights）

- 朝に掲げたMIT（最優先事項）や目標に対して、何が達成できたかを報告
- マージされたPR、クローズされたissue、完了したタスクを具体的に記載
- 例: 「認証機能のPR #123 をマージ完了」「ユーザー登録バグ #45 を修正」

### 明日への引き継ぎと課題（Hand-offs & Blockers for Tomorrow）

- 今日の業務で残ったタスク
- 明日以降に持ち越す必要のある懸念事項やブロッカー
- 「明日の朝一で〇〇の続きをする」のように、次のアクションを明確に
- 進行中のPRがあればその状態（レビュー待ち、修正中など）

### 今日の学びと振り返り（Today's Learnings & Reflection）（任意）

- その日を通じて得られた技術的な学びや気づき
- 例: 「React 19のuseActionStateの使い方を理解した」

### チームへの共有事項（任意）

- 他のメンバーに共有すべき情報があれば
- 例: 「staging環境のDBマイグレーション完了」「新しいAPIエンドポイント追加」

---

## 注意事項

- 簡潔に、箇条書きで記載する
- 具体的なPR番号やissue番号を含める
- 成果がない場合は正直に「進捗なし」と記載して良い
- 任意の項目は、特に記載がなければ省略可能
