---
title: Digispark (ATtiny85) 事始め
date: 2022-03-14 23:04:24
updated: 2022-03-14 23:04:24
---

![digispark.jpg](getting-started-with-digispark-attiny85/digispark.jpg)

マイコンの ATtiny85 を搭載した [Digispark][1] の事始め。

Digispark にスケッチ (プログラム) を書き込むための環境をセットアップする。
<!-- more -->
## 手順

### 1. Arduino IDE をインストール

https://www.arduino.cc/en/software

### 2. ボードマネージャをインストール

1. インストールした Arduino IDE を起動する。

   ![step-2-1.png](getting-started-with-digispark-attiny85/step-2-1.png)

2. 「ファイル」 > 「環境設定」をクリックする。

   ![step-2-2-1.png](getting-started-with-digispark-attiny85/step-2-2-1.png)

   「環境設定」ダイアログ ボックスが表示される。

   ![step-2-2-2.png](getting-started-with-digispark-attiny85/step-2-2-2.png)

3. 「追加のポードマネージャのURL」に以下の URL を入力して、「OK」をクリックする。

   `http://digistump.com/package_digistump_index.json`

   ![step-2-3.png](getting-started-with-digispark-attiny85/step-2-3.png)

4. 「ツール」 > 「ボード」 > 「ボードマネージャ...」をクリックする。

   ![step-2-4-1.png](getting-started-with-digispark-attiny85/step-2-4-1.png)

   「ボードマネージャ」ダイアログ ボックスが表示される。

   ![step-2-4-2.png](getting-started-with-digispark-attiny85/step-2-4-2.png)

5. テキスト フィールドに `Digispark` を入力する。

   ![step-2-5.png](getting-started-with-digispark-attiny85/step-2-5.png)

6. 一覧に「Digistump AVR Boards」が表示される。「インストール」をクリックする。

   ![step-2-6.png](getting-started-with-digispark-attiny85/step-2-6.png)

7. インストールが完了した後、「閉じる」をクリックする。

   ![step-2-7.png](getting-started-with-digispark-attiny85/step-2-7.png)

### 3. ドライバーをインストール

1. [Digistump.Drivers.zip][2] をダウンロードして解凍する。

2. DPinst.exe (32 ビット) または DPinst64.exe (64 ビット) をダブルクリックしてドライバーをインストールする。

3. Digispark を USB ポートに接続して、デバイス マネージャーで「libusb-win32 devices」 > 「Digispark Bootloader」が表示されていることを確認する。

   ![step-3-3.png](getting-started-with-digispark-attiny85/step-3-3.png)

### 4. スケッチを書き込む

注: Digispark は USB ポートから外しておく。

1. 「ツール」 > 「ボード」 > 「Digistump AVR Boards」から「Digispark (Default - 16.5mhz)」を選択する。

   ![step-4-1.png](getting-started-with-digispark-attiny85/step-4-1.png)

2. 「ツール」 > 「書込装置」から「Micronucleus」を選択する。

   ![step-4-2.png](getting-started-with-digispark-attiny85/step-4-2.png)

3. アップロード ボタン (右矢印ボタン) または「スケッチ」 > 「マイコンボードに書き込む」をクリックする。

   ![step-4-3.png](getting-started-with-digispark-attiny85/step-4-3.png)

4. コンソールに「Plug in device now... (will timeout in 60 seconds)」が表示されたら、Digispark を USB ポートに接続する。

   ![step-4-4.png](getting-started-with-digispark-attiny85/step-4-4.png)

5. 書き込みが完了すると、コンソールに「Micronucleus done. Thank you!」が表示される。

   ![step-4-5.png](getting-started-with-digispark-attiny85/step-4-5.png)

[1]: http://digistump.com/products/1
[2]: https://github.com/digistump/DigistumpArduino/releases/download/1.6.7/Digistump.Drivers.zip
