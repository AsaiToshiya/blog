---
title: Raspberry Pi のメモ
date: 2020-11-11 00:07:38
updated: 2022-03-29 21:21:41
tags: [メモ]
---

Raspberry Pi の個人メモ。

随時更新。
<!-- more -->
## セットアップ

### セットアップ

「[Raspberry Pi をセットアップする][7]」を参照。

### MX Linux

1. [イメージ ファイル][13] (.img.zip ファイル) をダウンロードして解凍する。

2. Raspberry Pi Imager を起動する。

3. 「CHOOSE OS」 > 「Use custom」で、解凍したフォルダー内のイメージ ファイル (.img ファイル) を選択する。

4. 「CHOOSE STORAGE」でメモリー カードを選択する。

5. 「WRITE」をクリックする。

6. メモリー カードを Raspberry Pi に差し込んでから、電源を接続する。

   ![mxlinux.png](notes-on-raspberry-pi/mxlinux.png)

### Wi-Fi 設定 (ワイヤレス セットアップ)

`/boot` に `wpa_supplicant.conf` を作成する。

`wpa_supplicant.conf`:

```
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1
country=JP

network={
	ssid="アクセス ポイントの SSID"
	psk="パスワード"
}
```

### SSH の有効化 (ワイヤレス セットアップ)

`/boot` に `ssh` という名前の空のファイルを作成する。

### バックアップ

「[Raspberry Pi をバックアップする][8]」を参照。

## 設定

### VNC の有効化

`raspi-config` コマンド -> 「3 Interface Options」-> 「P3 VNC」で変更する。

```bash
pi@raspberrypi:~ $ sudo raspi-config
```

![vnc-1.png](notes-on-raspberry-pi/vnc-1.png)

![vnc-2.png](notes-on-raspberry-pi/vnc-2.png)

![vnc-3.png](notes-on-raspberry-pi/vnc-3.png)

### 解像度を変更

`raspi-config` コマンド -> 「2 Display Options」-> 「D1 Resolution」で変更する。

```bash
pi@raspberrypi:~ $ sudo raspi-config
```

![raspi-config-1.png](notes-on-raspberry-pi/raspi-config-1.png)

![raspi-config-2.png](notes-on-raspberry-pi/raspi-config-2.png)

![raspi-config-3.png](notes-on-raspberry-pi/raspi-config-3.png)

### 固定 IP アドレスを設定

1. `route` または `netstat -r` コマンドでルーターの IP アドレスを確認する。

    ```bash
    pi@raspberrypi:~ $ route
    カーネルIP経路テーブル
    受信先サイト    ゲートウェイ    ネットマスク   フラグ Metric Ref 使用数 インタフェース
    default         192.168.3.1     0.0.0.0         UG    302    0        0 wlan0
    172.17.0.0      0.0.0.0         255.255.0.0     U     0      0        0 docker0
    192.168.3.0     0.0.0.0         255.255.255.0   U     302    0        0 wlan0
    ```

    この場合、`default` の `192.168.3.1` がルーターの IP アドレス。
2. `/etc/dhcpcd.conf` に以下の内容を追加する。

    ```
    interface eth0 または wlan0
    static ip_address=設定する IP アドレス
    static routers=ルーターの IP アドレス
    static domain_name_servers=DNS サーバーの IP アドレス
    ```

    例:

    ```
    interface wlan0
    static ip_address=192.168.3.24
    static routers=192.168.3.1
    static domain_name_servers=192.168.3.1
    ```

### ホスト名を変更

`raspi-config` コマンド -> 「1 System Options」-> 「S4 Hostname」で変更する。

```bash
pi@raspberrypi:~ $ sudo raspi-config
```

![hostname-1.png](notes-on-raspberry-pi/hostname-1.png)

![hostname-2.png](notes-on-raspberry-pi/hostname-2.png)

![hostname-3.png](notes-on-raspberry-pi/hostname-3.png)

![hostname-4.png](notes-on-raspberry-pi/hostname-4.png)

### SPI の有効化

`raspi-config` コマンド -> 「3 Interface Options」-> 「P4 SPI」で変更する。

```bash
pi@raspberrypi:~ $ sudo raspi-config
```

![spi-1.png](notes-on-raspberry-pi/spi-1.png)

![spi-2.png](notes-on-raspberry-pi/spi-2.png)

![spi-3.png](notes-on-raspberry-pi/spi-3.png)

### カメラ モジュール v1 の有効化 (Bullseye)

`raspi-config` コマンド -> 「3 Interface Options」-> 「I1 Legacy Camera」で有効にする。

```bash
sudo raspi-config
```

![enable-camera-1.png](notes-on-raspberry-pi/enable-camera-1.png)

![enable-camera-2.png](notes-on-raspberry-pi/enable-camera-2.png)

