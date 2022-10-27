---
title: Raspberry Pi で LED を点滅させる
date: 2020-11-26 19:06:49
updated: 2020-12-17 13:02:53
---

Raspberry Pi で LED を点滅させるサンプル。

スクリプトを実行すると 0.5 秒間隔で LED が点滅して、Ctrl-C でスクリプトを終了する。
<!-- more -->
## 配線図

![blinking-led-on-raspberry-pi.png](blinking-led-on-raspberry-pi/blinking-led-on-raspberry-pi.png)

* LED: 取り付ける向きに注意する。足の長い方がプラス (アノード)、短い方がマイナス (カソード)。
* ジャンパー ワイヤー (赤): BCM4 (ピン番号 7)
* ジャンパー ワイヤー (黒): GND
* 抵抗: 1kΩ

## スクリプト

ledblink.py:

```python
#!/usr/bin/python
# -*- coding: utf-8 -*-

import RPi.GPIO as GPIO
import time

PIN = 4

GPIO.setmode(GPIO.BCM)
GPIO.setup(PIN, GPIO.OUT)

try:
    while True:
        # 点灯
        GPIO.output(PIN, GPIO.HIGH)
        time.sleep(0.5)

        # 消灯
        GPIO.output(PIN, GPIO.LOW)
        time.sleep(0.5)
except KeyboardInterrupt:
    # Ctrl-C
    GPIO.cleanup()
```

## スクリプトの実行

```bash
$ chmod u+x ledblink.py # 実行権限を付与
$ ./ledblink.py # 実行
```

## トラブルシューティング

### 配線すると、LED が点灯する

以下のコマンドを実行して LED を消灯できる。

```bash
$ gpio -g mode 4 out
$ gpio -g write 4 0
```

### スクリプトを実行すると "This channel is already in use" が表示される

```bash
$ ledblink.py
/home/pi/bin/ledblink.py:10: RuntimeWarning: This channel is already in use, continuing anyway.  Use GPIO.setwarnings(False) to disable warnings.
  GPIO.setup(PIN, GPIO.OUT)
```

他のプログラムで GPIO を制御していると表示される警告。

`GPIO.setup(PIN, GPIO.OUT)` の直前に `GPIO.setwarnings(False)` を追加すると、警告を表示しないようにできる。