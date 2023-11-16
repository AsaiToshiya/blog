---
title: "Nostr: 勧告前の NIPs (アーカイブ)"
date: 2023-08-08 13:20:42
updated: 2023-11-15 12:46:13
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

## NIP-24: Extra metadata fields and tags

マージされた。

https://github.com/nostr-protocol/nips/blob/master/24.md

https://github.com/nostr-protocol/nips/blob/extra/24.md

NIP で明記されていない追加のフィールド (`kind: 0` の `display_name` など) やタグ (`r` タグなど)。

PR: https://github.com/nostr-protocol/nips/pull/794

## NIP-24: Rich Text Note

クローズした。

https://github.com/AsaiToshiya/nips/blob/nip-24-rich-text-note/24.md

HTML や Markdown などの「リッチ テキスト メモ」。拙著。

日本語: https://github.com/AsaiToshiya/nip-24-rich-text-note/blob/main/24-ja.md

PR: https://github.com/nostr-protocol/nips/pull/619

## NIP-30: Custom Emoji

マージされた。

https://github.com/nostr-protocol/nips/blob/master/30.md

https://github.com/alexgleason/nips/blob/emojis/30.md

カスタム絵文字。

PR: https://github.com/nostr-protocol/nips/pull/484

## NIP-32: Labeling

マージされた。

https://github.com/nostr-protocol/nips/blob/master/32.md

https://github.com/staab/nips/blob/nip-32-labeling/32.md

ラベリング。

[NIP-68](#NIP-68-Content-Labeling-including-Reviews-amp-Recommendations) も参照のこと。

PR: https://github.com/nostr-protocol/nips/pull/532

## NIP-38: User Statuses

マージされた。

https://github.com/nostr-protocol/nips/blob/master/38.md

https://github.com/jb55/nips/blob/user-statuses/315.md

ユーザーの「仕事中」、「ハイキング中」や視聴中の音楽などの状態。`kind 30315`。

PR: https://github.com/nostr-protocol/nips/pull/737

## NIP-44: Encrypted Direct Message (Versioned)

[#715](https://github.com/nostr-protocol/nips/pull/715) に置き換えられた。

https://github.com/paulmillr/nips/blob/master-1/44.md

暗号化アルゴリズムをバージョン管理 (選択) できるようにする [NIP-04](https://github.com/nostr-protocol/nips/blob/master/04.md) (Encrypted Direct Message) の代替。

PR: https://github.com/nostr-protocol/nips/pull/574

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

## NIP-75: Zap Goals

マージされた。

https://github.com/nostr-protocol/nips/blob/master/75.md

https://github.com/nostr-protocol/nips/blob/goals/75.md

クラウド ファンディングのような目標金額を示すイベント。

パラメーター化された置き換え可能なイベント (PRE) に `goal` タグを指定すると、そのイベントへの Zap も集計対象にすることができる。

PR: https://github.com/nostr-protocol/nips/pull/757

## NIP-84: Highlights

マージされた。

https://github.com/nostr-protocol/nips/blob/master/84.md

https://github.com/pablof7z/nips/blob/highlights/84.md

コンテンツの引用とハイライト。

PR: https://github.com/nostr-protocol/nips/pull/501

## NIP-86: Shared Keys

https://github.com/coracle-social/nips/blob/key-sharing/86.md

クローズされた。

秘密鍵の共有 (共有鍵)。

秘密鍵は [NIP-59: Gift Wrap](https://asaitoshiya.com/nostr-nips-before-recommendation/#NIP-59-Gift-Wrap) でユーザーごとに個別に共有される。

PR: https://github.com/nostr-protocol/nips/pull/876

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

## NIP-101: Standard HTTP REST API for Relays

クローズされた。

https://github.com/jacany/nips/blob/101/101.md

リレーが提供する REST API。

PR: https://github.com/nostr-protocol/nips/pull/680

## NIP-lol: Truly Private Messages

[ディスカッション](https://github.com/nostr-protocol/nips/discussions/658)に移動された。

https://github.com/MaxHillebrand/nips/blob/NIPlol-private-messages/lol.md

NIP-04 (Encrypted Direct Message) の代替。

PR: https://github.com/nostr-protocol/nips/pull/564