![enable-camera-3.png](notes-on-raspberry-pi/enable-camera-3.png)

カメラ モジュールが有効になったかどうかは、`vcgencmd get_camera` コマンドで確認する。

```bash
pi@raspberrypi:~ $ vcgencmd get_camera
supported=1 detected=1
```

`detected=1` が有効。

### ロケールを変更

`raspi-config` コマンド -> 「5 Localization Options」-> 「L1 Locale」で変更する。

```bash
pi@raspberrypi:~ $ sudo raspi-config
```

![locale-1.png](notes-on-raspberry-pi/locale-1.png)

![locale-2.png](notes-on-raspberry-pi/locale-2.png)

![locale-3.png](notes-on-raspberry-pi/locale-3.png)

![locale-4.png](notes-on-raspberry-pi/locale-4.png)

![locale-5.png](notes-on-raspberry-pi/locale-5.png)

![locale-6.png](notes-on-raspberry-pi/locale-6.png)

![locale-7.png](notes-on-raspberry-pi/locale-7.png)

![locale-8.png](notes-on-raspberry-pi/locale-8.png)

![locale-9.png](notes-on-raspberry-pi/locale-9.png)

## 電子工作

### GPIO のピンの配置

`pinout` または `gpio readall` コマンドで確認する。

`pinout`:

![pinout.png](notes-on-raspberry-pi/pinout.png)

`gpio readall`:

```bash
pi@raspberrypi:~ $ gpio readall
 +-----+-----+---------+------+---+-Pi ZeroW-+---+------+---------+-----+-----+
 | BCM | wPi |   Name  | Mode | V | Physical | V | Mode | Name    | wPi | BCM |
 +-----+-----+---------+------+---+----++----+---+------+---------+-----+-----+
 |     |     |    3.3v |      |   |  1 || 2  |   |      | 5v      |     |     |
 |   2 |   8 |   SDA.1 |   IN | 1 |  3 || 4  |   |      | 5v      |     |     |
 |   3 |   9 |   SCL.1 |   IN | 1 |  5 || 6  |   |      | 0v      |     |     |
 |   4 |   7 | GPIO. 7 |   IN | 1 |  7 || 8  | 0 | IN   | TxD     | 15  | 14  |
 |     |     |      0v |      |   |  9 || 10 | 1 | IN   | RxD     | 16  | 15  |
 |  17 |   0 | GPIO. 0 |   IN | 0 | 11 || 12 | 0 | IN   | GPIO. 1 | 1   | 18  |
 |  27 |   2 | GPIO. 2 |   IN | 0 | 13 || 14 |   |      | 0v      |     |     |
 |  22 |   3 | GPIO. 3 |   IN | 0 | 15 || 16 | 0 | IN   | GPIO. 4 | 4   | 23  |
 |     |     |    3.3v |      |   | 17 || 18 | 0 | IN   | GPIO. 5 | 5   | 24  |
 |  10 |  12 |    MOSI |   IN | 0 | 19 || 20 |   |      | 0v      |     |     |
 |   9 |  13 |    MISO |   IN | 0 | 21 || 22 | 0 | IN   | GPIO. 6 | 6   | 25  |
 |  11 |  14 |    SCLK |   IN | 0 | 23 || 24 | 1 | IN   | CE0     | 10  | 8   |
 |     |     |      0v |      |   | 25 || 26 | 1 | IN   | CE1     | 11  | 7   |
 |   0 |  30 |   SDA.0 |   IN | 1 | 27 || 28 | 1 | IN   | SCL.0   | 31  | 1   |
 |   5 |  21 | GPIO.21 |   IN | 1 | 29 || 30 |   |      | 0v      |     |     |
 |   6 |  22 | GPIO.22 |   IN | 1 | 31 || 32 | 0 | IN   | GPIO.26 | 26  | 12  |
 |  13 |  23 | GPIO.23 |   IN | 0 | 33 || 34 |   |      | 0v      |     |     |
 |  19 |  24 | GPIO.24 |   IN | 0 | 35 || 36 | 0 | IN   | GPIO.27 | 27  | 16  |
 |  26 |  25 | GPIO.25 |   IN | 0 | 37 || 38 | 0 | IN   | GPIO.28 | 28  | 20  |
 |     |     |      0v |      |   | 39 || 40 | 0 | IN   | GPIO.29 | 29  | 21  |
 +-----+-----+---------+------+---+----++----+---+------+---------+-----+-----+
 | BCM | wPi |   Name  | Mode | V | Physical | V | Mode | Name    | wPi | BCM |
 +-----+-----+---------+------+---+-Pi ZeroW-+---+------+---------+-----+-----+
```

### コマンド ラインで GPIO を制御

`gpio` コマンドを使用する。

