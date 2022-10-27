---
title: 人感センサーで LED を点灯させる
date: 2020-12-10 00:16:49
updated: 2020-12-17 13:16:20
tags: [Raspberry Pi]
---

人感センサーの [HC-SR501][1] を使用して、LED を点灯させるサンプル。

スクリプトの実行後に人感センサーが動きを検知すると、LED が点灯する。
<!-- more -->
## [HC-SR501][1] について

[HC-SR501][1] は、赤外線センサー (PIR センサー) で人間が放射する赤外線を検知する。

![hc-sr501.jpg](turn-on-led-with-pir-sensor/hc-sr501.jpg)  
_出典: [HC-SR501 PIR MOTION DETECTOR][1]_

- Output:  
  出力ピン。High (3.3v) または Low (0v)。

- Power:  
  電源ピン。DC 4.5 V ～ 20 V。

- Jumper Set:  
  High を出力するタイミングを制御するためのピン。短絡コネクタが「H」の位置にある場合は、リピート トリガーとして設定され、動きを検知したタイミングで High が出力される。短絡コネクタが「L」の位置にある場合は、シングル トリガーとして設定され、Output が Low の状態のときに動きを検知したタイミングで High が出力される。

- Sensitivity Adjust:  
  検知範囲を調整するための半固定抵抗器。左に回すと範囲が狭くなり (最小 3 メートル)、右に回すと範囲が広くなる (最大 7  メートル)。

- Time Delay Adjust:  
  High を出力する時間を調整するための半固定抵抗器。左に回すと時間が短くなり (最小 3 秒)、右に回すと時間が長くなる (最大 5  分)。

## 配線図

![turn-on-led-with-pir-sensor.png](turn-on-led-with-pir-sensor/turn-on-led-with-pir-sensor.png)

- ジャンパー ワイヤー (赤): 5 V (ピン番号 2)
- ジャンパー ワイヤー (黄): BCM27 (ピン番号 13)
- ジャンパー ワイヤー (紫): BCM22 (ピン番号 15)
- ジャンパー ワイヤー (黒): GND
- 抵抗: 1kΩ

## スクリプト

pir.py:

```python
#!/usr/bin/python
# -*- coding: utf-8 -*-

import RPi.GPIO as GPIO
import time

PIR_PIN = 27
LED_PIN = 22

GPIO.setmode(GPIO.BCM)
GPIO.setup(PIR_PIN, GPIO.IN)
GPIO.setup(LED_PIN, GPIO.OUT)

try:
    while True:
        if GPIO.input(PIR_PIN): # 1 (High)
            # LED を点灯する
            GPIO.output(LED_PIN, GPIO.HIGH)
        else:
            # LED を消灯する
            GPIO.output(LED_PIN, GPIO.LOW)

        time.sleep(0.1)
except KeyboardInterrupt:
    # Ctrl-C
    GPIO.cleanup()
```

## スクリプトの実行

```bash
$ chmod u+x pir.py # 実行権限を付与
$ ./pir.py # 実行
```

[1]: https://www.mpja.com/download/31227sc.pdf
