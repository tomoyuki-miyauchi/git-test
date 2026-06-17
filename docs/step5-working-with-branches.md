# Step 5: ブランチを使った機能開発

## このステップで学ぶこと

* ブランチの役割
* 機能ごとに開発を分離する方法
* ブランチをマージする方法
* VS Codeでブランチを操作する方法

---

# なぜブランチが必要なのか？

これまでの演習では、すべての変更を `main` ブランチへ直接コミットしていました。

しかし実際の開発では、

* 開発途中で動かなくなる
* 複数の機能を並行して開発したい
* バグ修正と機能追加を同時に進めたい

といった状況が頻繁に発生します。

そこで利用するのが **ブランチ** です。

ブランチを利用すると、

> 「完成するまで安全な場所で開発する」

ことができます。

---

# 演習1: ハイスコア機能を完成させる

前回の演習では画面上に High Score を表示しました。

しかし実際には値を保存していないため、ページを更新すると消えてしまいます。

今回は専用ブランチを作成してこの問題を修正します。

---

## 現在の履歴を確認する

まず現在の履歴を確認します。

```bash
git log --all --graph --oneline
```

履歴が一直線になっていることを確認してください。

---

## ブランチを作成する

新しいブランチを作成して移動します。

```bash
git branch fix-incomplete-high-score
git checkout fix-incomplete-high-score
```

ブランチ一覧を確認します。

```bash
git branch --list
```

現在のブランチには `*` が付きます。

---

## index.js を開く

`src/index.js` を開いてください。

---

## ハイスコア変数を追加する

40行目付近にあるスコア変数の近くへ追加します。

変更前:

```javascript
let score = 0;
```

変更後:

```javascript
let score = 0;
let highScore = 0;
```

コミットします。

```bash
git add src/index.js
git commit -m "Add new variable for tracking high score"
```

---

## 保存済みハイスコアを読み込む

60行目付近のゲーム初期化処理を探してください。

スコア表示を初期化しているコードの直後へ追加します。

```javascript
// Load high score from localStorage
highScore = parseInt(localStorage.getItem("stackOverflownHighScore")) || 0;
document.getElementById("high-score").textContent = highScore;
```

コミットします。

```bash
git add src/index.js
git commit -m "Add loading of stored high score"
```

---

## スコア更新処理を修正する

300行目付近にある

```javascript
function updateScore()
```

を探してください。

関数全体を以下へ置き換えます。

```javascript
function updateScore() {
  document.getElementById("score").textContent = score;

  if (score > highScore) {
    highScore = score;
    document.getElementById("high-score").textContent = highScore;
    localStorage.setItem("stackOverflownHighScore", highScore);
  }
}
```

この変更によって、

* ハイスコア更新
* ハイスコア表示更新
* ブラウザへの保存

が行われるようになります。

コミットします。

```bash
git add src/index.js
git commit -m "Add logic to keep track of highest score"
```

---

## 動作確認

ゲームをプレイしてスコアを獲得してください。

その後ページを再読み込みし、

ハイスコアが保持されていることを確認しましょう。

---

## ブランチの履歴を確認する

```bash
git log --all --graph --oneline
```

`main` よりも先に進んだブランチが表示されるはずです。

---

## mainへ戻る

```bash
git checkout main
```

---

## 機能をマージする

今回は履歴を分かりやすくするため、

マージコミットを作成します。

```bash
git merge --no-ff fix-incomplete-high-score -m "Fix high score tracker"
```

---

## マージ結果を確認する

```bash
git log --all --graph --oneline
```

ブランチが統合された履歴を確認してください。

---

## ブランチを削除する

開発が完了したため削除します。

```bash
git branch --delete fix-incomplete-high-score
```

ブランチ名だけが削除されます。

コミット履歴は残るので安心してください。

---

# 演習2: レベルシステムを追加する

次はVS Codeを利用して新機能を追加します。

---

## ブランチを作成する

左下のブランチ名をクリックします。

新しいブランチを作成してください。

```text
add-level-counter
```

---

## レベル表示を追加する

`src/index.html`

20行目付近にあるスコア表示エリアを探してください。

High Scoreの直後へ追加します。

```html
<h3>Level</h3>
<div class="score" id="level">1</div>
```

コミットメッセージ:

```text
Add element to display current level
```

---

## レベル変数を追加する

`src/index.js`

40行目付近にあるスコア変数の近くへ追加します。

```javascript
let level = 1;
let patternsCleared = 0;
```

コミットメッセージ:

```text
Add variables for level and clear counter
```

---

## レベルアップ処理を追加する

`src/index.js`

270行目付近にある

```javascript
function checkPatternMatch()
```

を探してください。

関数全体を以下へ置き換えます。

```javascript
function checkPatternMatch() {
  for (let startRow = 0; startRow <= ROWS - PATTERN_SIZE; startRow++) {
    for (let startCol = 0; startCol <= COLS - PATTERN_SIZE; startCol++) {
      if (matchesPattern(startRow, startCol)) {
        clearPattern(startRow, startCol);
        score += 100;
        patternsCleared++;

        if (patternsCleared % 5 === 0) {
          level++;
          dropInterval = Math.max(200, 1000 - (level - 1) * 100);
          document.getElementById("level").textContent = level;
        }

        updateScore();
        setNewTargetPattern();
        return;
      }
    }
  }
}
```

この変更により、

* パターンを5回消すごとにレベルアップ
* ブロック落下速度の上昇
* レベル表示の更新

が行われます。

コミットメッセージ:

```text
Add logic to calculate level
```

---

## 動作確認

ゲームをプレイしてレベルが上昇することを確認してください。

レベルアップ時に落下速度も速くなることを確認しましょう。

---

## Graphビューを確認する

Source Control の Graph を確認してください。

今回のブランチと先ほどのハイスコア修正ブランチが履歴として表示されているはずです。

---

## mainへマージする

左下のブランチ表示から `main` へ切り替えます。

その後、

```text
...
↓
Branch
↓
Merge
```

を選択します。

`add-level-counter` をマージしてください。

---

## ブランチを削除する

同じメニューから

```text
Delete Branch
```

を選択します。

---

# まとめ

このステップでは、

* ブランチを利用した機能開発
* ハイスコア機能の完成
* レベルシステムの追加
* CLIによるマージ
* VS Codeによるマージ

を体験しました。

実際の開発では、

```text
main
 ├─ feature-a
 ├─ feature-b
 └─ bugfix-c
```

のように機能ごとにブランチを分けて開発することが一般的です。

---

[← Step 4](step4-comparing-changes.md) | [Step 6 →](step6-introduction-to-collaboration.md)
