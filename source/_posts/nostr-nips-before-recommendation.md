---
title: "Nostr: 勧告前の NIPs"
date: 2023-05-12 23:15:50
updated: 2023-05-18 00:04:34
tags: [Nostr]
---

![image.jpg](nostr-nips-before-recommendation/image.jpg)

Nostr の気になった勧告前の NIPs。

随時更新。

<!-- more -->

## ~~NIP-30: Custom Emoji~~

マージされた。

https://github.com/nostr-protocol/nips/blob/master/30.md

~~https://github.com/alexgleason/nips/blob/emojis/30.md~~

~~カスタム絵文字。~~

~~PR: https://github.com/nostr-protocol/nips/pull/484~~

## NIP-32

https://github.com/staab/nips/blob/nip-32-labeling/32.md

ラベリング。

[NIP-68](#NIP-68) も参照のこと。

PR: https://github.com/nostr-protocol/nips/pull/532

## NIP-54 - Inline Resource Metadata

https://github.com/arthurfranca/nips/blob/inline-resource-metadata/54.md

URL や [NIP-21](https://github.com/nostr-protocol/nips/blob/master/21.md) の末尾に追加される `#t=24&a%20name=a%20value` のようなパラメーター。

[DIP-01](https://github.com/damus-io/dips/blob/master/01.md) も参照のこと。

PR: https://github.com/nostr-protocol/nips/pull/521

## NIP-68

https://github.com/rabble/nips/blob/nip-69/68.md

ラベリング。

[NIP-32](#NIP-32) も参照のこと。

PR: https://github.com/nostr-protocol/nips/pull/457

## NIP-89

https://github.com/pablof7z/nips/blob/application-handlers/89.md

未知の kind を処理するための推奨アプリケーション。

PR: https://github.com/nostr-protocol/nips/pull/530

## NIP-93: NSON

https://github.com/nostr-protocol/nips/blob/nip93-nson/93.md

JSON のデコードを高速化するための `nson` フィールド。

NSON は造語？

PR: https://github.com/nostr-protocol/nips/pull/515

## NIP-95 - Storage and Shared File

https://github.com/frbitten/nostr-nips/blob/NIP-95/95.md

Nostr でファイル ストレージ。

PR: https://github.com/nostr-protocol/nips/pull/345

## NIP-98 HTTP Auth

https://github.com/v0l/nips/blob/nip98/98.md

Nostr のイベントで HTTP 認証。

エンドポイントを含む `kind: 27235` のイベントを base64 エンコードして、HTTP Authorization ヘッダーに乗せてリクエストする。

リファレンス実装: [NostrAuth.cs](https://gist.github.com/v0l/74346ae530896115bfe2504c8cd018d3) (C#、ASP.NET による認証ハンドラー)

PR: https://github.com/nostr-protocol/nips/pull/469

## NIP-99: Prediction markets

https://github.com/ekzyis/nips/blob/nip-prediction-markets/99.md

予測市場 (先物市場)。

PR: https://github.com/nostr-protocol/nips/pull/517

## NIP-109: Pubkey Deletion

https://github.com/alexgleason/nips/blob/delete-pubkey/109.md

公開鍵の削除。

PR: https://github.com/nostr-protocol/nips/pull/377
