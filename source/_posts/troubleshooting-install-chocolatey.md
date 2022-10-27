---
title: Chocolatey のインストールで "このスクリプトには、悪質なコンテンツが含まれているため、ウイルス対策ソフトウェアによりブロックされています。" が表示された場合の対処方法
date: 2020-10-09 14:13:21
updated: 2020-10-09 14:13:21
---

```powershell
PS> Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
発生場所 行:1 文字:1
+ Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.Service ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
このスクリプトには、悪質なコンテンツが含まれているため、ウイルス対策ソフトウェアによりブロックされています。
    + CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordException
    + FullyQualifiedErrorId : ScriptContainedMaliciousContent
```
<!-- more -->

## 手順

### 1. インストール スクリプトをダウンロード

https://chocolatey.org/install.ps1

### 2. インストール スクリプトを実行

実行ポリシーを変更して、インストール スクリプトを実行する。

```powershell
PS> Set-ExecutionPolicy Bypass -Scope Process -Force
PS> C:\Users\User\Downloads\install.ps1
PS> Set-ExecutionPolicy Restricted -Scope Process -Force
```

### 3. インストールを確認

```powershell
PS> choco
Chocolatey v0.10.15
```


 [1]: https://chocolatey.org/