# 天神橋筋ホステルプロジェクト ダッシュボード

プロジェクト管理用のダッシュボードWebアプリです。GitHub Pagesでホスティングされています。

**公開URL**: https://yukiominato.github.io/tenjinbashi-hostel-hub/

---

## コンテンツの更新方法

### 議事録を追加する

1. `content/minutes/` に Markdown ファイルを作成（例：`2026-07-01-mtg.md`）
2. `content/index.json` の `minutes` 配列に1行追加

```json
{ "file": "minutes/2026-07-01-mtg.md", "title": "MTGタイトル", "date": "2026-07-01" }
```

3. git commit & push → 即反映

```bash
git add content/minutes/2026-07-01-mtg.md content/index.json
git commit -m "add: 2026-07-01 MTG議事録"
git push
```

---

### 決定事項を追記する

`content/decisions.md` を開いて、**先頭に** 新しいエントリを追加します（最新が上になるよう運用）。

```markdown
## 2026-07-01
- **決定内容**：ここに決定事項を書く
```

```bash
git add content/decisions.md
git commit -m "update: 決定事項 2026-07-01"
git push
```

---

### 別プロジェクトで使い回す

1. このリポジトリをフォークまたは複製する
2. `config.json` を書き換える（`projectName` / `tagline` / `phases` / `links`）
3. `content/` 以下のファイルをプロジェクト内容に合わせて差し替える
4. GitHub Pages を有効化する（Settings → Pages → Deploy from branch: main / root）

`index.html` は一切触らなくてよい設計です。

---

## Claude Code への依頼例文

コピーして貼り付けるだけで使えます。

```
content/minutes/ に今日の議事録（YYYY-MM-DD-タイトル.md）を追加して、
content/index.json も更新して git push して。
内容：[ここに議事録の内容を箇条書きで書く]
```

```
content/decisions.md の先頭に今日の決定事項を追記して git push して。
決定内容：[ここに書く]
```

```
config.json の phases を更新して Phase 1 を done、Phase 2 を active にして git push して。
```

---

## ローカルで確認する

`file://` では fetch が動かないため、必ずローカルサーバー経由で確認してください。

```bash
cd /path/to/tenjinbashi-hostel-hub
python3 -m http.server 8000
# → http://localhost:8000 をブラウザで開く
```
