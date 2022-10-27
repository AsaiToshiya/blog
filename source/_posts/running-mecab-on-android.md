---
title: MeCab を Android で動かす
date: 2020-11-12 22:55:31
updated: 2020-11-13 12:24:33
---
<p></p>

<!-- more -->
## 手順

### 1. Termux をインストール

https://play.google.com/store/apps/details?id=com.termux

### 2. wget をインストール

```bash
$ pkg install wget
```

### 3. $PREFIX に移動

```bash
$ cd $PREFIX
```

### 4. MeCab をインストール

```bash
$ wget "https://drive.google.com/uc?export=download&id=0B4y35FiV1wh7cENtOXlicTFaRUE" -O mecab-0.996.tar.gz
$ tar zxfv mecab-0.996.tar.gz
$ cd mecab-0.996
$ ./configure --prefix=$PREFIX/local
$ make
$ make check
$ make install
$ cd ../
$ rm -rf mecab-0.996.tar.gz mecab-0.996
```

`configure` で以下のエラーが発生する場合がある。

```bash
$ ./configure --prefix=$PREFIX/local
checking build system type... ./config.guess: unable to guess system type

This script, last modified 2011-05-11, has failed to recognize
the operating system you are using. It is advised that you
download the most up to date version of the config scripts from

  http://git.savannah.gnu.org/gitweb/?p=config.git;a=blob_plain;f=config.guess;hb=HEAD
and
  http://git.savannah.gnu.org/gitweb/?p=config.git;a=blob_plain;f=config.sub;hb=HEAD

If the version you run (./config.guess) is already up to date, please
send the following data and any information you think might be
pertinent to <config-patches@gnu.org> in order to provide the needed
information to handle your system.

config.guess timestamp = 2011-05-11

uname -m = aarch64
uname -r = 4.9.112-perf+
uname -s = Linux
uname -v = #2 SMP PREEMPT Wed Aug 5 19:47:11 CST 2020

/usr/bin/uname -p = unknown
/bin/uname -X     =

hostinfo               =
/bin/universe          =
/usr/bin/arch -k       =
/bin/arch              =
/usr/bin/oslevel       =
/usr/convex/getsysinfo =

UNAME_MACHINE = aarch64
UNAME_RELEASE = 4.9.112-perf+
UNAME_SYSTEM  = Linux
UNAME_VERSION = #2 SMP PREEMPT Wed Aug 5 19:47:11 CST 2020
configure: error: cannot guess build type; you must specify one
```

この場合は、`--build` オプションを付けて実行する。

```bash
$ ./configure --prefix=$PREFIX/local --build=aarch64-unknown-linux-gnu
```

### 5. MeCab のパスを通す

```bash
$ echo 'export PATH=$PREFIX/local/bin:$PATH' >> ~/.bash_profile
$ source ~/.bash_profile
```

### 6. インストールを確認

```bash
$ mecab --version
mecab of 0.996
```

### 7. 辞書をインストール

```bash
$ wget "https://drive.google.com/uc?export=download&id=0B4y35FiV1wh7MWVlSDBCSXZMTXM" -O mecab-ipadic-2.7.0-20070801.tar.gz
$ tar zxfv mecab-ipadic-2.7.0-20070801.tar.gz
$ cd mecab-ipadic-2.7.0-20070801
$ ./configure --prefix=$PREFIX/local --with-charset=utf8
$ make
$ make install
$ cd ../
$ rm -rf mecab-ipadic-2.7.0-20070801.tar.gz mecab-ipadic-2.7.0-20070801
```

### 8. MeCab を実行

```bash
$ mecab
すもももももももものうち
すもも  名詞,一般,*,*,*,*,すもも,スモモ,スモモ
も      助詞,係助詞,*,*,*,*,も,モ,モ
もも    名詞,一般,*,*,*,*,もも,モモ,モモ
も      助詞,係助詞,*,*,*,*,も,モ,モ
もも    名詞,一般,*,*,*,*,もも,モモ,モモ
の      助詞,連体化,*,*,*,*,の,ノ,ノ
うち    名詞,非自立,副詞可能,*,*,*,うち,ウチ,ウチ
EOS

```

### 9. [mecab-ipadic-NEologd][2] をインストール

