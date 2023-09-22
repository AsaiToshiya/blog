---
title: "Nostr: 勧告前の NIPs"
date: 2023-05-12 23:15:50
updated: 2023-09-21 23:13:04
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

## NIP-24: Private Direct Messages and Small Group Chats

https://github.com/vitorpamplona/nips/blob/sealed-dms/24.md

未署名のイベント (Rumor、`kind: 14`)、Rumor のラップ (Seal、`kind: 13`)、および Seal のラップ (Gift Wrap、`kind: 1059`) で DM のプライバシーを保護。

`content` の暗号化には XChaCha を使用する。

各イベントの目的:
 - Rumor: ブロードキャストを防ぐ
 - Seal: 署名
 - Gift Wrap: メタデータ (送信者) の漏えいを防ぐ

各イベントの例え:
 - Rumor: 署名されていない手紙
 - Seal: 署名だけされた中封筒
 - Gift Wrap: 宛先だけが書かれた差出人不明の封筒

関連: [NIP-24](https://github.com/jeffthibault/nips/blob/private-messages-v2/24.md) (Private, Encrypted Direct Messages)
関連: [NIP-44](#NIP-44-Encrypted-Payloads-Versioned) (Encrypted Payloads (Versioned))
関連: [NIP-59](https://github.com/v0l/nips/blob/59/59.md) (Gift Wrap)
関連: [NIP-76](https://github.com/d-krause/nostr-nips/blob/nip76-draft-2/76.md) (Private Channels)
関連: [NIP-103](https://github.com/threeseries/nips/blob/nip-103/103.md) (Onion Routed Direct Messages)

PR: https://github.com/nostr-protocol/nips/pull/686

## NIP-34: Algorithmic Filter

https://github.com/arthurfranca/nips/blob/nip-34/34.md

フィルターに `limit` が指定されている場合のイベントの並び順。

`["REQ", <subscription_id>, { ..., limit: 5, nip34: "asc" }]` のように指定する。

PR: https://github.com/nostr-protocol/nips/pull/579

## NIP-34: Media Attachments

https://github.com/alexgleason/nips/blob/media-tag/34.md

イベントの添付ファイルを示すタグ。

```
["media", <url>, <data, optional>]
```

マイクロブログなどでは、`content` にメディア URL が記載されている必要がないため、それを代替する。

関連: [NIP-94](https://github.com/nostr-protocol/nips/blob/master/94.md) (File Metadata)
関連: [NIP-54](#NIP-54-Inline-Resource-Metadata) (Inline Resource Metadata)

PR: https://github.com/nostr-protocol/nips/pull/751

## NIP-34: Wiki

https://github.com/nostr-protocol/nips/blob/wiki/34.md

Nostr で Wiki。

イベントの内容は NIP-23 (Long-form Content) とほぼ同じだが、ユースケースが異なる。

PR: https://github.com/nostr-protocol/nips/pull/787

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

## NIP-44: Encrypted Payloads (Versioned)

https://github.com/paulmillr/nips/blob/NIP-44/44.md

選択暗号文攻撃 (Chosen-ciphertext attack) に対して安全な暗号化標準。

暗号化アルゴリズムをバージョン管理 (選択) できる。

バージョン 1 では任意の秘密鍵 (ECDH) と XChaCha20 で暗号化する。

関連: https://github.com/nostr-protocol/nips/pull/574
関連: https://github.com/nostr-protocol/nips/pull/715

PR: https://github.com/nostr-protocol/nips/pull/746

## NIP-54: Inline Resource Metadata

https://github.com/arthurfranca/nips/blob/inline-resource-metadata/54.md

`content` 内のインライン リソースの読み込みを強化するために、URL や [NIP-21](https://github.com/nostr-protocol/nips/blob/master/21.md) の末尾に追加される `#t=24&a%20name=a%20value` のようなパラメーター。

[DIP-01](https://github.com/damus-io/dips/blob/master/01.md) も参照のこと。

PR: https://github.com/nostr-protocol/nips/pull/521

## NIP-59: Gift Wrap

https://github.com/staab/nips/blob/NIP-59/59.md

[NIP-24](#NIP-24-Private-Direct-Messages-and-Small-Group-Chats) (Private Direct Messages and Small Group Chats) から DM 固有のものを省略してより一般化した NIP。

内容的には NIP-24 とほぼ同じ。

`content` の暗号化には [NIP-44](#NIP-44-Encrypted-Payloads-Versioned) (Encrypted Payloads (Versioned)) を使用する。

関連: https://github.com/v0l/nips/blob/59/59.md

PR: https://github.com/nostr-protocol/nips/pull/716

## NIP-60: Zap Gates

https://github.com/Egge7/nips/blob/zapGates/60.md

[NIP-98](#NIP-98-HTTP-Auth) (HTTP Auth) のリソースに [NIP-57](https://github.com/nostr-protocol/nips/blob/master/57.md) (Lightning Zaps) でアクセスできるようにする。

PR: https://github.com/nostr-protocol/nips/pull/542

## NIP-61: Unbounded lists

https://github.com/arthurfranca/nips/blob/bunch-of-events/61.md

リレーのイベントのサイズの制限を回避することができるリスト。

pubkey および `n` タグでリストを定義して、`u` タグまたは `nunb` でリストを参照する。

PR: https://github.com/nostr-protocol/nips/pull/784

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

## NIP-76: Key Change

https://github.com/arthurfranca/nips/blob/key-change/76.md

バックアップの鍵ペアを設定するためのイベント (`kind: 1076`) と鍵を交換するためのイベント (`kind: 1077`)。

関連: https://github.com/nostr-protocol/nips/pull/539
関連: [NIP-77: Trust Clock](#NIP-77-Trust-Clock)

PR: https://github.com/nostr-protocol/nips/pull/782

## NIP-77: Trust Clock

https://github.com/arthurfranca/nips/blob/trust-clock/77.md

ブロックチェーンの代わりに複数のリレーを使用する [NIP-03](https://github.com/nostr-protocol/nips/blob/master/03.md) (OpenTimestamps Attestations for Events) の代替。

https://github.com/arthurfranca/nips/blob/trust-clock/77.md?plain=1#L44-L45
> The response is a JSON `{ sig: "<signature>", pubkey: "<relay1pubkey>" }`.
> The signature uses the same Schnorr setup from NIP-01 to sign the received event `id`.

`event.id` に対する署名？

PR: https://github.com/nostr-protocol/nips/pull/781

## NIP-79: Digital Contracts

https://github.com/xemuj/nips/blob/DigitalContracts/79.md
~~https://github.com/nostr-protocol/nips/discussions/752~~

電子契約・電子署名。

PR: https://github.com/nostr-protocol/nips/pull/755

## NIP-79: `window.nostr` offline message signature & verificiation

https://github.com/b35363/nips/blob/master/79.md

`window.nostr` ([NIP-07: `window.nostr` capability for web browsers](07.md)) の拡張で、文字列に対する署名と検証のためのメソッド。

```
async window.nostr.signMessage(msg : string): string
async window.nostr.verifyMessage(sig: string, pubkey : string): boolean
```

Nostr 外から使用されることを想定。

PR: https://github.com/nostr-protocol/nips/pull/730

## NIP-81: Relationship Status

https://github.com/vitorpamplona/nips/blob/relationship-status/81.md

フォローしているユーザーとの関係性。

パラメーター化された置き換え可能なイベント (PRE) で、各フォローに対して 1 つのイベント。

参考: https://github.com/nostr-protocol/nips/pull/349#issuecomment-1472395508

PR: https://github.com/nostr-protocol/nips/pull/761

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

## NIP-97: Files hosted on relay

https://github.com/ondra-novak/nostr-nip-97/blob/version-2/97.md

バイナリー ファイル。

`kind: 1063` (NIP-94: File Metadata) を拡張したイベントと 2 つのメッセージ タイプ (`FILE` と `RETRIEVE`) でバイナリー ファイルを扱う。

関連: https://github.com/nostr-protocol/nips/pull/694

PR: https://github.com/nostr-protocol/nips/pull/719

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

## NIP-101: Enhancing Event Compression and Encoding Support

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

## NIP-101: Mailing lists

https://github.com/KaffinPX/nips/blob/patch-1/101.md

メーリングリスト。

`kind: 1923`。

`p` タグにメールの送信者となる個人や組織。`content` に受信者の暗号化されたメール アドレス。

メール アドレスは、ユーザーの秘密鍵と `p` タグの公開鍵で暗号化される ([NIP-04](https://github.com/nostr-protocol/nips/blob/master/04.md) (Encrypted Direct Message))。

PR: https://github.com/nostr-protocol/nips/pull/691

## NIP-102: Private Event

https://github.com/arthurfranca/nips/blob/private/102.md

NIP-43 (https://github.com/arthurfranca/nips/blob/private/43.md) と `PRIVATE_EVENT` メッセージでイベントの読み取りを制限。

PR: https://github.com/nostr-protocol/nips/pull/739

## NIP-104: Generative AI Prompt

https://github.com/vitorpamplona/nips/blob/generative-ai-nip/104.md

生成 AI のプロンプト。

このイベントを受け取ったクライアントが画像や動画を生成する。

PR: https://github.com/nostr-protocol/nips/pull/634

## NIP-105: API Service Marketplace

https://github.com/CoachChuckFF/nips/blob/NIP-105/105.md

API サービス プロバイダー。

API サービス プロバイダーは API サービス オファリング (`kind:31402`) を作成する。

クライアントは `s` タグによって API サービス オファリングを取得および API サービス プロバイダーを選択して、`content` のエンドポイントにサービスを要求する。

[NIP-90](#NIP-90-Data-Vending-Machine) (Data Vending Machine) との比較: https://github.com/nostr-protocol/nips/pull/780#issuecomment-1719606308

PR: https://github.com/nostr-protocol/nips/pull/780

## NIP-109: Pubkey Deletion

https://github.com/alexgleason/nips/blob/delete-pubkey/109.md

公開鍵の削除。

PR: https://github.com/nostr-protocol/nips/pull/377

## NIP-111: Accessibility (A11y)

https://github.com/fernandolguevara/nips/blob/a11y/111.md

ユーザーのアクセシビリティーの設定。

PR: https://github.com/nostr-protocol/nips/pull/702

## NIP-112: Encrypted Group Events

https://github.com/earonesty/nips/blob/112/112.md

[NIP-44](#NIP-44-Encrypted-Direct-Message-Versioned) (Encrypted Direct Message (Versioned)) と [NIP-59](#NIP-59-Gift-Wrap) (Gift Wrap) を使用するプライベート グループ チャット。

PR: https://github.com/nostr-protocol/nips/pull/580

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

## NIP-3166: Country Code

https://github.com/steliosrammos/nips/blob/nip-3166-geo-location-tag/3166.md

2 文字の ISO 国名コード (JP、US、BR など) を持つ `c` タグ。

PR: https://github.com/nostr-protocol/nips/pull/763

## NIP-XX: Use Nostr as storage for chart data

https://github.com/nostr-protocol/nips/issues/743

チャート データ。Shino3 さん著。

## NIP-XX: Decentralized Web Hosting on Nostr

https://github.com/nostr-protocol/nips/issues/742

Nostr で Web ホスティング。kaiji さん著。

kind:
 - `kind: 5392`: HTML
 - `kind: 5393`: CSS
 - `kind: 5394`: JavaScript

kind (パラメーター化された置き換え可能なイベント):
 - `kind: 35392`: HTML
 - `kind: 35393`: CSS
 - `kind: 35394`: JavaScript

実装: https://github.com/studiokaiji/nostr-webhost

## NIP-XXX: Order

https://github.com/civkit/nips/blob/2023-07-nip-xxx-order/XXX.md

オファー (BOLT12) のイベント。

PR: https://github.com/nostr-protocol/nips/pull/638
