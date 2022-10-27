---
title: Raspberry Pi をセットアップする
date: 2022-01-25 00:01:47
updated: 2022-01-25 00:01:47
---

[Raspberry Pi Imager][1] を使用して Raspberry Pi  をセットアップする。
<!-- more -->
## 環境

- Raspberry Pi OS 2021-10-30 (Bullseye)
- Raspberry Pi Imager 1.6.2

## 手順

### 1. Raspberry Pi Imager をインストール

https://www.raspberrypi.org/software/

### 2. メモリー カードをフォーマット

インストールした Raspberry Pi Imager を起動する。

![step-2-1.png](setup-raspberry-pi/step-2-1.png)

「CHOOSE OS」をクリックする。

![step-2-2.png](setup-raspberry-pi/step-2-2.png)

一覧から「Erase」を選択する。

![step-2-3.png](setup-raspberry-pi/step-2-3.png)

「CHOOSE STORAGE」をクリックする。

![step-2-4.png](setup-raspberry-pi/step-2-4.png)

一覧からフォーマットするメモリー カードを選択する。

![step-2-5.png](setup-raspberry-pi/step-2-5.png)

「WRITE」をクリックする。

![step-2-6.png](setup-raspberry-pi/step-2-6.png)

「YES」をクリックする。

![step-2-7.png](setup-raspberry-pi/step-2-7.png)

メモリー カードのフォーマットが開始される。フォーマットが完了するまで数分かかる場合がある。

![step-2-8.png](setup-raspberry-pi/step-2-8.png)

「CONTINUE」をクリックする。

![step-2-9.png](setup-raspberry-pi/step-2-9.png)

### 3. OS とメモリー カードを選択

「ERASE」をクリックする。

![step-3-1.png](setup-raspberry-pi/step-3-1.png)

一覧から「Raspberry Pi OS (32-bit)」を選択する。

![step-3-2.png](setup-raspberry-pi/step-3-2.png)

「CHOOSE STORAGE」をクリックする。

![step-3-3.png](setup-raspberry-pi/step-3-3.png)

一覧から手順 2 でフォーマットしたメモリー カードを選択する。

![step-3-4.png](setup-raspberry-pi/step-3-4.png)

### 4. SSH を有効化 (必要な場合)

Ctrl + Shift + X で「Advanced options」を表示する。

![step-4-1.png](setup-raspberry-pi/step-4-1.png)

「Enable SSH」を選択する。

![step-4-2.png](setup-raspberry-pi/step-4-2.png)

「Set password for 'pi' user」に pi ユーザーのパスワードを入力する。

![step-4-3.png](setup-raspberry-pi/step-4-3.png)

### 5. Wi-Fi 設定 (必要な場合)

「Configure wifi」を選択する。

![step-5-1.png](setup-raspberry-pi/step-5-1.png)

「SSID」と「Password」、「Wifi country」を適宜変更して、「Save」をクリックする。

![step-5-2.png](setup-raspberry-pi/step-5-2.png)

### 6. OS を書き込む

「WRITE」をクリックする。

![step-6-1.png](setup-raspberry-pi/step-6-1.png)

「YES」をクリックする。

![step-6-2.png](setup-raspberry-pi/step-6-2.png)

OS の書き込みが開始される。書き込みが完了するまで数分かかる場合がある。

![step-6-3.png](setup-raspberry-pi/step-6-3.png)

「CONTINUE」をクリックした後に PC からメモリー カードを取り出す。

![step-6-4.png](setup-raspberry-pi/step-6-4.png)

### 7. Raspberry Pi を起動

メモリー カードを Raspberry Pi に差し込んでから、電源を接続する。

### 8. パッケージの更新とアップグレード

ターミナルで以下のコマンドを実行する。

```bash
sudo apt update && sudo apt upgrade -y
```

[1]: https://www.raspberrypi.org/software/
