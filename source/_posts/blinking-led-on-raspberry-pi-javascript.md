---
title: Raspberry Pi で LED を点滅させる (JavaScript)
date: 2021-12-15 10:10:06
updated: 2021-12-15 10:10:06
---

「[Raspberry Pi で LED を点滅させる][1]」の JavaScript 版。

このサンプルでは、GPIO の制御に [rpi-gpio][2]  を使用する。
<!-- more -->
## 配線図

「[Raspberry Pi で LED を点滅させる][1]」を参照。

## Node.js をインストール

```bash
$ sudo apt install -y nodejs npm
$ node -v
v10.24.0
$ npm -v
5.8.0
```

## rpi-gpio をインストール

```bash
$ mkdir led-blink
$ cd led-blink
$ npm init -y
$ npm install rpi-gpio
```

## スクリプト

ledblink.js:

```javascript
const gpio = require("rpi-gpio");

const PIN = 4;

// ピンの状態
let state = true;

gpio.setMode(gpio.MODE_BCM);
gpio.setup(PIN, gpio.DIR_OUT, () => {
  setInterval(() => {
    gpio.write(PIN, state);
    state = !state;
  }, 500);
});
```

## スクリプトの実行

```bash
$ node ledblink.js
```

Ctrl-C でスクリプトを終了する。

[1]: /blinking-led-on-raspberry-pi
[2]: https://github.com/JamesBarwell/rpi-gpio.js
