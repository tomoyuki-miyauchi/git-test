# Step 1: Gitとバージョン管理の基礎

## このステップで学ぶこと

* Gitとは何か
* バージョン管理システムの役割
* Gitを利用するメリット
* Gitの基本コマンド
* Gitのユーザー設定

---

## バージョン管理とは？

プログラムやドキュメントを開発していると、次のような問題が発生します。

* 誤ってファイルを上書きしてしまった
* 昨日まで動いていたコードに戻したい
* 複数人で同じファイルを編集したい
* 変更履歴を確認したい

そのような問題を解決するために利用されるのが**バージョン管理システム（Version Control System）**です。

---

## Gitを使わない場合によくある例

次のようなファイルを見たことはありませんか？

```text
report.docx
report_final.docx
report_final_v2.docx
report_final_v2_fix.docx
report_final_v2_fix_really_final.docx
```

また、

* 「いつ壊れたのかわからない」
* 「最新版はどれ？」
* 「誰が変更したの？」

といった状況も発生しがちです。

Gitを利用すると、これらの問題を効率的に管理できます。

---

## Gitとは？

Gitは分散型バージョン管理システム（Distributed Version Control System）です。

各開発者がリポジトリの履歴を完全に保持するため、

* オフラインで作業できる
* バックアップ性が高い
* 柔軟な開発フローを構築できる

といった特徴があります。

---

## Gitが解決する問題

Gitを利用すると次のようなことが可能になります。

* 変更履歴の管理
* 過去バージョンへの復元
* 実験的な変更の作成
* 複数人での並行開発
* コードレビュー
* チーム開発

---

## Gitを利用する方法

Gitはさまざまな環境から利用できます。

### コマンドライン

最も基本的な利用方法です。

```bash
git status
git add
git commit
git push
```

### GUIツール

* GitHub Desktop
* Sourcetree
* GitKraken
* TortoiseGit

### IDE・エディタ

* Visual Studio Code
* JetBrains IDE
* Xcode
* Vim
* Emacs

---

# 演習1: Gitの確認

Gitがインストールされていることを確認します。

```bash
git --version
```

実行例:

```text
git version 2.xx.x
```

---

## Gitのヘルプを表示

```bash
git --help
```

利用可能なコマンドやオプションを確認できます。

---

# 演習2: Gitのユーザー設定

Gitではコミット作成者の情報を記録します。

## ユーザー名の設定

以下のコマンドを実行してください。

```bash
git config --global user.name "Your Name"
```

例:

```bash
git config --global user.name "Taro Yamada"
```

---

## メールアドレスの設定

```bash
git config --global user.email "your-email@example.com"
```

例:

```bash
git config --global user.email "taro@example.com"
```

GitHubを利用する場合は、GitHubが提供する noreply メールアドレスの利用も検討してください。

---

## 設定内容の確認

```bash
git config --global --list
```

実行結果の例:

```text
user.name=Taro Yamada
user.email=taro@example.com
```

---

# まとめ

このステップでは、

* Gitとは何か
* バージョン管理の目的
* Gitの基本的な利用方法
* Gitの初期設定

について学習しました。

次のステップでは、実際にGitリポジトリを操作しながら、コミットや履歴管理を体験します。

[Step 2 →](step2-first-repository.md)