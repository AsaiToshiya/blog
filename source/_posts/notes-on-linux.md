---
title: Linux のメモ
date: 2020-12-25 12:45:05
updated: 2022-02-06 02:58:23
tags: [メモ]
---

Linux の個人メモ。

随時更新。
<!-- more -->
## NAS のマウント

```bash
$ sudo mkdir /mnt/nas
$ sudo mount //192.168.3.8/Public /mnt/nas -o "user=ユーザー名,password=パスワード"
```

エラーが発生した場合は、 以下のコマンドでログを確認することができる。

```bash
$ tail -f /var/log/kern.log
```

## アンマウント

```bash
$ sudo umount /mnt/nas
```

## シャットダウン

```bash
$ sudo shutdown -h now
```

## 再起動

```bash
$ sudo reboot
```

## Noto フォントのインストール

```bash
$ sudo apt-get install fonts-noto
```

## スライドショー

```bash
$ sudo apt-get install feh
$ feh -Y -x -q -D 5 -F -z -r -d -e NotoSansCJK-Regular.ttc/12 -C /usr/share/fonts/opentype/noto /mnt/nas/Pictures/
```

feh コマンド オプション:

* `-Y`: ポインターを非表示にする。
* `-x`: ボーダーレス ウィンドウで表示する。
* `-q`: ファイルの読み込みに失敗した場合にエラー メッセージを表示しない。
* `-D 秒数`: スライドショーの間隔を指定する。
* `-F`: ウィンドウをフルスクリーンにする。
* `-z`: スライドショーをランダムに表示する。
* `-r`: ディレクトリーの画像を再帰的に表示する。
* `-d`: ファイル名を表示する。
* `-e フォント名/サイズ`: フォントを指定する。
* `-C パス`: フォントのディレクトリを指定する。

feh の詳細は、「[feh – a fast and light image viewer][1]」を参照。

## モニターの青みを抑える

```bash
$ xgamma -bgamma 0.1
```

## パッケージのアンインストール

```bash
sudo apt -y remove パッケージ
```

例:

```bash
sudo apt -y remove nodejs
```

## Node.js のダウングレード

1. Node.js のバージョン管理ツールの [n][2] をインストールする。

    ```bash
    sudo npm install -g n
    ```

2. [n][2] を実行する。

    ```bash
    sudo n バージョン
    ```

    例:

    ```bash
    sudo n 10
    ```

 [1]: https://feh.finalrewind.org/
 [2]: https://github.com/tj/n
