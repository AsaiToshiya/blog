---
title: Raspberry Pi のクリスマス ツリー
date: 2020-12-16 23:55:56
updated: 2020-12-16 23:55:56
---

GPIO Xmas Tree: http://www.pocketmoneytronics.co.uk/?page_id=491

![GPIO Xmas Tree](christmas-tree-for-raspberry-pi/gpio-xmas-tree.png)  
_出典: [GPIO Xmas Tree | pocketmoneytronics][1]_

GPIO Xmas Tree の LED を点滅させるサンプル。

スクリプトを実行すると 0.5 秒間隔でランダムに LED が点滅して、Ctrl-C でスクリプトを終了する。
<!-- more -->
## GPIO Xmas Tree の接続

LED が外側を向くように、GPIO Xmas Tree をピン番号 29 (BCM5) ～ 39 (GND) に接続する。

## スクリプト

tree.py:

```python
#!/usr/bin/python
# -*- coding: utf-8 -*-

import random
import RPi.GPIO as GPIO
import time

BOTTOM_LEFT = 26
BOTTOM_RIGHT = 5
MIDDLE_LEFT = 13
MIDDLE_RIGHT = 19
TOP = 6

# GPIO の設定
GPIO.setmode(GPIO.BCM)
GPIO.setup(BOTTOM_LEFT, GPIO.OUT)
GPIO.setup(BOTTOM_RIGHT, GPIO.OUT)
GPIO.setup(MIDDLE_LEFT, GPIO.OUT)
GPIO.setup(MIDDLE_RIGHT, GPIO.OUT)
GPIO.setup(TOP, GPIO.OUT)

try:
    while True:
        # ランダムに LED を点灯する
        GPIO.output(BOTTOM_LEFT, random.randint(0, 1))
        GPIO.output(BOTTOM_RIGHT, random.randint(0, 1))
        GPIO.output(MIDDLE_LEFT, random.randint(0, 1))
        GPIO.output(MIDDLE_RIGHT, random.randint(0, 1))
        GPIO.output(TOP, random.randint(0, 1))

        time.sleep(0.5)

        # LED を消灯する
        GPIO.output(BOTTOM_LEFT, GPIO.LOW)
        GPIO.output(BOTTOM_RIGHT, GPIO.LOW)
        GPIO.output(MIDDLE_LEFT, GPIO.LOW)
        GPIO.output(MIDDLE_RIGHT, GPIO.LOW)
        GPIO.output(TOP, GPIO.LOW)

        time.sleep(0.5)
except KeyboardInterrupt:
    # Ctrl-C
    GPIO.cleanup()
```

## スクリプトの実行

```bash
$ chmod u+x tree.py # 実行権限を付与
$ ./tree.py # 実行
```

[1]: http://www.pocketmoneytronics.co.uk/?page_id=491