新語を収録した辞書の [mecab-ipadic-NEologd][2] をインストールする。

```bash
$ git clone https://github.com/neologd/mecab-ipadic-neologd.git
$ cd mecab-ipadic-neologd
$ ./bin/install-mecab-ipadic-neologd -y
$ cd ../
$ rm -rf mecab-ipadic-neologd
```

`install-mecab-ipadic-neologd` で以下のようなエラーが発生した場合は、`pkg install` コマンドで不足しているライブラリーをインストールする。

```bash
$ ./bin/install-mecab-ipadic-neologd -y
[install-mecab-ipadic-NEologd] :     iconv is not found.
```

### 10. mecab-ipadic-NEologd を使用して MeCab を実行

```bash
$ mecab -d /data/data/com.termux/files/usr/local/lib/mecab/dic/mecab-ipadic-neologd
8月3日に放送された「中居正広の金曜日のスマイルたちへ」(TBS系)で、1日たった5分でぽっこりおなかを解消するというダイエット方法を紹介。キンタロー。のダイエットにも密着。
8月3日  名詞,固有名詞,一般,*,*,*,8月3日,ハチガツミッカ,ハチガツミッカ
に      助詞,格助詞,一般,*,*,*,に,ニ,ニ
放送    名詞,サ変接続,*,*,*,*,放送,ホウソウ,ホーソー
さ      動詞,自立,*,*,サ変・スル,未然レル接続,する,サ,サ
れ      動詞,接尾,*,*,一段,連用形,れる,レ,レ
た      助動詞,*,*,*,特殊・タ,基本形,た,タ,タ
「      記号,括弧開,*,*,*,*,「,「,「
中居正広の金曜日のスマイルたちへ        名詞,固有名詞,一般,*,*,*,中居正広の金曜日のスマイルたちへ,ナカイマサヒロノキンヨウビノスマイルタチヘ,ナカイマサヒロノキンヨービノスマイルタチヘ
」(     記号,一般,*,*,*,*,*
TBS     名詞,固有名詞,一般,*,*,*,TBS,ティービーエス,ティー ビーエス
系      名詞,接尾,一般,*,*,*,系,ケイ,ケイ
)       記号,一般,*,*,*,*,*
で      助動詞,*,*,*,特殊・ダ,連用形,だ,デ,デ
、      記号,読点,*,*,*,*,、,、,、
1日     名詞,固有名詞,一般,*,*,*,1日,ツイタチ,ツイタチ
たった  副詞,助詞類接続,*,*,*,*,たった,タッタ,タッタ
5分     名詞,固有名詞,一般,*,*,*,5分,ゴフン,ゴフン
で      助詞,格助詞,一般,*,*,*,で,デ,デ
ぽっこりおなか  名詞,固有名詞,一般,*,*,*,ぽっこりおなか,ポ ッコリオナカ,ポッコリオナカ
を      助詞,格助詞,一般,*,*,*,を,ヲ,ヲ
解消    名詞,サ変接続,*,*,*,*,解消,カイショウ,カイショー
する    動詞,自立,*,*,サ変・スル,基本形,する,スル,スル
という  助詞,格助詞,連語,*,*,*,という,トイウ,トユウ
ダイエット方法  名詞,固有名詞,一般,*,*,*,ダイエット方法,ダ イエットホウホウ,ダイエットホウホー
を      助詞,格助詞,一般,*,*,*,を,ヲ,ヲ
紹介    名詞,サ変接続,*,*,*,*,紹介,ショウカイ,ショーカイ
。      記号,句点,*,*,*,*,。,。,。
キンタロー。    名詞,固有名詞,一般,*,*,*,キンタロー。,キン タロー,キンタロー
の      助詞,連体化,*,*,*,*,の,ノ,ノ
ダイエット      名詞,サ変接続,*,*,*,*,ダイエット,ダイエット,ダイエット
に      助詞,格助詞,一般,*,*,*,に,ニ,ニ
も      助詞,係助詞,*,*,*,*,も,モ,モ
密着    名詞,サ変接続,*,*,*,*,密着,ミッチャク,ミッチャク
。      記号,句点,*,*,*,*,。,。,。
EOS

```


 [1]: https://taku910.github.io/mecab/
 [2]: https://github.com/neologd/mecab-ipadic-neologd