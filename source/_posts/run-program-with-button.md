---
title: ボタンでプログラムを実行する
date: 2020-12-03 23:44:08
updated: 2020-12-17 13:15:40
tags: [Raspberry Pi]
---

ボタンでプログラムを実行するサンプル。

ボタンを押すと、プログラムを実行する。

もう一度ボタンを押すと、プログラムを終了する。

このサンプルでは、「[Raspberry Pi で LED を点滅させる][1]」のスクリプトを実行する。
<!-- more -->
## 配線図

![run-program-with-button.png](run-program-with-button/run-program-with-button.png)

* ジャンパー ワイヤー (赤): BCM17 (ピン番号 11)
* ジャンパー ワイヤー (黒): GND

## スクリプト

launcher.py:

```python
#!/usr/bin/python
# -*- coding: utf-8 -*-

import RPi.GPIO as GPIO
import subprocess

PIN = 17
CMD = "/home/pi/bin/ledblink.py" # 実行するプログラム

GPIO.setmode(GPIO.BCM)

# プルアップ抵抗を有効にする
GPIO.setup(PIN, GPIO.IN, pull_up_down=GPIO.PUD_UP)

p = None

try:
    while True:
        # 立ち下がりエッジが検出されるまで待機する
        GPIO.wait_for_edge(PIN, GPIO.FALLING)
    
        if p is None:
            # プログラムを実行する
            p = subprocess.Popen("exec " + CMD, shell=True)
        else:
            # プログラムを終了する
            p.kill()
            p = None
except KeyboardInterrupt:
    # Ctrl-C
    GPIO.cleanup()
```

## ボタンでプログラムの実行と終了

以下のコマンドでスクリプトを実行してからボタンを押すと、プログラムが実行される。

```bash
$ chmod u+x launcher.py # 実行権限を付与
$ ./launcher.py # 実行
```

もう一度ボタンを押すと、プログラムが終了する。

Ctrl-C でスクリプト自身を終了する。


 [1]: /blinking-led-on-raspberry-pi
