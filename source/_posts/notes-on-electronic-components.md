---
title: 電子部品のメモ
date: 2022-02-03 09:11:20
updated: 2022-02-03 09:11:20
tags: [メモ]
---

電子部品の個人メモ。

随時更新。
<!-- more -->
## LED (発光ダイオード)

![LED](notes-on-electronic-components/led.jpg)  
_出典: [File:Electronic-Component-Red-LED.jpg - Wikimedia Commons][1]_

名前のとおり、光るダイオード。

極性があり、足の長い方がプラス (アノード)、短い方がマイナス (カソード)。

LED を光らせるための電圧は VF (順方向電圧)、電流は IF (順方向電流) で表される。

過大な電流が流れると LED が壊れるため、電流制限抵抗が必要。必要な抵抗値は、オームの法則により求めることができる。

Ω(オーム) = (V (電源電圧) - VF (順方向電圧)) / IF (順方向電流)

## 抵抗器

![抵抗器](notes-on-electronic-components/resistor.jpg)  
_出典: [File:Electronic-Axial-Lead-Resistors-Array.jpg - Wikimedia Commons][2]_

電流を制限したり、電圧を分圧したりするために使用する。抵抗の単位はΩ(オーム)。

抵抗にかかる電圧と抵抗に流れる電流は、オームの法則により計算することができる。

V (電圧) = Ω(オーム) x A (電流)

A (電流) = V (電圧) / Ω(オーム)

## タクト スイッチ

![タクト スイッチ](notes-on-electronic-components/tact-switch.jpg)  
_出典: [File:Tactile switches.jpg - Wikimedia Commons][3]_

タクタイル スイッチとも呼ばれる。

押した感触があるスイッチで、スイッチを押している間だけ導通する。

4 本の足は内部で 2 本ずつつながっている。

[1]: https://commons.wikimedia.org/wiki/File:Electronic-Component-Red-LED.jpg
[2]: https://commons.wikimedia.org/wiki/File:Electronic-Axial-Lead-Resistors-Array.jpg
[3]: https://commons.m.wikimedia.org/wiki/File:Tactile_switches.jpg
