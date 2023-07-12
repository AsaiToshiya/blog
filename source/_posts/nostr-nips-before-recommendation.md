---
title: "Nostr: 勧告前の NIPs"
date: 2023-05-12 23:15:50
updated: 2023-07-09 21:14:58
tags: [Nostr]
---

![image.jpg](nostr-nips-before-recommendation/image.jpg)

Nostr の勧告前の NIPs (Nostr Implementation Possibilities)。

多数の提案がある中で、自分がある程度理解している NIP に限り記載する。

随時更新。

<!-- more -->

## NIP-17: Event Metadata

https://github.com/arthurfranca/nips/blob/nip-17/17.md

リレーのレスポンス (イベント) に追加されるメタデータ。

PR: https://github.com/nostr-protocol/nips/pull/605

## NIP-17: Tracking Git Commits with Nostr

https://github.com/nip17/nips/blob/master/17.md

Nostr で Git コミットを追跡できるようにする。

この NIP ができるようにするユースケース:
 - GitHub Actions
 - 継続的インテグレーション/継続的デプロイメント (CI/CD)
 - Travis CI

PR: https://github.com/nostr-protocol/nips/pull/324

## NIP-18: Private Direct Message

https://github.com/Giszmo/nips/blob/PrivateDmEvent/18.md

