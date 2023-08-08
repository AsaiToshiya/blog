---
title: "Nostr: 勧告前の NIPs"
date: 2023-05-12 23:15:50
updated: 2023-08-08 12:33:57
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

## NIP-24: Sealed Private Messages and Private Group Chats

https://github.com/vitorpamplona/nips/blob/sealed-dms/24.md

未署名のイベント (Gossip)、XChaCha による暗号化 (Sealed Gossip)、およびイベントのラップ (Gift Wrap) で非公開にするイベントのプライバシーを保護。

関連: [NIP-24](https://github.com/jeffthibault/nips/blob/private-messages-v2/24.md) (Private, Encrypted Direct Messages)
関連: [NIP-44](#NIP-44-Encrypted-Direct-Message-Versioned) (Encrypted Direct Message (Versioned))
関連: [NIP-59](#NIP-59-Gift-Wrap) (Gift Wrap)
関連: [NIP-76](https://github.com/d-krause/nostr-nips/blob/nip76-draft-2/76.md) (Private Channels)
関連: [NIP-103](https://github.com/threeseries/nips/blob/nip-103/103.md) (Onion Routed Direct Messages)

PR: https://github.com/nostr-protocol/nips/pull/686

## NIP-29: Simple Group Chat

https://github.com/nostr-protocol/nips/blob/simple-chat-groups/29.md

リレー主導のグループ チャット。

PR: https://github.com/nostr-protocol/nips/pull/566

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

## NIP-37: Methods for dealing with lost or compromised keys

https://github.com/nostr-protocol/nips/blob/key-invalidation-and-migration/37.md

秘密鍵の漏えいの対応。

kind:
 - `kind: 10529`: 公開鍵の削除
 - `kind: 10520`: 友人への秘密鍵の漏えいの通知
 - `kind: 1521`: 友人が推奨する新しい公開鍵

PR: https://github.com/nostr-protocol/nips/pull/637

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

## NIP-69: Zap Poll event

https://github.com/toadlyBroodle/nips/blob/master/69.md

Zap による投票。

質問のイベント (`kind: 6969`) に [NIP-57](https://github.com/nostr-protocol/nips/blob/master/57.md) (Lightning Zaps) の Zap リクエストのイベント (`kind: 9734`) で投票する。

一部のクライアントでは既に実装されている。

PR: https://github.com/nostr-protocol/nips/pull/320

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

## NIP-90: Data Vending Machine

https://github.com/nostr-protocol/nips/blob/vending-machine/90.md

「音声書き起こし」や「要約」などのジョブを実行する汎用的な仕組み。

PR: https://github.com/nostr-protocol/nips/pull/682

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

## NIP-97: Attachments

https://github.com/ondra-novak/nostr-nip-97/blob/master/97.md

バイナリー ファイル。

`attachment` タグと 2 つのメッセージ タイプ (`ATTACH` と `FETCH`) でバイナリー ファイルを扱う。

PR: https://github.com/nostr-protocol/nips/pull/694

## NIP-99: Prediction markets

https://github.com/ekzyis/nips/blob/nip-prediction-markets/99.md

予測市場 (先物市場)。

PR: https://github.com/nostr-protocol/nips/pull/517

## NIP-100: Querying Events by Tags Presence

https://github.com/fernandolguevara/nips/blob/nip100/100.md

タグの有無によるフィルター (`tags`)。

例:

`g` タグが存在するイベントに一致するフィルター。

```
{
  "tags": ["g"]
}
```

`e` タグが存在しないイベントに一致するフィルター。

```
{
  "tags": ["!e"]
}
```

PR: https://github.com/nostr-protocol/nips/pull/683

## NIP-101: Mailing lists

https://github.com/KaffinPX/nips/blob/patch-1/101.md

メーリングリスト。

`kind: 1923`。

`p` タグにメールの送信者となる個人や組織。`content` に受信者の暗号化されたメール アドレス。

メール アドレスは、ユーザーの秘密鍵と `p` タグの公開鍵で暗号化される ([NIP-04](https://github.com/nostr-protocol/nips/blob/master/04.md) (Encrypted Direct Message))。

PR: https://github.com/nostr-protocol/nips/pull/691

## NIP-104: Generative AI Prompt

https://github.com/vitorpamplona/nips/blob/generative-ai-nip/104.md

生成 AI のプロンプト。

このイベントを受け取ったクライアントが画像や動画を生成する。

PR: https://github.com/nostr-protocol/nips/pull/634

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

## NIP-199: a simple username password login

https://github.com/nostr-protocol/nips/issues/639

ユーザー名とパスワードによるログイン (秘密鍵の保管)。

秘密鍵は PBKDF2 (ユーザー名とパスワードから導出された共通鍵) と AES で暗号化されて、`kind: 30669` でリレーに保管される。

## NIP-320: Nostr Rating Mass

https://github.com/motorina0/nips/blob/nip-320/320.md

料金の支払いにより、レーティングの信頼性を保証する。

ハッシュ ツリーを使用してリーフの重み (Rating Mass) と値 (Rating Value) から実際のレーティングを計算する。

PR: https://github.com/nostr-protocol/nips/pull/604

## NIP-1078: Arbitrary custom app data

https://github.com/BlowaterNostr/nips/blob/master/1078.md

`kind: 30078` の Regular Event 版で `kind: 1078`。

CRDT (Conflict-free Replicated Data Type) でイベントの整合性を保証する。

関連: [NIP-78](https://github.com/nostr-protocol/nips/blob/master/78.md) (Arbitrary custom app data)

PR: https://github.com/nostr-protocol/nips/pull/667

## NIP-lol: Truly Private Messages

https://github.com/MaxHillebrand/nips/blob/NIPlol-private-messages/lol.md

NIP-04 (Encrypted Direct Message) の代替。

PR: https://github.com/nostr-protocol/nips/pull/564

## NIP-XXX: Order

https://github.com/civkit/nips/blob/2023-07-nip-xxx-order/XXX.md

オファー (BOLT12) のイベント。

PR: https://github.com/nostr-protocol/nips/pull/638
