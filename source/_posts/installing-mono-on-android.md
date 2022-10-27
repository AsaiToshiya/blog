---
title: Mono を Android にインストールする
date: 2020-10-16 10:58:15
updated: 2020-10-16 10:58:15
---
<p></p>

<!-- more -->
## 手順

### 1. Termux をインストール

https://play.google.com/store/apps/details?id=com.termux

### 2. wget をインストール

```bash
$ pkg install wget
```

### 3. $PREFIX に移動

```bash
$ cd $PREFIX
```

### 4. Mono をインストール

インストールするファイルは、端末の CPU アーキテクチャーによって異なる。

ARM64:

```bash
$ wget https://github.com/IanusInferus/termux-mono/releases/download/v20201017/mono-termux.6.12.0.90-arm64-androideabi24.tar.xz
$ tar Jxf mono-termux.6.12.0.90-arm64-androideabi24.tar.xz
$ rm mono-termux.6.12.0.90-arm64-androideabi24.tar.xz
```

ARMv7:

```bash
$ wget https://github.com/IanusInferus/termux-mono/releases/download/v20201017/mono-termux.6.12.0.90-armv7a-androideabi21.tar.xz
$ tar Jxf mono-termux.6.12.0.90-armv7a-androideabi21.tar.xz
$ rm mono-termux.6.12.0.90-armv7a-androideabi21.tar.xz
```

### 5. Mono のパスを通す

```bash
$ echo 'export PATH=$PREFIX/local/bin:$PATH' >> ~/.bash_profile
$ source ~/.bash_profile
```

### 6. インストールを確認

```bash
$ mono --version
Mono JIT compiler version 6.12.0.90 (tarball Sat Oct 17 13:58:52 CST 2020)
Copyright (C) 2002-2014 Novell, Inc, Xamarin Inc and Contributors. www.mono-project.com
        TLS:
        SIGSEGV:       normal
        Notifications: epoll
        Architecture:  arm64
        Disabled:      none
        Misc:          softdebug
        Interpreter:   yes
        LLVM:          supported, not enabled.
        Suspend:       preemptive
        GC:            sgen
```

### 7. C# のコンパイルと実行

```bash
$ echo 'using System;class HelloWorld{static void Main(){Console.WriteLine("Hello, world!");}}' > HelloWorld.cs
$ mcs HelloWorld.cs
$ mono HelloWorld.exe
Hello, world!
```