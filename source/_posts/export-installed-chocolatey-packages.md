---
title: Chocolatey でインストールしたパッケージをエクスポートする
date: 2020-10-09 20:30:49
updated: 2020-10-09 20:30:49
---
<p></p>

<!-- more -->
## 手順

### 1. スクリプトをダウンロード

https://gist.githubusercontent.com/alimbada/449ddf65b4ef9752eff3/raw/2cbc528668bc20aff55bc6a9cc340f7cd3dc6442/Export-Chocolatey.ps1

### 2. スクリプトを実行

実行ポリシーを変更して、インストール スクリプトを実行する。

```powershell
PS> Set-ExecutionPolicy Bypass -Scope Process -Force
PS> C:\Users\User\Downloads\Export-Chocolatey.ps1 > chocolatey.config
PS> Set-ExecutionPolicy Restricted -Scope Process -Force
```


 [1]: https://chocolatey.org/