---
title: Android で SSH を使用して GitHub からリポジトリをクローンする
date: 2022-04-08 22:59:47
updated: 2022-04-08 22:59:47
---

Android で SSH を使用して GitHub からリポジトリをクローンするまでの手順。

ここでは、公開鍵が GitHub に登録されていることを前提とする。

<!-- more -->

## 手順

### 1. Termux をインストール

https://play.google.com/store/apps/details?id=com.termux

### 2. 内部ストレージへのシンボリック リンクを作成

```bash
$ termux-setup-storage
```

### 3. OpenSSH と Git をインストール

```bash
$ pkg install openssh git -y
```

インストールの途中で以下が表示される。何も入力せずに Enter キーを押す。

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

### 4. 秘密鍵をコピー

秘密鍵を `~/.ssh/` にコピーする。

例: 秘密鍵が内部ストレージの直下にある場合

```bash
$ cp ~/storage/shared/id_ed25519 ~/.ssh/id_ed25519
```

### 5. GitHub に接続

```bash
$ ssh -T -oStrictHostKeyChecking=no git@github.com
Warning: Permanently added 'github.com' (ED25519) to the list of known hosts.
Hi AsaiToshiya! You've successfully authenticated, but GitHub does not provide shell access.
```

### 6. リポジトリをクローン

```bash
$ cd ~/storage/shared
$ git clone git@github.com:AsaiToshiya/blog.git
```
