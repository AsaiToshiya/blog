---
title: Android で Hexo
date: 2022-04-11 14:07:36
updated: 2022-04-11 14:07:36
---
<p></p>

<!-- more -->
## 手順

### 1. Termux をインストール

https://f-droid.org/en/packages/com.termux/

### 2. パッケージの更新とアップグレード

```bash
pkg update && pkg upgrade
```

インストールの途中で「Do you want to continue? [Y/n]」が表示された場合は、y を入力して Enter キーを押す。また、以下のようなメッセージが表示された場合は、何も入力せずに Enter キーを押す。

```bash
Configuration file '/data/data/com.termux/files/usr/etc/tls/openssl.cnf'
 ==> File on system created by you or by a script.
 ==> File also in package provided by package maintainer.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : start a shell to examine the situation
 The default action is to keep your current version.
*** openssl.cnf (Y/I/N/O/D/Z) [default=N] ?
```

### 3. 内部ストレージへのシンボリック リンクを作成

```bash
termux-setup-storage
```

### 4. Node.js をインストール

```bash
pkg install nodejs -y
```

### 5. Hexo をインストール

```bash
npm install hexo-cli -g
```

### 6. ブログをセットアップ

```bash
cd ~/storage/shared
hexo init blog
cd blog
npm install --no-bin-links
```

### 7. 確認

```
hexo generate
hexo server
```

`http://localhost:4000` にアクセスする。
