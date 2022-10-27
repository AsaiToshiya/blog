---
title: Digispark (ATtiny85) のオンボード LED を点滅させる
date: 2022-03-14 23:09:34
updated: 2022-03-14 23:09:34
---

Digispark のオンボード LED を点滅させるサンプル。

電源に接続すると、0.5 秒間隔でオンボード LED が点滅する。
<!-- more -->
## スケッチ

digispark_onboard_led_blink.ino:

```arduino
void setup() {
  pinMode(1, OUTPUT);
}

void loop() {
  // 点灯
  digitalWrite(1, HIGH);
  delay(500);

  // 消灯
  digitalWrite(1, LOW);
  delay(500);
}

```

オンボード LED が点滅しない場合 (Digispark がモデル B の場合) は、ピン (`1`) を `0` に変更する。