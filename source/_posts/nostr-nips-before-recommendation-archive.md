---
title: "Nostr: 勧告前の NIPs (アーカイブ)"
date: 2023-08-08 13:20:42
updated: 2024-03-12 12:37:19
tags: [Nostr]
---

[Nostr: 勧告前の NIPs](/nostr-nips-before-recommendation/) のマージ、クローズされた NIP。

随時更新。

<!-- more -->

## NIP-00: Thread

クローズされた。

https://github.com/arthurfranca/nips/blob/thread/00.md

マイクロブログにおけるルート イベント (原文では Original Post) や返信、メンションなどの再定義。

この NIP のモチベーション:
 - ルート イベントと返信のイベントを別のイベントにすることで、個別に取得できるようにする
 - 特別な意味を持つ `e` タグのマーカー ([NIP-10: Conventions for clients' use of `e` and `p` tags in text events](https://github.com/nostr-protocol/nips/blob/master/10.md)) を使用しないようにする
 - ルート イベントを編集できるようにする

PR: https://github.com/nostr-protocol/nips/pull/877

## NIP-18: Private Direct Message

クローズされた。

https://github.com/Giszmo/nips/blob/PrivateDmEvent/18.md

DM の受信者 (`p` タグ) を偽る、[NIP-04](https://github.com/nostr-protocol/nips/blob/master/04.md) (Encrypted Direct Message) の改良版。

オープンな PR の中で最も古い NIP。

PR: https://github.com/nostr-protocol/nips/pull/17

## NIP-24: Extra metadata fields and tags

マージされた。

https://github.com/nostr-protocol/nips/blob/master/24.md

https://github.com/nostr-protocol/nips/blob/extra/24.md

NIP で明記されていない追加のフィールド (`kind: 0` の `display_name` など) やタグ (`r` タグなど)。

PR: https://github.com/nostr-protocol/nips/pull/794

## NIP-24: Private, Encrypted Direct Messages

クローズされた。

https://github.com/jeffthibault/nips/blob/private-messages-v2/24.md

やり取りするユーザーごとに異なる鍵ペアを使用する DM。

[NIP-43: CK-based DM](#NIP-43-CK-based-DM) に似ている。

PR: https://github.com/nostr-protocol/nips/pull/56

## NIP-24: Rich Text Note

クローズした。

https://github.com/AsaiToshiya/nips/blob/nip-24-rich-text-note/24.md

HTML や Markdown などの「リッチ テキスト メモ」。拙著。

日本語: https://github.com/AsaiToshiya/nip-24-rich-text-note/blob/main/24-ja.md

PR: https://github.com/nostr-protocol/nips/pull/619

## NIP-29: Relay-based Groups

マージされた。

https://github.com/nostr-protocol/nips/blob/master/29.md

再オープンされた。

~~クローズされた。~~

https://github.com/nostr-protocol/nips/blob/simple-chat-groups/29.md

リレー主導のグループ。

PoC: https://github.com/fiatjaf/relay29
PoC: https://github.com/fiatjaf/chat29

PR: https://github.com/nostr-protocol/nips/pull/566

## NIP-30: Custom Emoji

マージされた。

https://github.com/nostr-protocol/nips/blob/master/30.md

https://github.com/alexgleason/nips/blob/emojis/30.md

カスタム絵文字。

PR: https://github.com/nostr-protocol/nips/pull/484

## NIP-30: Resources

クローズされた。

https://github.com/plantimals/nips/blob/nip-30/30.md

リソースへのリンクを示すイベント。`kind 9`。

1 つの `resource` タグを持つ。

```
["resource", "https://anchor.fm/s/45563e80/podcast/play/56797105/https%3A%2F%2Fd3ctxlq1ktw2nl.cloudfront.net%2Fstaging%2F2022-7-29%2F2cc29ddf-c44f-b38c-ee2c-88e0e1634449.mp3", "audio/mpeg"]
```

PR: https://github.com/nostr-protocol/nips/pull/43

## NIP-32: Labeling

マージされた。

https://github.com/nostr-protocol/nips/blob/master/32.md

https://github.com/staab/nips/blob/nip-32-labeling/32.md

ラベリング。

[NIP-68](#NIP-68-Content-Labeling-including-Reviews-amp-Recommendations) も参照のこと。

PR: https://github.com/nostr-protocol/nips/pull/532

## NIP-34: `git` stuff

マージされた。

https://github.com/nostr-protocol/nips/blob/master/34.md

https://github.com/nostr-protocol/nips/blob/git/34.md

Nostr で Git のコラボレーション。

これ自体が Git リポジトリというわけではない。

CLI の実装: https://github.com/fiatjaf/gitstr

PR: https://github.com/nostr-protocol/nips/pull/997

## NIP-34: Media Attachments

クローズされた。

https://github.com/alexgleason/nips/blob/media-tag/34.md

イベントの添付ファイルを示すタグ。

```
["media", <url>, <data, optional>]
```

マイクロブログなどでは、`content` にメディア URL が記載されている必要がないため、それを代替する。

関連: [NIP-94](https://github.com/nostr-protocol/nips/blob/master/94.md) (File Metadata)
関連: [NIP-54](#NIP-54-Inline-Resource-Metadata) (Inline Resource Metadata)

PR: https://github.com/nostr-protocol/nips/pull/751

## NIP-37: Editable Short Notes

クローズされた。

https://github.com/vitorpamplona/nips/blob/editable-kind1/37.md

編集可能な `kind: 1` (Short Text Note)。

PR: https://github.com/nostr-protocol/nips/pull/1087

## NIP-37: Editable Short Notes

クローズされた。

https://github.com/vitorpamplona/nips/blob/content-editable-kind1/37.md

`content` のみ編集可能な `kind: 1` (Short Text Note)。

メタデータ (`kind: 10`) と `content` (`kind: 31010`) に分かれる。

PR: https://github.com/nostr-protocol/nips/pull/1088

## NIP-37: Editable Short Notes

クローズされた。

https://github.com/vitorpamplona/nips/blob/content-editable-kind1-2/37.md

編集可能な `kind: 1` (Short Text Note)。

`d` タグの ID に一致する `kind: 1` の `content` を置き換えて表示する。

PR: https://github.com/nostr-protocol/nips/pull/1089

## NIP-38: User Statuses

マージされた。

https://github.com/nostr-protocol/nips/blob/master/38.md

https://github.com/jb55/nips/blob/user-statuses/315.md

ユーザーの「仕事中」、「ハイキング中」や視聴中の音楽などの状態。`kind 30315`。

PR: https://github.com/nostr-protocol/nips/pull/737

## NIP-43: CK-based DM

クローズされた。

https://github.com/arthurfranca/nips/blob/dm/43.md

やり取りするユーザーごとに異なる鍵ペアを使用する DM。

ユーザーごとに DM をピンポイントで取得できるため、[NIP-17: Private Direct Messages and Group DMs](https://asaitoshiya.com/nostr-nips-before-recommendation/#NIP-17-Private-Direct-Messages-and-Group-DMs) のように、無関係なイベントを取得する必要がない。

[NIP-24: Private, Encrypted Direct Messages](#NIP-24-Private-Encrypted-Direct-Messages) に似ている。

PR: https://github.com/nostr-protocol/nips/pull/945

## NIP-43: Fast Authentication

クローズされた。

~~再オープンされた。~~

~~クローズされた。~~

https://github.com/arthurfranca/nips/blob/nip-43/43.md

[NIP-42](https://github.com/nostr-protocol/nips/blob/master/42.md) (Authentication of clients to relays) を代替する認証。

リレーに接続するときに、クエリ パラメーターの `authorization` で認証を行う。

`kind` は、[NIP-42](https://github.com/nostr-protocol/nips/blob/master/42.md) と同じ `kind: 22242` を使用する。ただし、`challenge` タグは含めない。

PR: https://github.com/nostr-protocol/nips/pull/571

## NIP-44: Encrypted Direct Message (Versioned)

[#715](https://github.com/nostr-protocol/nips/pull/715) に置き換えられた。

https://github.com/paulmillr/nips/blob/master-1/44.md

暗号化アルゴリズムをバージョン管理 (選択) できるようにする [NIP-04](https://github.com/nostr-protocol/nips/blob/master/04.md) (Encrypted Direct Message) の代替。

PR: https://github.com/nostr-protocol/nips/pull/574

## NIP-44: Encrypted Payloads (Versioned)

マージされた。

https://github.com/nostr-protocol/nips/blob/master/44.md

https://github.com/paulmillr/nips/blob/NIP-44/44.md

選択暗号文攻撃 (Chosen-ciphertext attack) に対して安全な暗号化標準。

暗号化アルゴリズムをバージョン管理 (選択) できる。

バージョン 1 では任意の秘密鍵 (ECDH) と XChaCha20 で暗号化する。

関連: https://github.com/nostr-protocol/nips/pull/574
関連: https://github.com/nostr-protocol/nips/pull/715

PR: https://github.com/nostr-protocol/nips/pull/746

## NIP-48: Nostr Wallet Connect Receiving

[NIP-47](https://github.com/nostr-protocol/nips/blob/master/47.md) (Wallet Connect) に統合され、NIP としての提案ではなくなった。

https://github.com/benthecarman/nips/blob/nwc-extensions/48.md

Nostr Wallet Connect (NWC) によるライトニング インボイスの作成 (`get_invoice`) と状態 (`invoice_status`)。

関連: [NIP-47](https://github.com/nostr-protocol/nips/blob/master/47.md)

PR: https://github.com/nostr-protocol/nips/pull/685

## NIP-48: Proxy Tags

マージされた。

https://github.com/nostr-protocol/nips/blob/master/48.md

https://github.com/alexgleason/nips/blob/proxy/48.md

ActivityPub、AT Protocol、RSS、および HTTP/HTTPS などの他のプロトコルのソースを示す `proxy` タグ。

PR: https://github.com/nostr-protocol/nips/pull/693

## NIP-49: Private Key Encryption

マージされた。

https://github.com/nostr-protocol/nips/blob/master/49.md

https://github.com/mikedilger/nips/blob/nip-nn-key-export/49.md

パスワードによる秘密鍵の暗号化と復号化。

クライアントでの秘密鍵の保存やインポート/エクスポートを安全に行えるようにする。

拙作の実装: https://github.com/AsaiToshiya/nip-49

PR: https://github.com/nostr-protocol/nips/pull/133

## NIP-52: Calendar Events

マージされた。

https://github.com/nostr-protocol/nips/blob/master/52.md

https://github.com/tyiu/nips/blob/nip52-calendar-events/52.md

カレンダーの一般的な意味での「イベント」。

kind:
 - `kind: 31922`: 日付ベースのカレンダーのイベント
 - `kind: 31923`: 時間ベースのカレンダーのイベント
 - `kind: 31924`: カレンダー (`kind: 31923` のリスト)
 - `kind: 31925`: 出欠確認

実装: https://calendar.coracle.social/

## NIP-53: Calendar Event RSVPs

[NIP-52](#NIP-52-Calendar-Events) (Calendar Events) に統合された。

https://github.com/tyiu/nips/blob/nip52-calendar-events/53.md

[NIP-52](#NIP-52-Calendar-Events) (Calendar Events) の出欠確認。

`kind: 31925`。

PR: https://github.com/nostr-protocol/nips/pull/597

## NIP-53: Live Activities

マージされた。

https://github.com/nostr-protocol/nips/blob/master/53.md

https://github.com/vitorpamplona/nips/blob/nip102-live-activities/53.md

ライブ配信の場 (`kind: 30311`) とチャット (`kind: 1311`)。

PR: https://github.com/nostr-protocol/nips/pull/498

## NIP-59: Gift Wrap

[#716](https://github.com/nostr-protocol/nips/pull/716) に置き換えられた。

https://github.com/v0l/nips/blob/59/59.md

イベントのメタデータ (DM のやり取りなど) の隠蔽。

一時的な鍵ペアを使用してイベントをラップする。

受信者には、`p` タグで通知する。

PR: https://github.com/nostr-protocol/nips/pull/468

## NIP-59: Gift Wrap

マージされた。

https://github.com/nostr-protocol/nips/blob/master/59.md

https://github.com/staab/nips/blob/NIP-59/59.md

[NIP-17](https://asaitoshiya.com/nostr-nips-before-recommendation/#NIP-17-Private-Direct-Messages-and-Group-DMs) (Private Direct Messages and Group DMs) から DM 固有のものを省略してより一般化した NIP。

内容的には NIP-17 とほぼ同じ。

`content` の暗号化には [NIP-44](https://github.com/nostr-protocol/nips/blob/master/44.md) (Encrypted Payloads (Versioned)) を使用する。

関連: https://github.com/v0l/nips/blob/59/59.md

PR: https://github.com/nostr-protocol/nips/pull/716

## NIP-68: Content Labeling (including Reviews & Recommendations)

クローズされた。

https://github.com/rabble/nips/blob/nip-69/68.md

ラベリング。

[NIP-32](#NIP-32-Labeling) も参照のこと。

PR: https://github.com/nostr-protocol/nips/pull/457

## NIP-72: Moderated Communities (Reddit Style)

マージされた。

https://github.com/nostr-protocol/nips/blob/master/72.md

https://github.com/vitorpamplona/nips/blob/moderated-communities/172.md

投稿をモデレーションできる Reddit (掲示板) のようなコミュニティー。

PR: https://github.com/nostr-protocol/nips/pull/602

## NIP-73: Location Based Communities (Meetup Style)

クローズされた。

https://github.com/BrightonBTC/nips/blob/master/73.md

Meetup のようなコミュニティー。

kind:
 - `kind: 1037`: コミュニティーの作成
 - `kind: 30037`: コミュニティーのメタデータ
 - `kind: 10037`: コミュニティーのフォロー

コミュニティーの機能:
 - イベント: [NIP-52](https://github.com/nostr-protocol/nips/blob/master/52.md) (Calendar Events)
 - メンバーシップ: [NIP-51](https://github.com/nostr-protocol/nips/blob/master/51.md) (Lists)
 - チャット: [NIP-28](https://github.com/nostr-protocol/nips/blob/master/28.md) (Public Chat)

PR: https://github.com/nostr-protocol/nips/pull/825

## NIP-75: Zap Goals

マージされた。

https://github.com/nostr-protocol/nips/blob/master/75.md

https://github.com/nostr-protocol/nips/blob/goals/75.md

クラウド ファンディングのような目標金額を示すイベント。

パラメーター化された置き換え可能なイベント (PRE) に `goal` タグを指定すると、そのイベントへの Zap も集計対象にすることができる。

PR: https://github.com/nostr-protocol/nips/pull/757

## NIP-79: `window.nostr` offline message signature & verificiation

クローズされた。

https://github.com/b35363/nips/blob/master/79.md

`window.nostr` ([NIP-07: `window.nostr` capability for web browsers](07.md)) の拡張で、文字列に対する署名と検証のためのメソッド。

```
async window.nostr.signMessage(msg : string): string
async window.nostr.verifyMessage(sig: string, pubkey : string): boolean
```

Nostr 外から使用されることを想定。

PR: https://github.com/nostr-protocol/nips/pull/730

## NIP-84: Highlights

マージされた。

https://github.com/nostr-protocol/nips/blob/master/84.md

https://github.com/pablof7z/nips/blob/highlights/84.md

コンテンツの引用とハイライト。

PR: https://github.com/nostr-protocol/nips/pull/501

## NIP-89: Recommended Application Handlers

マージされた。

https://github.com/nostr-protocol/nips/blob/master/89.md

https://github.com/pablof7z/nips/blob/application-handlers/89.md

未知の kind を処理するための推奨アプリケーション。

kind:
 - `kind: 31989`: アプリケーションを推奨するユーザーが作成するイベントの kind
 - `kind: 31990`: 推奨されたアプリケーションが作成するイベントの kind

未知の kind を受け取ったユーザーは、`kind: 31989` 経由、または直接 `kind: 31990` の REQ を投げて `kind: 31990` のイベントを取得する。

`kind: 31990` には、推奨アプリケーションのリダイレクト情報が記述されている。

PR: https://github.com/nostr-protocol/nips/pull/530

## NIP-90: Data Vending Machine

マージされた。

https://github.com/nostr-protocol/nips/blob/master/90.md

https://github.com/nostr-protocol/nips/blob/vending-machine/90.md

「音声書き起こし」や「要約」などのジョブを実行する汎用的な仕組み。

PR: https://github.com/nostr-protocol/nips/pull/682

## NIP-91: Bech32 URL Query

クローズされた。

https://github.com/tyiu/nips/blob/nip91-query-param/91.md

[NIP-21](https://github.com/nostr-protocol/nips/blob/master/21.md) (`nostr:` URI scheme) の HTTP/HTTPS スキーム版。

PR: https://github.com/nostr-protocol/nips/pull/609

## NIP-92: Media Attachments

マージされた。

https://github.com/nostr-protocol/nips/blob/master/92.md

https://github.com/coracle-social/nips/blob/imeta/29.md

メモ内の画像 (URL) のメタデータ。`imeta` タグ。

関連: https://github.com/damus-io/dips/blob/master/01.md

PR: https://github.com/nostr-protocol/nips/pull/904

## NIP-95: Relay File Storage

クローズされた。

https://github.com/arthurfranca/nips/blob/nip-95-revisit/95.md

Nostr でファイル ストレージ。

base64 でエンコードされたファイルを持つイベントと、そのイベントを示す [NIP-19](https://github.com/nostr-protocol/nips/blob/master/19.md) (bech32-encoded entities) の `nfile`。

ファイルは `c` タグでチャンク化できる。

関連: https://github.com/nostr-protocol/nips/pull/345

PR: https://github.com/nostr-protocol/nips/pull/1145

## NIP-96: HTTP File Storage Integration

マージされた。

https://github.com/nostr-protocol/nips/blob/master/96.md

https://github.com/arthurfranca/nips/blob/nip-95-contender/96.md

Nostr で使用するファイル サーバー。

通常の NIP と違って、HTTP REST API によるファイルのアップロードと、HTTP メソッドによるファイルのダウンロード、および削除のための仕様。

PR: https://github.com/nostr-protocol/nips/pull/547

## NIP-97: Attachments

[#719](https://github.com/nostr-protocol/nips/pull/719) に置き換えられた。

https://github.com/ondra-novak/nostr-nip-97/blob/master/97.md

バイナリー ファイル。

`attachment` タグと 2 つのメッセージ タイプ (`ATTACH` と `FETCH`) でバイナリー ファイルを扱う。

PR: https://github.com/nostr-protocol/nips/pull/694

## NIP-98: HTTP Auth

マージされた。

https://github.com/nostr-protocol/nips/blob/master/98.md

https://github.com/v0l/nips/blob/nip98/98.md

Nostr のイベントで HTTP 認証。

エンドポイントを含む `kind: 27235` のイベントを base64 エンコードして、HTTP Authorization ヘッダーに乗せてリクエストする。

リファレンス実装: [NostrAuth.cs](https://gist.github.com/v0l/74346ae530896115bfe2504c8cd018d3) (C#、ASP.NET による認証ハンドラー)

PR: https://github.com/nostr-protocol/nips/pull/469

## NIP-99: Classified Listings

マージされた。

https://github.com/nostr-protocol/nips/blob/master/99.md

https://github.com/erskingardner/nips/blob/new-event-for-classifieds/99.md

「ジモティー」や「じゃマール」のようなクラシファイドと呼ばれる、商品、サービス、求人、およびレンタルなどのカテゴリーに分類された広告。

より厳密な [NIP-15](https://github.com/nostr-protocol/nips/blob/master/15.md) (Nostr Marketplace (for resilient marketplaces)) とは異なる。

実装: https://ostrich.work/

PR: https://github.com/nostr-protocol/nips/pull/662

## NIP-99: Prediction markets

クローズされた。

https://github.com/ekzyis/nips/blob/nip-prediction-markets/99.md

予測市場 (先物市場)。

PR: https://github.com/nostr-protocol/nips/pull/517

## NIP-99: Social Note

クローズされた。

https://github.com/arthurfranca/nips/blob/social-notes/99.md

編集可能な `kind: 1` (テキスト メモ)。

`kind: 31111`。

関連: https://github.com/nostr-protocol/nips/issues/646

PR: https://github.com/nostr-protocol/nips/pull/659

## NIP-100: Default Relay Port Standard

クローズされた。

https://github.com/nostr-protocol/nips/pull/852/files

リレーのデフォルトのポート。`444`

PR: https://github.com/nostr-protocol/nips/pull/852

## NIP-101: Enhancing Event Compression and Encoding Support

クローズされた。

https://github.com/b35363/nips/blob/master/101.md

メッセージのペイロードの圧縮 (エンコード)。

例:

```
["EVENT", <エンコードされたペイロード>, <エンコード方式>]
```

クライアントとリレーでサポートされるエンコード方式は、`CAP` メッセージで相互にやりとりする。

例 (クライアントからリレー):

```
["CAP", {"supportedEncodings": ["base64", "gzip64", "plaintext"]}]
```

例 (リレーからクライアント):

```
["CAP", {"selectedEncoding": "gzip64"}]
```

PR: https://github.com/nostr-protocol/nips/pull/730

## NIP-101: Standard HTTP REST API for Relays

クローズされた。

https://github.com/jacany/nips/blob/101/101.md

リレーが提供する REST API。

PR: https://github.com/nostr-protocol/nips/pull/680

## NIP-102: Private Event

クローズされた。

https://github.com/arthurfranca/nips/blob/private/102.md

NIP-43 (https://github.com/arthurfranca/nips/blob/private/43.md) と `PRIVATE_EVENT` メッセージでイベントの読み取りを制限。

PR: https://github.com/nostr-protocol/nips/pull/739

## NIP-lol: Truly Private Messages

[ディスカッション](https://github.com/nostr-protocol/nips/discussions/658)に移動された。

https://github.com/MaxHillebrand/nips/blob/NIPlol-private-messages/lol.md

NIP-04 (Encrypted Direct Message) の代替。

PR: https://github.com/nostr-protocol/nips/pull/564

## NIP-XX: Addendums

クローズされた。

https://github.com/nostr-protocol/nips/issues/903

他のイベントを補足するためのイベント。

`kind: 1040` (OpenTimestamps) に近いイメージ。

## NIP-xx: Indexes

クローズされた。

https://github.com/coracle-social/nips/blob/indexes/xx.md (削除済み)

関連するイベントのインデックスを表す `~` (チルダ) タグ。

インデックスのソースは、リレー、[NIP-05](https://github.com/nostr-protocol/nips/blob/master/05.md)、または GUN。

例:

- `["~", "wss://relay.example.com", "relay"]`
- `["~", "user@example.com", "nip05"]`
- `["~", "b0635d6a9851d3aed0cd6c495b282167acf761729078d975fc341b22650b07b9", "gundb"]`

参考: [GUN](https://gun.eco/)

PR: https://github.com/nostr-protocol/nips/pull/1130
