---
title: Raspberry Pi で 7 セグメント LED を使用する
date: 2022-02-11 01:14:34
updated: 2022-02-11 01:23:42
---

![max7219-8-digit-7-segment-display.jpg](using-seven-segment-displays-on-raspberry-pi/max7219-8-digit-7-segment-display.jpg)

Raspberry Pi で MAX7219 7 セグメント LED を使用する方法。

ここでは、MAX7219 用のディスプレイ ドライバとして [luma.led_matrix][1] を使用する。
<!-- more -->
## 環境

- Raspberry Pi Zero WH
- Raspberry Pi OS 2022-01-28 (Bullseye)

## 手順

### 1. モジュールを接続

| モジュール | Pi GPIO       | ピン番号 |
| ---------- | ------------- | -------- |
| VCC        | 5V            | 2        |
| GND        | GND           | 6        |
| DIN        | GPIO10 (MOSI) | 19       |
| CLK        | GPIO11 (CLK)  | 23       |
| CS         | GPIO8 (CE0)   | 24       |

### 2. SPI を有効化

`raspi-config` コマンド -> 「3 Interface Options」-> 「P4 SPI」で変更する。

```bash
sudo raspi-config
```

![step-2-1.png](using-seven-segment-displays-on-raspberry-pi/step-2-1.png)

![step-2-2.png](using-seven-segment-displays-on-raspberry-pi/step-2-2.png)

![step-2-3.png](using-seven-segment-displays-on-raspberry-pi/step-2-3.png)

### 3. luma.led_matrix をインストール

```bash
sudo -H pip install --upgrade --ignore-installed pip setuptools
sudo python3 -m pip install --upgrade luma.led_matrix
```

### 4. サンプル プログラムのダウンロードと実行

GitHub の[リポジトリ][2]をクローンして、サンプル プログラムを実行する。

```bash
git clone https://github.com/rm-hull/luma.led_matrix
cd luma.led_matrix
python examples/sevensegment_demo.py # 実行
```

[1]: https://luma-led-matrix.readthedocs.io/
[2]: https://github.com/rm-hull/luma.led_matrix
