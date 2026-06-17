# Step 2: ゲームをGitで管理する

## このステップで学ぶこと

* 既存プロジェクトをGit管理下に置く
* 最初のコミットを作成する
* 変更履歴を保存する
* VS Codeからコミットを行う

---

# ゲームプロジェクトの構成

この演習ではブラウザゲーム **Stack Overflown** を使用します。

まずはファイル構成を確認してみましょう。

```text
src/
├── index.html
├── index.js
├── patterns.js
└── style.css
```

各ファイルの役割は次の通りです。

| ファイル        | 内容         |
| ----------- | ---------- |
| index.html  | ゲーム画面の構造   |
| index.js    | ゲーム本体のロジック |
| patterns.js | 問題パターンの定義  |
| style.css   | 見た目のデザイン   |

---

# 現在のゲームを確認する

VS Codeで `src/index.html` を開きます。

右クリックして **Show Preview** を選択してください。

ゲームが正常に動作することを確認します。

> この時点ではまだGitによる履歴管理は行われていません。

---

# 最初のコミットを作成する

現在のゲームの状態を履歴として保存します。

リポジトリの状態を確認します。

```bash
git status
```

すべてのファイルをステージングします。

```bash
git add src/*
```

状態を確認します。

```bash
git status
```

追加されたファイルが表示されます。

---

# 初回コミット

現在のゲームを履歴として保存します。

```bash
git commit -m "Initial commit"
```

これでゲームの最初の状態が保存されました。

今後どのような変更を行っても、この状態へ戻ることができます。

---

# READMEを追加する

次にプロジェクトの説明を追加します。

プロジェクトルートに

```text
README.md
```

を作成してください。

以下を記述します。

```markdown
# Stack Overflown

Organize the falling blocks into the current debug pattern before the stack overflows! ⏳
```

---

# VS Codeからコミットしてみる

README を保存すると Source Control に変更が表示されます。

1. Source Control を開く
2. README.md の `+` を押す
3. コミットメッセージを入力

```text
Start game documentation
```

4. Commit を押す

---

# ドキュメントを更新する

README.md に以下を追記します。

```markdown
## How to Develop

- index.html - the game container for playing
- index.js - the primary game logic
- patterns.js - the error patterns to match during gameplay
- style.css - the game formatting and styling
```

再度コミットを作成します。

```text
Start developer docs
```

---

# コミット履歴を確認する

ターミナルで以下を実行します。

```bash
git log --oneline
```

実行例:

```text
c4e32a1 Start developer docs
f81f6d0 Start game documentation
1d9ab45 Initial commit
```

ゲーム開発の履歴が少しずつ積み上がっていることが確認できます。

---

# まとめ

このステップでは、

* ゲームプロジェクトをGit管理下に置いた
* 最初のコミットを作成した
* READMEを追加した
* VS Codeからコミットを行った

次のステップでは、ゲームに新機能を追加しながらブランチを利用した開発を体験します。

[← Step 1](step1-introduction.md) | [Step 3 →](step3-exploring-history.md)