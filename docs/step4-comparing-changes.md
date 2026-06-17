# Step 4: 変更内容を確認する

## このステップで学ぶこと

* Gitで変更内容を確認する方法
* ステージングエリアと作業ディレクトリの違い
* VS Codeで差分（Diff）を確認する方法
* ゲームのUIやゲーム内容を変更する方法

---

# コードレビューはなぜ重要なのか？

コミットを作成する前に、

> 「本当に意図した変更だけが含まれているか？」

を確認することは非常に重要です。

Gitでは変更箇所を比較（Diff）することで、

* 追加したコード
* 削除したコード
* 修正したコード

を簡単に確認できます。

---

# 差分の見方

Gitでは通常、

```diff
+ 追加された行
- 削除された行
```

として表示されます。

例えば

```diff
- <h3>Score</h3>
+ <h3>Current Score</h3>
```

であれば、

「Score」が「Current Score」に変更されたことを意味します。

---

# 演習1: スコア表示を改善する

今回はゲーム画面にハイスコア表示を追加します。

まず `src/index.html` を開いてください。

---

## スコア表示部分を探す

20行目付近に次のようなコードがあります。

```html
<div class="info-section">
   <h3>Score</h3>
   <div class="score" id="score">0</div>
</div>

<div class="info-section">
   <h3>Status</h3>
   <div class="status" id="status">Ready</div>
</div>
```

---

## スコア表示を変更する

上記を以下の内容に置き換えてください。

```html
<div class="info-section">
   <h3>Current Score</h3>
   <div class="score" id="score">0</div>
   <h3>High Score</h3>
   <div class="high-score" id="high-score">0</div>
</div>
```

変更内容:

* `Score` → `Current Score`
* `High Score` を追加
* `Status` 表示を削除

---

## ブラウザで確認する

ゲームをリロードしてください。

右側の情報欄が変更されていることを確認しましょう。

---

## 変更内容を確認する

コミットする前に差分を確認します。

```bash
git diff src/index.html
```

追加・削除された行が表示されることを確認してください。

---

## ステージングする

```bash
git add src/index.html
```

---

## ステージング後の状態を確認する

```bash
git diff src/index.html
```

何も表示されないことを確認してください。

これは

```text
作業ディレクトリ
=
ステージングエリア
```

になったためです。

---

## コミット前の内容を確認する

```bash
git diff --staged src/index.html
```

ステージングされた変更内容が表示されます。

---

## コミットする

```bash
git commit -m "Add element for showing high score"
```

---

# 演習2: Null Pointerパターンを変更する

次はゲーム内で出題されるパターンを変更します。

`src/patterns.js` を開いてください。

---

## Null Pointerパターンを探す

3行目付近に次のようなコードがあります。

```javascript
{
  name: "Null Pointer",
  pattern: [
    ...
  ],
},
```

この `pattern` の内容を書き換えます。

---

## パターンを書き換える

`Null Pointer` の定義全体を以下に置き換えてください。

```javascript
{
  name: "Null Pointer",
  pattern: [
    [0, 1, 1, 1, 0],
    [0, 1, 0, 1, 0],
    [0, 1, 1, 1, 0],
    [0, 0, 1, 0, 0],
    [0, 0, 1, 0, 0],
  ],
},
```

---

## 変更内容をゲームで確認する

ゲームをリロードし、

出題される Null Pointer パターンの形が変わっていることを確認してください。

コードだけでなく、実際のゲーム画面も確認するようにしましょう。

---

## VS Codeで差分を確認する

Source Control を開くと、

```text
patterns.js
```

が Changes に表示されます。

ファイルをダブルクリックすると Diff ビューが開きます。

確認するポイント:

* どの行が削除されたか
* どの行が追加されたか
* パターンの形がどう変わったか

---

## ステージングする

`+` ボタンを押してステージングします。

⚠️ まだコミットはしないでください。

---

## Staged Changes を確認する

Staged Changes に移動した

```text
patterns.js
```

をダブルクリックしてください。

この画面は

> これからコミットされる内容

を確認するためのビューです。

---

## コミットする

```bash
git commit -m "Make null pointer pattern easier to complete"
```

---

# まとめ

このステップでは、

* `src/index.html` のスコア表示を改善した
* `src/patterns.js` の Null Pointer パターンを変更した
* `git diff` を利用して変更内容を確認した
* VS Code の Diff ビューを利用した

実際の開発では、

```text
編集
↓
ゲームで確認
↓
差分確認
↓
ステージング
↓
差分確認
↓
コミット
```

という流れを繰り返します。

コミット前に差分を確認する習慣を付けることで、意図しない変更を履歴へ残すことを防げます。

---

[← Step 3](step3-exploring-history.md) | [Step 5 →](step5-working-with-branches.md)
