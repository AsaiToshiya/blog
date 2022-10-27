---
title: Vercel でデプロイするときに HTML をミニファイする
date: 2021-12-11 22:49:51
updated: 2021-12-11 23:03:44
---

注: Vercel は gzip と brotli をサポートしているため、通常、自前でのリソースのミニファイは不要。
<!-- more -->
## 手順

### 1. package.json ファイルの設定

package.json ファイルを作成していない場合は以下のコマンドで作成する。

```
npm init -y
```

ミニファイヤーの [HTMLMinifier][1] をインストールする。

```
npm install html-minifier --save-dev
```

package.json ファイルの `scripts` プロパティーに [HTMLMinifier][1] を実行するためのスクリプトを追加する。

ここでは、minify という名前で追加する。

package.json:

```json
{
  "name": "test",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "minify": "html-minifier --input-dir . --output-dir . --file-ext html --collapse-whitespace --minify-js true --minify-css true"
  },
  "repository": {
    "type": "git",
    "url": "git+https://github.com/AsaiToshiya/test.git"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "bugs": {
    "url": "https://github.com/AsaiToshiya/test/issues"
  },
  "homepage": "https://github.com/AsaiToshiya/test#readme",
  "devDependencies": {
    "html-minifier": "^4.0.0"
  }
}
```

### 2. Vercel の設定

[ダッシュボード][2]を表示して、HTML をミニファイするプロジェクトを選択する。

![step-2-1.png](minify-html-when-deploy-on-vercel/step-2-1.png)

「Settings」タブを選択する。

![step-2-2.png](minify-html-when-deploy-on-vercel/step-2-2.png)

「Project Settings」ページが表示される。

![step-2-3.png](minify-html-when-deploy-on-vercel/step-2-3.png)

「BUILD COMMAND」の「OVERRIDE」トグルをオンにして、以下のコマンドを入力する。

```
npm run minify
```

![step-2-4.png](minify-html-when-deploy-on-vercel/step-2-4.png)

「OUTPUT DIRECTORY」の「OVERRIDE」トグルをオンにして、`.` (カレント ディレクトリ) を入力する。

注: プレースホルダーに <q>\`public\` if it exists, or \`.\`</q> (存在する場合は \`public\`、存在しない場合は \`.\`) が記載されているが、`.` で上書きする必要がある。

![step-2-5.png](minify-html-when-deploy-on-vercel/step-2-5.png)

「Save」をクリックする。

![step-2-6.png](minify-html-when-deploy-on-vercel/step-2-6.png)

### 3. package.json ファイルのコミットとプッシュ

手順 1 で作成した package.json ファイルのコミットとプッシュを行う。

```
> git add package.json
> git commit -m "package.json を追加する"
> git branch -M main
> git push -u origin main
```

### 4. HTML のミニファイを確認

Vercel に戻り、「Overview」タブを選択する。

![step-4-1.png](minify-html-when-deploy-on-vercel/step-4-1.png)

スクリーン ショットをクリックする。

![step-4-2.png](minify-html-when-deploy-on-vercel/step-4-2.png)

表示されたページのソースを確認する。

![step-4-3.png](minify-html-when-deploy-on-vercel/step-4-3.png)

![step-4-4.png](minify-html-when-deploy-on-vercel/step-4-4.png)

[1]: https://github.com/kangax/html-minifier
[2]: https://vercel.com/dashboard
