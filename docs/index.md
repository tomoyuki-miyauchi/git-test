# vcl Git勉強会

このページは vcl Git勉強会用の教材です。

GitHub Skills の **Introduction to Git** をベースに、ローカル環境で実行できるよう再構成しています。

ゲームプログラムを実際に改造しながら、Gitの基本操作とGitHubを利用した開発フローを学びます。

---

## 演習用リポジトリ

```bash
git clone https://github.com/HirotoKaburagi/skills-introduction-to-git.git
```

自分のGitHubアカウントで新しいリポジトリを作成し、Push先を変更してください。

```bash
git remote set-url origin <自分のリポジトリURL>
```

演習開始時点のコミットから作業用ブランチを作成します。

```bash
git switch --create dev 831cd6f90ff1e444109ab7e645a572517d3f21ab
```

---

## 目次

* [Step 1: Gitの基礎と環境設定](step1-introduction.md)
* [Step 2: 最初のリポジトリを作成する](step2-first-repository.md)
* [Step 3: Gitの履歴を確認する](step3-exploring-history.md)
* [Step 4: 変更内容を確認する](step4-comparing-changes.md)
* [Step 5: ブランチを使った機能開発](step5-working-with-branches.md)
* [Step 6: GitHubを使った共同開発](step6-introduction-to-collaboration.md)

---

## この教材で学べること

* Gitによるバージョン管理
* コミットと履歴管理
* 差分確認
* ブランチ開発
* マージ
* GitHubを利用した共同開発