例:

```bash
pi@raspberrypi:~ $ gpio mode 7 out # ピン番号 7 を出力モードに設定
pi@raspberrypi:~ $ gpio write 7 1 # ピン番号 7 への 1 (High) の書き込み
pi@raspberrypi:~ $ gpio write 7 0 # ピン番号 7 への 0 (Low) の書き込み
```

`-g` オプションを使用すると、BCM の番号でピンを指定できる。

例:

```bash
pi@raspberrypi:~ $ gpio -g mode 4 out
```

`gpio` コマンドの詳細は、「[The GPIO utility | Wiring Pi][1]」を参照。

### LED を点滅させる

「[Raspberry Pi で LED を点滅させる][2]」または「[Raspberry Pi で LED を点滅させる (JavaScript)][3]」を参照。

### 電源ボタンを付ける

「[Raspberry Pi に電源ボタンを付ける][4]」を参照。

### 人感センサー

「[人感センサーで LED を点灯させる][5]」を参照。

### クリスマス ツリー

「[Raspberry Pi のクリスマス ツリー][6]」を参照。

### 7 セグメント LED

「[Raspberry Pi で 7 セグメント LED を使用する][9]」を参照。

## Tips

### VNC Viewer  で Raspberry Pi にアクセス

ホスト名 (raspberrypi.local) では Raspberry Pi にアクセスできない。

SSH  で Raspberry Pi に接続し、`hostname` または `ifconfig` コマンドで  IP アドレスを調べて、そのアドレスでアクセスする。

`hostname`:

```bash
pi@raspberrypi:~ $ hostname -I
192.168.3.24 172.17.0.1 2001:a251:4308:8a00:ba27:ebff:fe04:247a
```

`ifconfig`:

```bash
pi@raspberrypi:~ $ ifconfig
lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (ローカルループバック)
        RX packets 22  bytes 1256 (1.2 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 22  bytes 1256 (1.2 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlan0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.3.24  netmask 255.255.255.0  broadcast 192.168.3.255
        inet6 2001:a251:4308:8a00:63b0:3528:a897:70a7  prefixlen 64  scopeid 0x0<global>
        inet6 fe80::9177:bf99:d9e:c218  prefixlen 64  scopeid 0x20<link>
        ether b8:27:eb:04:24:7a  txqueuelen 1000  (イーサネット)
        RX packets 91382  bytes 38680509 (36.8 MiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 14195  bytes 3831906 (3.6 MiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

### HDMI を無効にして消費電力を抑える

```bash
pi@raspberrypi:~ $ sudo tvservice --off
```

### 画面の黒枠を削除

`raspi-config` コマンド -> 「2 Display Options」-> 「D2 Underscan」-> 「いいえ」で、黒枠を削除できる。

```bash
pi@raspberrypi:~ $ sudo raspi-config
```

![underscan-1.png](notes-on-raspberry-pi/underscan-1.png)

![underscan-2.png](notes-on-raspberry-pi/underscan-2.png)

![underscan-3.png](notes-on-raspberry-pi/underscan-3.png)

### テキスト エディタで管理者としてファイルを開く

```bash
pi@raspberrypi:~ $ sudo mousepad ファイル
```

例:

```bash
pi@raspberrypi:~ $ sudo mousepad /etc/lightdm/lightdm.conf
```

### 画面のスリープを無効に

`/etc/lightdm/lightdm.conf` の [Seat:*] セクションに以下の内容を追加する。

```ini
xserver-command=X -s 0 -p 0 -dpms
```

### 画面出力の切り替え

```bash
pi@raspberrypi:~ $ vcgencmd display_power 0 # 出力しない
pi@raspberrypi:~ $ vcgencmd display_power 1 # 出力する
```

### 解像度を 1024 x 600 に設定

`/boot/config.txt` に以下の内容を追加する。

```ini
hdmi_group=2
hdmi_mode=87
hdmi_cvt=1024 600 60 3 0 0 0
```

### GPIO ピンから電源を供給する

5V をピン番号 2 またはピン番号 4 と GND に接続する。

例:

![power-through-gpio-pins.png](notes-on-raspberry-pi/power-through-gpio-pins.png)

この例では、ブレークアウト ボードの 1 が 5V、5 が GND。

### LED の消灯

```bash
echo 0 | sudo tee /sys/class/leds/led0/brightness # ACT
echo 0 | sudo tee /sys/class/leds/led1/brightness # PWR
```

### Web カメラ

1. カメラ モジュールを有効化する (「カメラ モジュール v1 の有効化 (Bullseye)」を参照)。

2. Git をまだインストールしていない場合は、インストールする。

    ```bash
    sudo apt install git
    ```

3. [RPi-Cam-Web-Interface][10] をインストールする。

    ```bash
    git clone https://github.com/silvanmelchior/RPi_Cam_Web_Interface.git
    cd RPi_Cam_Web_Interface
    ./install.sh
    ```

4. インストールの途中でオプションが表示される。矢印キーを使用して適宜変更する。

    ![webcam-1.png](notes-on-raspberry-pi/webcam-1.png)

5. Tab キーで「OK」に移動して Enter キーを押す。

    ![webcam-2.png](notes-on-raspberry-pi/webcam-2.png)

6. インストールが完了すると、「Start now?」が表示される。「Yes」を選択して Enter キーを押す。

    ![webcam-3.png](notes-on-raspberry-pi/webcam-3.png)

7. `http://IP アドレス/html/` にアクセスする。

