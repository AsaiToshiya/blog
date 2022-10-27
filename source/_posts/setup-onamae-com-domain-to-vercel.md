---
title: Vercel にお名前.com のドメインを設定する
date: 2021-12-03 14:16:25
updated: 2021-12-03 14:16:25
---
<p></p>

<!-- more -->
## 手順

### 1. Vercel の設定

[ダッシュボード][1]を表示してドメインを設定するプロジェクトを選択する。

![step-1-1.png](setup-onamae-com-domain-to-vercel/step-1-1.png)

「View Domains」をクリックする。

![step-1-2.png](setup-onamae-com-domain-to-vercel/step-1-2.png)

以下の画面が表示される。

![step-1-3.png](setup-onamae-com-domain-to-vercel/step-1-3.png)

ドメインを入力して「Add」をクリックする。

![step-1-4.png](setup-onamae-com-domain-to-vercel/step-1-4.png)

「ADD」をクリックする。

![step-1-5.png](setup-onamae-com-domain-to-vercel/step-1-5.png)

ネーム サーバーが正しく構成されていないため、「Invalid Configuration」が表示される。

![step-1-6.png](setup-onamae-com-domain-to-vercel/step-1-6.png)

「or Nameservers」をクリックして、「Intended Nameservers」に表示されるネーム サーバーをメモしておく。

![step-1-7.png](setup-onamae-com-domain-to-vercel/step-1-7.png)

### 2. お名前.com の設定

「[ネームサーバー設定][2]」を表示する。

![step-2-1.png](setup-onamae-com-domain-to-vercel/step-2-1.png)

「1.ドメインの選択」でネーム サーバーを設定するドメインを選択する。

![step-2-2.png](setup-onamae-com-domain-to-vercel/step-2-2.png)

「2.ネームサーバーの選択」で「その他」タブを選択する。

![step-2-3.png](setup-onamae-com-domain-to-vercel/step-2-3.png)

「その他のネームサーバーを使う」を選択する。

![step-2-4.png](setup-onamae-com-domain-to-vercel/step-2-4.png)

「ネームサーバー1」と「ネームサーバー2」に先ほどメモしたネーム サーバーを入力して、「確認」をクリックする。

![step-2-5.png](setup-onamae-com-domain-to-vercel/step-2-5.png)

「OK」をクリックする。

![step-2-6.png](setup-onamae-com-domain-to-vercel/step-2-6.png)

![step-2-7.png](setup-onamae-com-domain-to-vercel/step-2-7.png)

ネーム サーバーの変更が反映されるまで数分かかる場合がある。

### 3. ドメインの設定を確認

Vercel に戻り、「Valid Configuration」が表示されていることを確認する。

![step-3.png](setup-onamae-com-domain-to-vercel/step-3.png)

[1]: https://vercel.com/dashboard
[2]: https://navi.onamae.com/domain/setting/ns
