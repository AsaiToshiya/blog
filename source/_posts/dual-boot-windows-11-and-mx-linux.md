---
title: Windows 11 と MX Linux をデュアル ブートする
tags: [Linux, Windows, MX Linux]
---

Windows 11 がインストールされているマシンに MX Linux をインストールしてデュアル ブートする。

ここでは、Windows 11 と MX Linux は物理的に異なるストレージにする。

<!-- more -->
## マシン構成

- CPU: Intel Core i5-12400F
- マザーボード: ASRock B760M Pro RS/D4 WiFi
- メモリー: DDR4-3200 2 x 16 GB (Crucial CT2K16G4DFRA32A)
- ストレージ: M.2 SSD 1 TB (Western Digital WD_BLACK SN770 NVMe SSD)、M.2 SSD 128 GB (Transcend TS128GMTE110S)
- ビデオ カード: NVIDIA GeForce RTX 3060 (玄人志向 GG-RTX3060-E12GB/OC/DF)
- OS: Windows 11 Home、MX Linux 23.2 (Libretto)
- UEFI バージョン: ASRock B760M Pro RS/D4 WiFi

## 手順

### 1. MX Linux のイメージ ファイル (.iso ファイル) をダウンロード

https://mxlinux.org/

![step-1-1.png](dual-boot-windows-11-and-mx-linux/step-1-1.png)

![step-1-2.png](dual-boot-windows-11-and-mx-linux/step-1-2.png)

### 2. Rufus をダウンロード

Live USB を作成するために Rufus をダウンロードする。

https://rufus.ie/ja/

![step-2-1.png](dual-boot-windows-11-and-mx-linux/step-2-1.png)

![step-2-2.png](dual-boot-windows-11-and-mx-linux/step-2-2.png)

### 3. Live USB を作成

ダウンロードした Rufus を起動する。

![step-3-1.png](dual-boot-windows-11-and-mx-linux/step-3-1.png)

「選択」をクリックして手順 1 でダウンロードした MX Linux のイメージ ファイルを選択する。

![step-3-2.png](dual-boot-windows-11-and-mx-linux/step-3-2.png)

「スタート」をクリックする。

![step-3-3.png](dual-boot-windows-11-and-mx-linux/step-3-3.png)

「OK」をクリックする。

![step-3-4.png](dual-boot-windows-11-and-mx-linux/step-3-4.png)

「はい(Y)」をクリックする。

![step-3-5.png](dual-boot-windows-11-and-mx-linux/step-3-5.png)

![step-3-6.png](dual-boot-windows-11-and-mx-linux/step-3-6.png)

「OK」をクリックする。

![step-3-7.png](dual-boot-windows-11-and-mx-linux/step-3-7.png)

イメージの書き込みが開始される。書き込みが完了するまで数分かかる場合がある。

![step-3-8.png](dual-boot-windows-11-and-mx-linux/step-3-8.png)

書き込みが完了したら、マシンをシャットダウンする。

![step-3-8.png](dual-boot-windows-11-and-mx-linux/step-3-9.png)

### 4. ストレージを換装

Windows 11 がインストールされたストレージを取り外して、MX Linux 用の新しいストレージを取り付ける。

![step-4.jpg](dual-boot-windows-11-and-mx-linux/step-4.jpg)

### 5. MX Linux (ライブ環境) を起動

作成した Live USB を接続してマシンを起動する。ブート画面が表示される。

(画像は VirtualBox)

![step-5-1.png](dual-boot-windows-11-and-mx-linux/step-5-1.png)

「Language - Keyboard - Timezone」で言語を変更する。

![step-5-2.png](dual-boot-windows-11-and-mx-linux/step-5-2.png)

![step-5-3.png](dual-boot-windows-11-and-mx-linux/step-5-3.png)

![step-5-4.png](dual-boot-windows-11-and-mx-linux/step-5-4.png)

![step-5-5.png](dual-boot-windows-11-and-mx-linux/step-5-5.png)

「<=== メインメニューへ戻る」でメインメニューに戻る。

![step-5-6.png](dual-boot-windows-11-and-mx-linux/step-5-6.png)

Enter キーを押して MX Linux を起動する。

![step-5-7.png](dual-boot-windows-11-and-mx-linux/step-5-7.png)

![step-5-8.png](dual-boot-windows-11-and-mx-linux/step-5-8.png)

### 6. MX Linux をインストール

MX Linux がライブ環境で起動する。「MX Linux をインストール」をクリックする。

(画像は VirtualBox)

![step-6-1.png](dual-boot-windows-11-and-mx-linux/step-6-1.png)

MX Linux インストーラーが起動する。

![step-6-2.png](dual-boot-windows-11-and-mx-linux/step-6-2.png)

ウィザードに従って MX Linux をインストールする。

![step-6-3.png](dual-boot-windows-11-and-mx-linux/step-6-3.png)

注: 「システムクロックに現地時刻を使用する」を選択しない場合、ハードウェア クロックは UTC になる。

![step-6-4.png](dual-boot-windows-11-and-mx-linux/step-6-4.png)

インストールが完了したら、マシンをシャットダウンする。

### 7. ストレージの取り付け

取り外した Windows 11 がインストールされたストレージを取り付ける。

(写真では CPU 側に取り付け)

![step-7.jpg](dual-boot-windows-11-and-mx-linux/step-7.jpg)

### 8. ブート順序を変更

マシンを起動して、UEFI 設定に入る。

ASRock のマザーボードの場合、起動する際に「F2」キーを押して UEFI 設定に入る。

![step-8-1.png](dual-boot-windows-11-and-mx-linux/step-8-1.png)

MX Linux が最初になるようにブート順序を変更する。

![step-8-2.png](dual-boot-windows-11-and-mx-linux/step-8-2.png)

設定を保存してマシンを再起動する。

### 9. GRUB メニューを更新

Windows 11 を GRUB メニューに表示させるために、ターミナルで以下のコマンドを実行する。

```bash
$ sudo update-grub
[sudo] user のパスワード:
Generating grub configuration file ...
Found theme: /boot/grub/themes/mx_linux/theme.txt
Found linux image: /boot/vmlinuz-6.1.0-21-amd64
Found initrd image: /boot/initrd.img-6.1.0-21-amd64
Found mtest-64.efi image: /boot/uefi-mt/mtest-64.efi
Found Windows Boot Manager on /dev/nvme0n1p1@/efi/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
done
```

参考: [Dual Boot – MX Linux](https://mxlinux.org/wiki/system/dual-boot/)
参考: [boot - Check GRUB_DISABLE_OS_PROBER - Ask Ubuntu](https://askubuntu.com/questions/1475735/check-grub-disable-os-prober)

### 10. Hello, MX Linux!

![step-10.png](dual-boot-windows-11-and-mx-linux/step-10.png)
