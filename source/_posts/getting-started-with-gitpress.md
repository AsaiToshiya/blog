---
title: GitPress 事始め
date: 2020-11-09 23:29:37
updated: 2020-11-09 23:29:37
---

ブログ サービスの [GitPress][1] 事始め。
<!-- more -->
## 手順

### 1. リポジトリを作成

GitHub でブログ用のリポジトリを作成する。

![step-1.png](getting-started-with-gitpress/step-1.png)

### 2. GitPress にログイン

https://gitpress.io/login を開いて「Login with GitHub」をクリックする。

![step-2-1.png](getting-started-with-gitpress/step-2-1.png)

「Authorize gitpress-io」をクリックして GitPress を認証する。

![step-2-2.png](getting-started-with-gitpress/step-2-2.png)

プライベート リポジトリに連携させる場合は、「Skip and setup manually.」をクリックして手順  5 に進む。

![step-2-3.png](getting-started-with-gitpress/step-2-3.png)

### 3. リポジトリを連携

「Select a repository...」でリポジトリを選択する。

![step-3.png](getting-started-with-gitpress/step-3.png)

### 4. Webhook を許可

「Allow」をクリックする。

![step-4.png](getting-started-with-gitpress/step-4.png)

手順 7 に進む。

### 5. リポジトリを連携 (プライベート リポジトリの場合)

「Dashboard」をクリックして、ダッシュボードを表示する。

![step-5-1.png](getting-started-with-gitpress/step-5-1.png)

「Repo」をクリックする。

![step-5-2.png](getting-started-with-gitpress/step-5-2.png)

「Article Repo Url」に `git@` で始まるリポジトリの URL を入力して、「Save」をクリックする。

例: `git@github.com:AsaiToshiya/blog.git`

![step-5-3.png](getting-started-with-gitpress/step-5-3.png)

### 6. Webhook と Deploy key を許可 (プライベート リポジトリの場合)

「Allow」をクリックする。

![step-6.png](getting-started-with-gitpress/step-6.png)

### 7. ローカル リポジトリを準備

```
> mkdir blog
> cd blog
> git init
> git remote add origin https://github.com/AsaiToshiya/blog.git
```

### 8. Markdown ファイルのコミットとプッシュ

hello.md:

```markdown
# Hello

Hello, world!
```

```
> git add hello.md
> git commit -m "hello.md を追加する"
> git branch -M main
> git push -u origin main
```

### 9. 記事を確認

![step-9-1.png](getting-started-with-gitpress/step-9-1.png)

![step-9-2.png](getting-started-with-gitpress/step-9-2.png)

## トラブルシューティング

この画面が表示された場合は、以下の手順を実行して Webhook と Deploy key を設定する。

![troubleshooting.png](getting-started-with-gitpress/troubleshooting.png)

### 1. Webhook Url と Deploy key をコピー

「Dashboard」をクリックして、ダッシュボードを表示する。

![troubleshooting-1-1.png](getting-started-with-gitpress/troubleshooting-1-1.png)

「Repo」をクリックする。

![troubleshooting-1-2.png](getting-started-with-gitpress/troubleshooting-1-2.png)

「Repo Operations」の Webhook Url と Deploy key をコピーする。

![troubleshooting-1-3.png](getting-started-with-gitpress/troubleshooting-1-3.png)

### 2. Webhook を設定

GitHub でリポジトリを開いて「Settings」をクリックする。

![troubleshooting-2-1.png](getting-started-with-gitpress/troubleshooting-2-1.png)

「Webhooks」をクリックする。

![troubleshooting-2-2.png](getting-started-with-gitpress/troubleshooting-2-2.png)

「Add webhook」をクリックする。

![troubleshooting-2-3.png](getting-started-with-gitpress/troubleshooting-2-3.png)

「Payload URL」に、コピーした Webhook Url を貼り付ける。

![troubleshooting-2-4.png](getting-started-with-gitpress/troubleshooting-2-4.png)

「Add webhook」をクリックする。

![troubleshooting-2-5.png](getting-started-with-gitpress/troubleshooting-2-5.png)

### 3. Deploy key を設定

「Deploy keys」をクリックする。

![troubleshooting-3-1.png](getting-started-with-gitpress/troubleshooting-3-1.png)

「Add deploy key」をクリックする。

![troubleshooting-3-2.png](getting-started-with-gitpress/troubleshooting-3-2.png)

「Title」に「GitPress」を入力する。

![troubleshooting-3-3.png](getting-started-with-gitpress/troubleshooting-3-3.png)

「Key」に、コピーした Deploy key を貼り付けて、「Add key」をクリックする。

![troubleshooting-3-4.png](getting-started-with-gitpress/troubleshooting-3-4.png)

### 4. 記事を再構築

GitPress に戻り「Rebuild」をクリックする。

![troubleshooting-4.png](getting-started-with-gitpress/troubleshooting-4.png)

[1]: https://gitpress.io/
