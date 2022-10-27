---
title: Vercel で静的サイトをホスティングする
date: 2021-11-27 03:36:52
updated: 2021-11-28 23:17:34
---

ホスティング プラットフォームの [Vercel][1] (ヴァーセル) と GitHub リポジトリを連携させて静的サイトを公開する。
<!-- more -->
## 手順

### 1. Vercel にログイン

https://vercel.com を開いて「Start Deploying」をクリックする。

![step-1-1.png](hosting-static-site-with-vercel/step-1-1.png)

「Import Git Repository」の「Continue with GitHub」をクリックする。

![step-1-2.png](hosting-static-site-with-vercel/step-1-2.png)

GitHub にログインしていない場合はログインする。

![step-1-3.png](hosting-static-site-with-vercel/step-1-3.png)

Vercel の認証を求められる。

![step-1-4.png](hosting-static-site-with-vercel/step-1-4.png)

「Authorize Vercel」をクリックして Vercel を認証する。

![step-1-5.png](hosting-static-site-with-vercel/step-1-5.png)

### 2. リポジトリを連携

「Select a Git Namespace」コンボ ボックスをクリックする。

![step-2-1.png](hosting-static-site-with-vercel/step-2-1.png)

「Add GitHub Namespace」をクリックする。

![step-2-2.png](hosting-static-site-with-vercel/step-2-2.png)

「Only select repositories」をクリックする。

![step-2-3.png](hosting-static-site-with-vercel/step-2-3.png)

「Select repositories」でリポジトリを選択する。

![step-2-4.png](hosting-static-site-with-vercel/step-2-4.png)

「Install」をクリックする。

![step-2-5.png](hosting-static-site-with-vercel/step-2-5.png)

### 3. デプロイ

「Import」をクリックする。

![step-3-1.png](hosting-static-site-with-vercel/step-3-1.png)

プロジェクトの詳細を入力する画面が表示される。すべてそのままにして、「Deploy」をクリックする。

![step-3-2.png](hosting-static-site-with-vercel/step-3-2.png)

デプロイが開始される。

![step-3-3.png](hosting-static-site-with-vercel/step-3-3.png)

デプロイが完了すると以下の画面が表示される。

![step-3-4.png](hosting-static-site-with-vercel/step-3-4.png)

### 4. Web サイトを確認

「Go to Dashboard」をクリックする。

![step-4-1.png](hosting-static-site-with-vercel/step-4-1.png)

スクリーン ショットをクリックして、デプロイされた Web サイトを確認する。

![step-4-2.png](hosting-static-site-with-vercel/step-4-2.png)

![step-4-3.png](hosting-static-site-with-vercel/step-4-3.png)

[1]: https://vercel.com