### ネットワーク経由で GPIO を操作

1. [WebIOPi][11] をインストールする。

    ```bash
    wget https://github.com/Freenove/WebIOPi/archive/master.zip -O WebIOPi.zip
    unzip WebIOPi.zip
    cd WebIOPi-master/WebIOPi-0.7.1
    patch -p1 -i webiopi-pi2bplus.patch
    sudo ./setup.sh
    ```

2. インストールの途中で「Do you want to access WebIOPi over Internet ? [y/n] (インターネット経由で WebIOPi にアクセスしますか？)」が表示される。ここでは、n を入力して Enter キーを押す。

3. WebIOPi を開始する。

    ```bash
    sudo webiopi -d -c /etc/webiopi/config
    ```

4. `http://IP アドレス:8000/` にアクセスする。

    デフォルトのユーザー名は `webiopi`、デフォルトのパスワードは `raspberry`。

### `raspi-gpio get` コマンドの出力を `gpio read` コマンドと同じに

```bash
pi@raspberrypi:~ $ raspi-gpio get 20 | tr " " "\n" | awk -F= '$1=="level"{print $2}'
1
```

## トラブルシューティング

### apt-get update のエラー

```bash
pi@raspberrypi:~ $ sudo apt-get update
ヒット:1 https://download.docker.com/linux/raspbian buster InRelease
取得:2 http://archive.raspberrypi.org/debian buster InRelease [32.6 kB]
取得:3 http://raspbian.raspberrypi.org/raspbian buster InRelease [15.0 kB]
パッケージリストを読み込んでいます... 完了
E: Repository 'http://archive.raspberrypi.org/debian buster InRelease' changed its 'Suite' value from 'testing' to 'oldstable'
N: This must be accepted explicitly before updates for this repository can be applied. See apt-secure(8) manpage for details.
E: Repository 'http://raspbian.raspberrypi.org/raspbian buster InRelease' changed its 'Suite' value from 'stable' to 'oldstable'
N: This must be accepted explicitly before updates for this repository can be applied. See apt-secure(8) manpage for details.
```

`sudo apt update -y` を使用する。

### VNC のレスポンスを改善 (Bullseye)

`/boot/config.txt` の `dtoverlay=vc4-kms-v3d` をコメントアウトして Raspberry Pi を再起動する。

```ini
#dtoverlay=vc4-kms-v3d
```

### VNC Viewer で Cannot currently show the desktop

![cannot-currently-show-the-desktop.png](notes-on-raspberry-pi/cannot-currently-show-the-desktop.png)

`/boot/config.txt` の `hdmi_force_hotplug=1` のコメントアウトを外して Raspberry Pi を再起動する。

```ini
hdmi_force_hotplug=1
```

### gpio: command not found

```bash
pi@raspberrypi:~ $ gpio -g read 5
-bash: gpio: command not found
```

`raspi-gpio` コマンドを使用する。

```bash
pi@raspberrypi:~ $ raspi-gpio get 5
GPIO 5: level=1 fsel=0 func=INPUT
```

`raspi-gpio` コマンドの詳細は、「[GitHub - RPi-Distro/raspi-gpio: Dump the state of the BCM270x GPIOs][12]」を参照。

 [1]: http://wiringpi.com/the-gpio-utility/
 [2]: /blinking-led-on-raspberry-pi
 [3]: /blinking-led-on-raspberry-pi-javascript
 [4]: /adding-power-button-to-raspberry-pi
 [5]: /turn-on-led-with-pir-sensor
 [6]: /christmas-tree-for-raspberry-pi
 [7]: /setup-raspberry-pi
 [8]: /backup-raspberry-pi
 [9]: /using-seven-segment-displays-on-raspberry-pi
 [10]: https://elinux.org/RPi-Cam-Web-Interface
 [11]: http://webiopi.trouch.com/
 [12]: https://github.com/RPi-Distro/raspi-gpio
 [13]: https://sourceforge.net/projects/mx-linux/files/Community_Respins/Raspberry%20Pi/