DM の受信者 (`p` タグ) を偽る、[NIP-04](https://github.com/nostr-protocol/nips/blob/master/04.md) (Encrypted Direct Message) の改良版。

オープンな PR の中で最も古い NIP。

PR: https://github.com/nostr-protocol/nips/pull/17

## NIP-24: Rich Text Note

https://github.com/AsaiToshiya/nips/blob/nip-24-rich-text-note/24.md

HTML や Markdown などの「リッチ テキスト メモ」。拙著。

日本語: https://github.com/AsaiToshiya/nip-24-rich-text-note/blob/main/24-ja.md

PR: https://github.com/nostr-protocol/nips/pull/619

## NIP-29: Simple Group Chat

https://github.com/nostr-protocol/nips/blob/simple-chat-groups/29.md

リレー主導のグループ チャット。

PR: https://github.com/nostr-protocol/nips/pull/566

## ~~NIP-30: Custom Emoji~~

マージされた。

https://github.com/nostr-protocol/nips/blob/master/30.md

~~https://github.com/alexgleason/nips/blob/emojis/30.md~~

~~カスタム絵文字。~~

~~PR: https://github.com/nostr-protocol/nips/pull/484~~

## ~~NIP-32: Labeling~~

マージされた。

https://github.com/nostr-protocol/nips/blob/master/32.md

~~https://github.com/staab/nips/blob/nip-32-labeling/32.md~~

~~ラベリング。~~

~~[NIP-68](#NIP-68-Content-Labeling-including-Reviews-amp-Recommendations) も参照のこと。~~

~~PR: https://github.com/nostr-protocol/nips/pull/532~~

## NIP-34: Algorithmic Filter

https://github.com/arthurfranca/nips/blob/nip-34/34.md

フィルターに `limit` が指定されている場合のイベントの並び順。

`["REQ", <subscription_id>, { ..., limit: 5, nip34: "asc" }]` のように指定する。

PR: https://github.com/nostr-protocol/nips/pull/579

## NIP-35: Member List

https://github.com/arthurfranca/nips/blob/nip-35/35.md

グループ、チャンネル、コミュニティーなどに属するユーザーの「連絡可能」、「退席中」などの状態。

PR: https://github.com/nostr-protocol/nips/pull/607

## NIP-37: Language Tag

https://github.com/alexgleason/nips/blob/lang/37.md

イベントの言語を示すタグ。

PR: https://github.com/nostr-protocol/nips/pull/632

## NIP-43: Fast Authentication

再オープンされた。

~~クローズされた。~~

https://github.com/arthurfranca/nips/blob/nip-43/43.md

[NIP-42](https://github.com/nostr-protocol/nips/blob/master/42.md) (Authentication of clients to relays) を代替する認証。

リレーに接続するときに、クエリ パラメーターの `authorization` で認証を行う。

`kind` は、[NIP-42](https://github.com/nostr-protocol/nips/blob/master/42.md) と同じ `kind: 22242` を使用する。ただし、`challenge` タグは含めない。

PR: https://github.com/nostr-protocol/nips/pull/571

## NIP-44: Encrypted Direct Message (Versioned)

https://github.com/paulmillr/nips/blob/master-1/44.md

暗号化アルゴリズムをバージョン管理 (選択) できるようにする [NIP-04](https://github.com/nostr-protocol/nips/blob/master/04.md) (Encrypted Direct Message) の代替。

PR: https://github.com/nostr-protocol/nips/pull/574

## NIP-52: Calendar Events

https://github.com/tyiu/nips/blob/nip52-calendar-events/52.md

カレンダーの一般的な意味での「イベント」。

kind:
 - `kind: 31923`: カレンダーのイベント
 - `kind: 31924`: カレンダー (`kind: 31923` のリスト)
 - `kind: 31925`: 出欠確認

## ~~NIP-53: Calendar Event RSVPs~~

[NIP-52](#NIP-52-Calendar-Events) (Calendar Events) に統合された。

~~https://github.com/tyiu/nips/blob/nip52-calendar-events/53.md~~

~~[NIP-52](#NIP-52-Calendar-Events) (Calendar Events) の出欠確認。~~

~~`kind: 31925`。~~

~~PR: https://github.com/nostr-protocol/nips/pull/597~~

## ~~NIP-53: Live Activities~~

マージされた。

https://github.com/nostr-protocol/nips/blob/master/53.md

~~https://github.com/vitorpamplona/nips/blob/nip102-live-activities/53.md~~

~~ライブ配信の場 (`kind: 30311`) とチャット (`kind: 1311`)。~~

~~PR: https://github.com/nostr-protocol/nips/pull/498~~

## NIP-54: Inline Resource Metadata

https://github.com/arthurfranca/nips/blob/inline-resource-metadata/54.md

URL や [NIP-21](https://github.com/nostr-protocol/nips/blob/master/21.md) の末尾に追加される `#t=24&a%20name=a%20value` のようなパラメーター。

[DIP-01](https://github.com/damus-io/dips/blob/master/01.md) も参照のこと。

PR: https://github.com/nostr-protocol/nips/pull/521

## NIP-59: Gift Wrap

https://github.com/v0l/nips/blob/59/59.md

イベントのメタデータ (DM のやり取りなど) の隠蔽。

一時的な鍵ペアを使用してイベントをラップする。

受信者には、`p` タグで通知する。

PR: https://github.com/nostr-protocol/nips/pull/468

## NIP-60: Zap Gates

https://github.com/Egge7/nips/blob/zapGates/60.md

[NIP-98](#NIP-98-HTTP-Auth) (HTTP Auth) のリソースに [NIP-57](https://github.com/nostr-protocol/nips/blob/master/57.md) (Lightning Zaps) でアクセスできるようにする。

PR: https://github.com/nostr-protocol/nips/pull/542

## ~~NIP-68: Content Labeling (including Reviews & Recommendations)~~

クローズされた。

~~https://github.com/rabble/nips/blob/nip-69/68.md~~

~~ラベリング。~~

~~[NIP-32](#NIP-32-Labeling) も参照のこと。~~

~~PR: https://github.com/nostr-protocol/nips/pull/457~~

## NIP-77: Nostr Data Sharing URI Scheme

https://github.com/mandelmonkey/nips/blob/master/77.md

Nostr クライアントにテキストや画像を共有するための URI スキーマ (`nostr-share://`)。

リファレンス実装:
https://github.com/mandelmonkey/nostr-share-sample-game
https://github.com/mandelmonkey/nostr-share-wallet-demo

PR: https://github.com/nostr-protocol/nips/pull/491

## NIP-84: Highlights

https://github.com/pablof7z/nips/blob/highlights/84.md

コンテンツの引用とハイライト。

PR: https://github.com/nostr-protocol/nips/pull/501

## NIP-88: Nostr Cash (simple Nostr cash/token/cheque)

https://github.com/arcbtc/nips/blob/nostrcash/88.md

Nostr ネイティブなウォレットとミント (造幣局)。

クライアントはウォレットの役目を負い、リレーはミントの役目を負う。

PR: https://github.com/nostr-protocol/nips/pull/627

## ~~NIP-89: Recommended Application Handlers~~

マージされた。

https://github.com/nostr-protocol/nips/blob/master/89.md

~~https://github.com/pablof7z/nips/blob/application-handlers/89.md~~

~~未知の kind を処理するための推奨アプリケーション。~~

~~kind:~~
 - ~~`kind: 31989`: アプリケーションを推奨するユーザーが作成するイベントの kind~~
 - ~~`kind: 31990`: 推奨されたアプリケーションが作成するイベントの kind~~

~~未知の kind を受け取ったユーザーは、`kind: 31989` 経由、または直接 `kind: 31990` の REQ を投げて `kind: 31990` のイベントを取得する。~~

~~`kind: 31990` には、推奨アプリケーションのリダイレクト情報が記述されている。~~

~~PR: https://github.com/nostr-protocol/nips/pull/530~~

## NIP-91: Bech32 URL Query

https://github.com/tyiu/nips/blob/nip91-query-param/91.md

[NIP-21](https://github.com/nostr-protocol/nips/blob/master/21.md) (`nostr:` URI scheme) の HTTP/HTTPS スキーム版。

PR: https://github.com/nostr-protocol/nips/pull/609

## NIP-93: NSON

https://github.com/nostr-protocol/nips/blob/nip93-nson/93.md

JSON のデコードを高速化するための `nson` フィールド。

NSON は造語？

PR: https://github.com/nostr-protocol/nips/pull/515

## NIP-95: Storage and Shared File

https://github.com/frbitten/nostr-nips/blob/NIP-95/95.md

Nostr でファイル ストレージ。

PR: https://github.com/nostr-protocol/nips/pull/345

## NIP-96: Code Collaboration over Nostr

https://github.com/fostr-dev/nips/blob/master/96.md

Nostr 上で GitHub のようなコラボレーションを実現する。

PR: https://github.com/nostr-protocol/nips/pull/618

## NIP-96: HTTP File Storage Integration

https://github.com/arthurfranca/nips/blob/nip-95-contender/96.md

Nostr で使用するファイル サーバー。

通常の NIP と違って、HTTP REST API によるファイルのアップロードと、HTTP メソッドによるファイルのダウンロード、および削除のための仕様。

PR: https://github.com/nostr-protocol/nips/pull/547

## ~~NIP-98: HTTP Auth~~

マージされた。

https://github.com/nostr-protocol/nips/blob/master/98.md

~~https://github.com/v0l/nips/blob/nip98/98.md~~

~~Nostr のイベントで HTTP 認証。~~

~~エンドポイントを含む `kind: 27235` のイベントを base64 エンコードして、HTTP Authorization ヘッダーに乗せてリクエストする。~~

~~リファレンス実装: [NostrAuth.cs](https://gist.github.com/v0l/74346ae530896115bfe2504c8cd018d3) (C#、ASP.NET による認証ハンドラー)~~

~~PR: https://github.com/nostr-protocol/nips/pull/469~~

## NIP-99: Prediction markets

https://github.com/ekzyis/nips/blob/nip-prediction-markets/99.md

予測市場 (先物市場)。

PR: https://github.com/nostr-protocol/nips/pull/517

## NIP-109: Pubkey Deletion

https://github.com/alexgleason/nips/blob/delete-pubkey/109.md

公開鍵の削除。

PR: https://github.com/nostr-protocol/nips/pull/377

## NIP-112: Encrypted Group Events

https://github.com/earonesty/nips/blob/112/112.md

[NIP-44](#NIP-44-Encrypted-Direct-Message-Versioned) (Encrypted Direct Message (Versioned)) と [NIP-59](#NIP-59-Gift-Wrap) (Gift Wrap) を使用するプライベート グループ チャット。

PR: https://github.com/nostr-protocol/nips/pull/580

## NIP-172: Moderated Communities (Reddit Style)

https://github.com/vitorpamplona/nips/blob/moderated-communities/172.md

投稿をモデレーションできる Reddit (掲示板) のようなコミュニティー。

PR: https://github.com/nostr-protocol/nips/pull/602

## NIP-320: Nostr Rating Mass

https://github.com/motorina0/nips/blob/nip-320/320.md

料金の支払いにより、レーティングの信頼性を保証する。

ハッシュ ツリーを使用してリーフの重み (Rating Mass) と値 (Rating Value) から実際のレーティングを計算する。

PR: https://github.com/nostr-protocol/nips/pull/604

## NIP-lol: Truly Private Messages

https://github.com/MaxHillebrand/nips/blob/NIPlol-private-messages/lol.md

NIP-04 (Encrypted Direct Message) の代替。

PR: https://github.com/nostr-protocol/nips/pull/564
