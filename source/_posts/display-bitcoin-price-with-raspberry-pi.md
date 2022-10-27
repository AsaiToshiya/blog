---
title: Raspberry Pi でビットコインの価格を表示する
date: 2022-02-16 23:28:49
updated: 2022-02-16 23:28:49
---

bitFlyer の [API][1] と MAX7219 7 セグメント LED を使用して、ビットコインの価格をリアルタイムで表示するサンプル。

このサンプルでは、「[Raspberry Pi で 7 セグメント LED を使用する][2]」の手順 1 から手順 3 までが完了していることを前提とする。
<!-- more -->
## python-socketio をインストール

bitFlyer とリアルタイム通信するために、ここでは Socket.IO の Python 実装である [python-socketio][3] を使用する。

```bash
pip install "python-socketio[client]"
```

## スクリプト

bitcoin_ticker.py:

```python
#!/usr/bin/env python
# -*- coding: utf-8 -*-

import socketio
from luma.led_matrix.device import max7219
from luma.core.interface.serial import spi, noop
from luma.core.virtual import sevensegment

# チャンネル
CHANNEL = "lightning_ticker_BTC_JPY"

# 7 セグメント LED
serial = spi(port=0, device=0, gpio=noop())
device = max7219(serial, cascaded=1)
seg = sevensegment(device)

# Socket.IO
sio = socketio.Client()

# 7 セグメント LED の桁数
digits = seg.device.width

@sio.event
def connect():
    sio.emit("subscribe", CHANNEL)

@sio.on(CHANNEL)
def on_subscribe(data):
    # 最終取引価格を表示する
    ltp = str(data["ltp"])
    padding = " " * (digits - len(ltp)) # 右寄せにするためのパディング
    seg.text = padding + ltp

# 7 セグメント LED の明るさを下げる
seg.device.contrast(0)

# bitFlyer に接続する
sio.connect("https://io.lightstream.bitflyer.com", transports=["websocket"])
sio.wait()
```

チャンネルには、`lightning_ticker_BTC_JPY` の他に、`lightning_ticker_FX_BTC_JPY` や `lightning_ticker_ETH_BTC` など、[マーケットの一覧][4]で取得できるものを指定できる。

## スクリプトの実行

```bash
$ chmod u+x bitcoin_ticker.py # 実行権限を付与
$ ./bitcoin_ticker.py # 実行
```

Ctrl-C でスクリプトを終了する。

[1]: https://lightning.bitflyer.com/docs
[2]: /using-seven-segment-displays-on-raspberry-pi
[3]: https://python-socketio.readthedocs.io/
[4]: https://lightning.bitflyer.com/docs?lang=ja#%E3%83%9E%E3%83%BC%E3%82%B1%E3%83%83%E3%83%88%E3%81%AE%E4%B8%80%E8%A6%A7
