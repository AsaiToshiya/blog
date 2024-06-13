---
title: "Nostr: 勧告前の NIPs"
date: 2023-05-12 23:15:50
updated: 2024-06-13 21:24:40
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

## NIP-22: Comment

https://github.com/arthurfranca/nips/blob/comment/22.md

あらゆるイベントへのコメント (返信)。`kind: 1111`。

[NIP-00: Thread](https://asaitoshiya.com/nostr-nips-before-recommendation-archive/#NIP-00-Thread) のブラッシュアップな印象。

PR: https://github.com/nostr-protocol/nips/pull/1233

## NIP-29: Shared Event Ownership Through Trusted DVMs

https://github.com/vitorpamplona/nips/blob/dvm-replaceables/29.md

DVM ([NIP-90: Data Vending Machine](https://github.com/nostr-protocol/nips/blob/master/90.md)) を介したイベントの共同編集。

イベントはユーザーの代わりに DVM の秘密鍵で署名され、イベントを編集できるユーザーは `admin` タグで表される。

PR: https://github.com/nostr-protocol/nips/pull/1015

## NIP-29: Time-Based Sync

https://github.com/vitorpamplona/nips/blob/negentropy-sync/29.md

クライアント - リレーやリレー - リレーでイベントを同期するために使用されるハッシュ。

ハッシュの要求と応答は、`WEEKLY-HASHES` メッセージで行う。

PR: https://github.com/nostr-protocol/nips/pull/826

## NIP-34: Algorithmic Filter

https://github.com/arthurfranca/nips/blob/nip-34/34.md

フィルターに `limit` が指定されている場合のイベントの並び順。

`["REQ", <subscription_id>, { ..., limit: 5, nip34: "asc" }]` のように指定する。

PR: https://github.com/nostr-protocol/nips/pull/579

## NIP-35: Draft Events

https://github.com/vitorpamplona/nips/blob/draft-event/35.md

下書き用の汎用的なイベント。

任意のイベント (下書き) を [NIP-44](https://github.com/nostr-protocol/nips/blob/master/44.md) (Encrypted Payloads (Versioned)) で暗号化して `.content` に含める。

PR: https://github.com/nostr-protocol/nips/pull/1124

## NIP-35: Member List

https://github.com/arthurfranca/nips/blob/nip-35/35.md

グループ、チャンネル、コミュニティーなどに属するユーザーの「連絡可能」、「退席中」などの状態。

PR: https://github.com/nostr-protocol/nips/pull/607

## NIP-37: Editable Short Notes

https://github.com/vitorpamplona/nips/blob/content-editable-kind1-unboundlist/37.md

`kind: 1` (Short Text Note) の `content` の履歴。`kind: 1010`

`n` タグの ID に一致する `kind: 1` の `content` を置き換えて表示する

PR: https://github.com/nostr-protocol/nips/pull/1090

## NIP-37: Annotations

https://github.com/coracle-social/nips/blob/annotations/37.md

自分の他のイベントに付けることができる注釈 (コメント)。

PR: https://github.com/nostr-protocol/nips/pull/1091

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

## NIP-41: Key migration

https://github.com/nostr-protocol/nips/blob/pf7z-nip41/41.md

公開鍵の移行。

事前に作成するバックアップ (移行先) になる公開鍵を示すイベント (`kind: 1776`) と公開鍵を移行するためのイベント (`kind: 1777`)。

これらのイベントには、NIP-03 (OpenTimestamps Attestations for Events) の OpenTimestamps を付ける必要がある。

PR: https://github.com/nostr-protocol/nips/pull/829

## NIP-54: Inline Resource Metadata

https://github.com/arthurfranca/nips/blob/inline-resource-metadata/54.md

`content` 内のインライン リソースの読み込みを強化するために、URL や [NIP-21](https://github.com/nostr-protocol/nips/blob/master/21.md) の末尾に追加される `#t=24&a%20name=a%20value` のようなパラメーター。

[DIP-01](https://github.com/damus-io/dips/blob/master/01.md) も参照のこと。

PR: https://github.com/nostr-protocol/nips/pull/521

## NIP-60: Zap Gates

https://github.com/Egge7/nips/blob/zapGates/60.md

[NIP-98](#NIP-98-HTTP-Auth) (HTTP Auth) のリソースに [NIP-57](https://github.com/nostr-protocol/nips/blob/master/57.md) (Lightning Zaps) でアクセスできるようにする。

PR: https://github.com/nostr-protocol/nips/pull/542

## NIP-61: Event Set

https://github.com/arthurfranca/nips/blob/bunch-of-events/61.md

リレーのイベントのサイズの制限を回避することができるリスト。

pubkey および `n` タグでリストを定義して、`u` タグまたは `nunb` でリストを参照する。

PR: https://github.com/nostr-protocol/nips/pull/784

## NIP-62: Signed and Versioned Third-Party Objects

https://github.com/buttercat1791/nips/blob/master/62.md

バージョン管理を考慮した、オブジェクト (Git コミット、ドキュメント、画像など) を示すイベント。

オブジェクト (`kind: 32000`) とそのバージョン (`kind: 32001`) で構成される。

[NIP-94: File Metadata](https://github.com/nostr-protocol/nips/blob/master/94.md) に近い印象。

PR: https://github.com/nostr-protocol/nips/pull/986

## NIP-62: Right to Vanish

https://github.com/vitorpamplona/nips/blob/right-to-vanish/62.md

忘れられる権利。すべてのイベントをリレーから削除。

kind:
 - `kind: 62`: 特定のリレー
 - `kind: 63`: すべてのリレー

PR: https://github.com/nostr-protocol/nips/pull/1256

## NIP-64: Inbox model

https://github.com/nostr-protocol/nips/blob/inbox-model/64.md

受信ボックス (`kind: 10064`) とフォロー インテント (`kind: 6401`) を使用するインボックス モデル。

ユーザーは受信ボックス (A) を作成して、フォロワーは A のリレーにフォロー インテント (B) を送信する。

ユーザーは A のリレーから B をフェッチして、フェッチした B のリレーにイベントを送信する。

関連: https://github.com/nostr-protocol/nips/discussions/1134

PR: https://github.com/nostr-protocol/nips/pull/1135

## NIP-69: Linked Crytographic Identities

https://github.com/fr4nzap/nips/blob/linked-cryptographic-identities/69.md

NIP-39: External Identities in Profiles の PGP や SSL 版で、これらの暗号鍵と Nostr の公開鍵をリンクする。

関連: https://github.com/nostr-protocol/nips/pull/1041
関連: https://github.com/nostr-protocol/nips/commit/afbb8dd008969c863f6075645d09fcb1ef283ed2

PR: https://github.com/nostr-protocol/nips/pull/1182

## NIP-69: Zap Poll event

https://github.com/toadlyBroodle/nips/blob/master/69.md

Zap による投票。

質問のイベント (`kind: 6969`) に [NIP-57](https://github.com/nostr-protocol/nips/blob/master/57.md) (Lightning Zaps) の Zap リクエストのイベント (`kind: 9734`) で投票する。

一部のクライアントでは既に実装されている。

PR: https://github.com/nostr-protocol/nips/pull/320

## NIP-74: Proxy and Broadcasting Relay Lists

https://github.com/vitorpamplona/nips/blob/broadcasting-proxy-relay-lists/74.md

クライアントで優先されるプロキシー (読み取り) リレーとブロードキャスト (書き込み) リレーのプライベート リスト。`kind: 10017`、`kind: 10018`。

この NIP は https://github.com/nostr-protocol/nips/discussions/1301 を解決するわけではなさそう。

関連: https://github.com/nostr-protocol/nips/discussions/1301

PR: https://github.com/nostr-protocol/nips/pull/1303

## NIP-77: Nostr Data Sharing URI Scheme

https://github.com/mandelmonkey/nips/blob/master/77.md

Nostr クライアントにテキストや画像を共有するための URI スキーマ (`nostr-share://`)。

リファレンス実装:
https://github.com/mandelmonkey/nostr-share-sample-game
https://github.com/mandelmonkey/nostr-share-wallet-demo

PR: https://github.com/nostr-protocol/nips/pull/491

## NIP-79: Digital Contracts

https://github.com/xemuj/nips/blob/DigitalContracts/79.md
~~https://github.com/nostr-protocol/nips/discussions/752~~

電子契約・電子署名。

PR: https://github.com/nostr-protocol/nips/pull/755

## NIP-81: Relationship Status

https://github.com/vitorpamplona/nips/blob/relationship-status/81.md

フォローしているユーザーとの関係性。

パラメーター化された置き換え可能なイベント (PRE) で、各フォローに対して 1 つのイベント。

参考: https://github.com/nostr-protocol/nips/pull/349#issuecomment-1472395508

PR: https://github.com/nostr-protocol/nips/pull/761

## NIP-85: Reviews

https://github.com/coracle-social/nips/blob/reviews/85.md

レビューを表すイベント。

例:

```json
{
  "kind": 1986,
  "content": "This relay is fast!",  // 人間が読めるレビュー
  "tags": [
    ["L", "review"],                 // NIP-32 のラベル
    ["l", "review/relay", "review"], // 同上
    ["rating", "0.8"],               // レーティング
    ["rating", "0.2", "smell"],      // オプションのレーティングの属性
    ["rating", "1", "service"],      // 同上
    ["r", <relay_url>]               // レビューの対象。ここではリレー
  ],
}
```

PR: https://github.com/nostr-protocol/nips/pull/879

## NIP-86: Shared Keys

https://github.com/coracle-social/nips/blob/groups/86.md
~~https://github.com/coracle-social/nips/blob/key-sharing/86.md~~

秘密鍵の共有 (共有鍵)。

秘密鍵は [NIP-59: Gift Wrap](https://github.com/nostr-protocol/nips/blob/master/59.md) でユーザーごとに個別に共有される。

PR: https://github.com/nostr-protocol/nips/pull/875
~~PR: https://github.com/nostr-protocol/nips/pull/876~~

## NIP-87: Closed Groups

https://github.com/coracle-social/nips/blob/groups/87.md

共有鍵 ([NIP-86: Shared Keys](#NIP-86-Shared-Keys)) でメッセージをラップ ([NIP-59: Gift Wrap](https://github.com/nostr-protocol/nips/blob/master/59.md)) することでプライベートなコミュニティー ([NIP-72: Moderated Communities](https://github.com/nostr-protocol/nips/blob/master/72.md)) を実現する。

PR: https://github.com/nostr-protocol/nips/pull/875

## NIP-88: Nostr Cash (simple Nostr cash/token/cheque)

https://github.com/arcbtc/nips/blob/nostrcash/88.md

Nostr ネイティブなウォレットとミント (造幣局)。

クライアントはウォレットの役目を負い、リレーはミントの役目を負う。

PR: https://github.com/nostr-protocol/nips/pull/627

## NIP-88: NOTIFY Request

https://github.com/vitorpamplona/nips/blob/pay-spec/88.md

リレーから任意のタイミングで送信される、何かしらを通知する `NOTIFY` メッセージ。

PR: https://github.com/nostr-protocol/nips/pull/901

## NIP-88: Recurring Subscriptions

https://github.com/nostr-protocol/nips/blob/nip88/88.md

Zap によるユーザーへの定期的な支援。

kind:
 - `kind: 7002`: 支援される側が作成する Patreon のティアのような支援のプラン
 - `kind: 7001`: 支援する側が作成する支援の表明

PR: https://github.com/nostr-protocol/nips/pull/866

## NIP-93: Alternative URLs

https://github.com/nostr-protocol/nips/blob/alt-urls/93.md

代替 URL を示す `alturl` タグと `kind: 4001` のイベント。

リンク切れを防ぐ。

PR: https://github.com/nostr-protocol/nips/pull/898

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

## NIP-97: Files hosted on relay

https://github.com/ondra-novak/nostr-nip-97/blob/version-2/97.md

バイナリー ファイル。

`kind: 1063` (NIP-94: File Metadata) を拡張したイベントと 2 つのメッセージ タイプ (`FILE` と `RETRIEVE`) でバイナリー ファイルを扱う。

関連: https://github.com/nostr-protocol/nips/pull/694

PR: https://github.com/nostr-protocol/nips/pull/719

## NIP-97: Nostr Login

https://github.com/nostr-protocol/nips/blob/login/97.md

サービスが NIP-98: HTTP Auth でログインできることを示す `nostr+login:` スキーマ (ログイン URI)？

PR: https://github.com/nostr-protocol/nips/pull/1042

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

## NIP-101: Descriptor Note

https://github.com/unostr/nips/blob/nip-101---descriptor-note/101.md

「Stuff」を記述するためのメモ。`kind: 101`。

主に NIP-211: Info Triple Note で使用することを想定。

例 (`content`):

```
1234567890abcdef1234567890abcdef              // 「Stuff」の識別子 (必須)

order-number_12345                            // 名前

webshop order of a T-shirt                    // 1 行の短い説明

"This is awesome" T-shirt in size L.          // 複数行の説明
Ordered from the webshop (order number 12345)
Remember to pack sticker freebies.
```

詳細: https://descriptor-note.surge.sh/

PR: https://github.com/nostr-protocol/nips/pull/892

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

## NIP-105: API Service Marketplace

https://github.com/CoachChuckFF/nips/blob/NIP-105/105.md

API サービス プロバイダー。

API サービス プロバイダーは API サービス オファリング (`kind:31402`) を作成する。

クライアントは `s` タグによって API サービス オファリングを取得および API サービス プロバイダーを選択して、`content` のエンドポイントにサービスを要求する。

[NIP-90](#NIP-90-Data-Vending-Machine) (Data Vending Machine) との比較: https://github.com/nostr-protocol/nips/pull/780#issuecomment-1719606308

PR: https://github.com/nostr-protocol/nips/pull/780

## NIP-106: Decentralized Web Hosting on Nostr

https://github.com/studiokaiji/nips/blob/master/106.md
~~https://github.com/nostr-protocol/nips/issues/742~~

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

PR: https://github.com/nostr-protocol/nips/pull/811

## NIP-108: Lightning Gated Notes

https://github.com/project-excalibur/nips/blob/NIP-108_lightning_gated_content/108.md

有料コンテンツ (任意のイベント)。

この NIP を実装する API サーバーが、有料コンテンツを暗号化するときに使用した任意の秘密鍵を保持し、料金を支払ったユーザーにその秘密鍵を配る仕組み。

PR: https://github.com/nostr-protocol/nips/pull/827

## NIP-109: Pubkey Deletion

https://github.com/alexgleason/nips/blob/delete-pubkey/109.md

公開鍵の削除。

PR: https://github.com/nostr-protocol/nips/pull/377

## NIP-110: License tag

https://github.com/degenrocket/nips/blob/nip-110/110.md

イベントのライセンスを示す `license` タグ。

例:

```
{"tags": [["license", "CC0"]]}
```

PR: https://github.com/nostr-protocol/nips/pull/857

## NIP-111: Accessibility (A11y)

https://github.com/fernandolguevara/nips/blob/a11y/111.md

ユーザーのアクセシビリティーの設定。

PR: https://github.com/nostr-protocol/nips/pull/702

## NIP-112: Encrypted Group Events

https://github.com/earonesty/nips/blob/112/112.md

[NIP-44](https://github.com/nostr-protocol/nips/blob/master/44.md) (Encrypted Direct Message (Versioned)) と [NIP-59](https://github.com/nostr-protocol/nips/blob/master/59.md) (Gift Wrap) を使用するプライベート グループ チャット。

PR: https://github.com/nostr-protocol/nips/pull/580

## NIP-117: Bounties

https://github.com/ChristianChiarulli/nips/blob/nip-117-bounties/117.md

タスクに対する報奨金 (`kind: 30050`) とその申請 (`kind: 8050`)。

デモ サイト: https://resolvr-io.vercel.app/

PR: https://github.com/nostr-protocol/nips/pull/865

## NIP-199: a simple username password login

https://github.com/nostr-protocol/nips/issues/639

ユーザー名とパスワードによるログイン (秘密鍵の保管)。

秘密鍵は PBKDF2 (ユーザー名とパスワードから導出された共通鍵) と AES で暗号化されて、`kind: 30669` でリレーに保管される。

## NIP-200: Nostr relay communication over HTTP(s) (NoH)

https://github.com/Yonle/nips/blob/nip200/200.md

リレーの HTTP インターフェース。

実装:
 - [nhttp](https://github.com/Yonle/nhttp): この NIP の実装。HTTP インターフェース
 - [nhttp-adapter](https://github.com/Yonle/nhttp-adapter): HTTP のアダプターになるリレー
 - [nostr-relay-http-chunk](https://github.com/mattn/nostr-relay-http-chunk/): チャンク ストリームの PoC (mattn さん)

PR: https://github.com/nostr-protocol/nips/pull/966

## NIP-211: Info Triple Note

https://github.com/unostr/nips/blob/nip-211---info-triple/211.md

「Stuff」間の関係を記述するためのメモ。`kind: 211`。

関連: [NIP-101: Descriptor Note](#NIP-101-Descriptor-Note)
詳細: https://www.infotriple.org/

PR: https://github.com/nostr-protocol/nips/pull/893

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

## NIP-XX: Audio Events

https://github.com/coracle-social/nips/blob/music/xx.md

音声/音楽を表すイベント。`kind 31337`。

PR: https://github.com/nostr-protocol/nips/pull/1043

## NIP-XX: External Content IDs

https://github.com/MerryOscar/nips/blob/external-content-ids/XX.md

ISBN やポッドキャストの GUID などの外部コンテンツを示す `i` タグ。

例:

```json
["i", "book:isbn:123"]         // ISBN
["i", "podcast:guid:123"]      // ポッドキャスト
["i", "podcast:item:guid:123"] // ポッドキャスト (エピソード)
["i", "movie:eidr:123"]        // EIDR
```

PR: https://github.com/nostr-protocol/nips/pull/1185

## NIP-XX: Improved event signing scheme

https://github.com/sant0s12/nips/blob/master/XX.md

タグ (`tags` プロパティー) だけではなく、純粋なプロパティーを使用できるようにするための署名。

```
{
  "id": ...,
  "pubkey": ...,
  "created_at": ...,
  "kind": ...,
  "tags": ...,
  "content": ...,
  "sig": ...,
  "super_cool": ..., // このように純粋なプロパティーを使用できる
  "sig_v2": ...      // この NIP で追加される署名のプロパティー
}
```

PR: https://github.com/nostr-protocol/nips/pull/1258

## NIP-XX: Nostr Token Login

https://github.com/arthurfranca/nips/blob/token/xx.md

NIP-26 (Delegated Event Signing) の NIP-19 (bech32-encoded entities) のエンティティーを表す `ntoken`。

`nsec` の代わりに使用することを想定。

PR: https://github.com/nostr-protocol/nips/pull/793

## NIP-XX: Read Status

https://github.com/coracle-social/nips/blob/read-status/xx.md

イベントの既読を示すイベント。

```json
{
  "kind": "15",
  "tags": [
    ["expiration", "<unix-timestamp>"], // NIP-40: Expiration Timestamp
    ["e", "<event-id>"],
    ["e", "<event-id>"]
  ]
}
```

[NIP-59: Gift Wrap](https://github.com/nostr-protocol/nips/blob/master/59.md) によってプライベートにすることもできる。

関連: https://github.com/nostr-protocol/nips/discussions/932

PR: https://github.com/nostr-protocol/nips/pull/933

## NIP-XX: Use Nostr as storage for chart data

https://github.com/nostr-protocol/nips/issues/743

チャート データ。Shino3 さん著。

## NIP-XXX: Internationalization & Localization

https://github.com/eznix86/nips/blob/patch-2/nip-xxx.md

イベントの言語タグ (`language`) とプロフィール (`kind 0`) の言語属性 (`allowed_language`、`language`)。

関連: [NIP-37: Language Tag](#NIP-37-Language-Tag)
関連: https://github.com/nostr-protocol/nips/pull/1129

PR: https://github.com/nostr-protocol/nips/pull/1127

## NIP-XXX: Order

https://github.com/civkit/nips/blob/2023-07-nip-xxx-order/XXX.md

オファー (BOLT12) のイベント。

PR: https://github.com/nostr-protocol/nips/pull/638
