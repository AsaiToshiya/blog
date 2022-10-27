---
title: Gist のインデックス ページを作成する
date: 2020-10-10 17:07:06
updated: 2020-10-10 17:07:06
---

[gistly][1] を使用して Gist のインデックス ページを作成する。

例: https://gist.github.com/AsaiToshiya/b588634b8efeefc55c028f424315e3d9
<!-- more -->

## 手順

### 1. GitHub トークンを生成

  1. https://github.com/settings/tokens を開く
  2. 「Generate new token」をクリックする
  3. 「Note」に「gistly」を入力する
  4. 「Select scopes」で「gist」を選択する
  5. 「Generate token」をクリックする

### 2. gistly をインストール

```
> npm i -g gistly
```

### 3. GitHub へのアクセスを初期化

```
> gistly init --token <GitHub トークン>
```

### 4. gistly を実行

```
> gistly index --put
## [@AsaiToshiya](https://github.com/AsaiToshiya)'s gist index
* [troubleshooting-install-chocolatey.md](https://gist.github.com/AsaiToshiya/b371fd63481e726abbc921579ab1c2c0)
  * `gist:b371fd63481e726abbc921579ab1c2c0` Chocolatey のインストールで "このスクリプトには、悪質なコンテンツが含まれて いるため、ウイルス対策ソフトウェアによりブロックされています。" が表示された場合の対処方法
* [export-installed-chocolatey-packages.md](https://gist.github.com/AsaiToshiya/f1a69893e9cd80fe5b88ea01dc5cd77c)
  * `gist:f1a69893e9cd80fe5b88ea01dc5cd77c` Chocolatey でインストールしたパッケージをエクスポートする

---
❤️ [built with gistly](https://github.com/dcai/gistly)
```

### 5. インデックス ページを更新

```
> gistly index --put
## [@AsaiToshiya](https://github.com/AsaiToshiya)'s gist index
* [troubleshooting-install-chocolatey.md](https://gist.github.com/AsaiToshiya/b371fd63481e726abbc921579ab1c2c0)
  * `gist:b371fd63481e726abbc921579ab1c2c0` Chocolatey のインストールで "このスクリプトには、悪質なコンテンツが含まれ ているため、ウイルス対策ソフトウェアによりブロックされてい ます。" が表示された場合の対処方法
* [export-installed-chocolatey-packages.md](https://gist.github.com/AsaiToshiya/f1a69893e9cd80fe5b88ea01dc5cd77c)
  * `gist:f1a69893e9cd80fe5b88ea01dc5cd77c` Chocolatey でインストールしたパッケージをエクスポートする
* [index.md](https://gist.github.com/AsaiToshiya/b588634b8efeefc55c028f424315e3d9)
  * `gist:b588634b8efeefc55c028f424315e3d9` gist index
* [create-gist-index-page.md](https://gist.github.com/AsaiToshiya/3d5c0e4f881dfb4e5b076880fb79204e)
  * `gist:3d5c0e4f881dfb4e5b076880fb79204e` Gist のインデックス ページを作成する

---
❤️ [built with gistly](https://github.com/dcai/gistly)
```


 [1]: https://github.com/dcai/gistly