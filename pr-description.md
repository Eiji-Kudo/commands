PR番号を指定してPRの内容を取得し、Markdownファイルとして保存してください。

## 手順

1. **PR情報の取得**
   - `gh pr list` でPR一覧を確認
   - 指定されたPR番号のPR情報を `gh pr view {num} --json title,body,number,headRefName,baseRefName,author,createdAt,url` で取得
   - または `gh pr view {num}` でPRの詳細を確認

2. **PRテンプレートの確認**
   - `.github/pull_request_template.md` が存在する場合は内容を確認
   - テンプレートの構造に従ってPR内容を整理

3. **PR内容の作成**
   - 取得したPR情報を基に、テンプレートに従ってMarkdown形式で内容を作成
   - フォーマルな文体で記述（敬語は使用しない）
   - 詳細すぎず、要点を簡潔にまとめる

4. **ファイル保存**
   - 作成した内容をMarkdownファイルとして保存
   - ファイル名は `pr-{num}.md` など適切な名前を付ける

## 注意事項

- Git CLIを使用してPR情報を取得する
- テンプレートが存在する場合は必ず参照する
- 文体はフォーマルで、敬語は使わない
- 内容は簡潔に、細かすぎない程度にまとめる
- 基本情報（PR番号、作成者、作成日、URL等）は含めない
