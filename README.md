# vcl Git勉強会用リポジトリ

## 概要

このリポジトリでは、GitHub公式チュートリアル  
https://github.com/skills/introduction-to-git  
をローカル環境で実行していきます。

---

## GitHub Flow

![GitHub Flow](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F196629%2F69a8f5b8-f9a6-1129-f467-21524fdc647c.png?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&w=1400&fit=max&s=2a5de66b9fe432e19d84bbc00bb8fd5b)

上図の GitHub Flow のように、このリポジトリをローカル環境に clone し、  
自分の GitHub アカウントで作成したリモートリポジトリへ push します。

> [!NOTE]
> Fork や Pull Request を行うと元リポジトリの作成者に通知が届くため、  
> 今回はそれらを使用しない運用にしています。

変更手順の詳細は、このリポジトリの Issue に記載されています。

---

# 手順

## 1. リポジトリを clone

PowerShell などで以下を実行します。

```bash
git clone https://github.com/HirotoKaburagi/skills-introduction-to-git.git
```

---

## 2. 自分の GitHub アカウントでリポジトリを作成

GitHub 上で新しいリポジトリを作成してください。

---

## 3. push 先を自分のリポジトリへ変更

```bash
git remote set-url origin <新しいURL>
```

例:

```bash
git remote set-url origin https://github.com/your-name/skills-introduction-to-git.git
```

---

## 4. 最初のコミットへ戻す

この時点では演習終了後の状態になっているため、最初のコミットへ戻します。

```bash
git checkout 831cd6f90ff1e444109ab7e645a572517d3f21ab
```

---

## 5. 作業用ブランチを作成

```bash
git checkout -b dev
```

---

## 6. Issue のチュートリアルを実行

https://github.com/HirotoKaburagi/skills-introduction-to-git/issues/1
上記のURLに従って作業を進めます。

---

## 7. 自分のリモートリポジトリへ push

```bash
git push origin dev
```

---

# 補足

現在の remote 設定は以下で確認できます。

```bash
git remote -v
```

ブランチ一覧の確認:

```bash
git branch
```
