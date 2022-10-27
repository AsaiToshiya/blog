---
title: Raspberry Pi をバックアップする
date: 2022-02-10 16:27:19
updated: 2022-02-10 16:27:19
---

[Win32 Disk Imager][1] を使用して Raspberry Pi をバックアップする。
<!-- more -->
## 手順

### 1. Win32 Disk Imager をインストール

https://win32diskimager.org/

### 2. バックアップ

インストールした Win32 Disk Imager を起動する。

![step-2-1.png](backup-raspberry-pi/step-2-1.png)

「Image File」にバックアップを保存するイメージ ファイルを指定して、「Device」でバックアップするメモリー カードを選択する。

![step-2-2.png](backup-raspberry-pi/step-2-2.png)

「Read」をクリックしてバックアップを開始する。バックアップが完了するまで数分かかる場合がある。

![step-2-3.png](backup-raspberry-pi/step-2-3.png)

バックアップが完了すると、 ダイアログが表示される。「OK」をクリックする。

![step-2-4.png](backup-raspberry-pi/step-2-4.png)

### 3. リストア

「Image File」にバックアップしたイメージ ファイルを指定して、「Device」でリストア先のメモリー カードを選択する。

![step-3-1.png](backup-raspberry-pi/step-3-1.png)

「Write」をクリックしてリストアを開始する。リストアが完了するまで数分かかる場合がある。

![step-3-2.png](backup-raspberry-pi/step-3-2.png)

リストアが完了すると、 ダイアログが表示される。「OK」をクリックする。

![step-3-3.png](backup-raspberry-pi/step-3-3.png)

## トラブルシューティング

### Win32 Disk Imager が起動しない

仮想的にドライブを割り当てるアプリケーション (例えば、Google ドライブ) を終了させる。

[1]: https://www.raspberrypi.org/software/
