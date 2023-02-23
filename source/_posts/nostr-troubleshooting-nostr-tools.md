---
title: "Nostr: nostr-tools のトラブルシューティング"
date: 2023-02-22 06:31:40
updated: 2023-02-22 06:31:40
tags: [Nostr, nostr-tools, トラブルシューティング]
---

JavaScript モジュールで [nostr-tools](https://github.com/nbd-wtf/nostr-tools) を使用する場合のトラブルシューティング。

<!-- more -->

## 環境

- Node.js 16.16.0
- nostr-tools 1.3.2

## `SyntaxError: Named export 'SimplePool' not found. The requested module 'nostr-tools' is a CommonJS module, which may not support all module.exports as named exports.`

```javascript
import { SimplePool } from "nostr-tools";
```

以下のエラーが発生する。

```
import { SimplePool } from "nostr-tools";
         ^^^^^^^^^^
SyntaxError: Named export 'SimplePool' not found. The requested module 'nostr-tools' is a CommonJS module, which may not support all module.exports as named exports.       
CommonJS modules can always be imported via the default export, for example using:

import pkg from 'nostr-tools';
const { SimplePool } = pkg;
```

import をメッセージのとおり書き換える。

```javascript
import pkg from "nostr-tools";
const { SimplePool } = pkg;
```

## `ReferenceError: WebSocket is not defined`

```
      ws = new WebSocket(url);
      ^

ReferenceError: WebSocket is not defined
```

websocket-polyfill をインストールしてインポートする。

```
npm i websocket-polyfill
```

```javascript
import "websocket-polyfill";
```

https://github.com/nbd-wtf/nostr-tools#interacting-with-a-relay

## `TypeError: Cannot read properties of undefined (reading 'sendCloseFrame')`

```javascript
const pool = new SimplePool();
const posts = await pool.list(RELAYS, [
  {
    authors: [PK],
    kinds: [1],
  },
]);
...
await pool.close(RELAYS);
```

`pool.close` で以下のエラーが発生する。

```
            this.connection_.sendCloseFrame();
                             ^

TypeError: Cannot read properties of undefined (reading 'sendCloseFrame')
```

未解決。暫定的に、`pool.close` をコメントアウトして、`process.exit` で強制終了させる。

```javascript
...
// await pool.close(RELAYS);
process.exit();
```

## `pool.list` のタイムアウト

```javascript
const pool = new SimplePool();
const posts = await pool.list(RELAYS, [
  {
    authors: [PK],
    kinds: [1],
  },
]);
```

`pool.list` でタイムアウトが発生する場合がある。

`pool.list` の前に以下のコードを追加し、nostr-tools のタイムアウトを長くする。

```
const temp = setTimeout;
setTimeout = (func) => temp(func, 30 * 1000);
```

## `UnhandledPromiseRejection: This error originated either by throwing inside of an async function without a catch block`

```javascript
const RELAYS = [
  "wss://nos.lol",
  "wss://nostr-pub.wellorder.net",
  "wss://nostr.bitcoiner.social",
  "wss://nostr.mom",
  "wss://nostr.oxtr.dev",
  "wss://relay.damus.io",
  "wss://relay.nostr.bg",
];

const pool = new SimplePool();
const posts = await pool.list(RELAYS, [
  {
    authors: [PK],
    kinds: [1],
  },
]);
```

`pool.list` で以下のエラーが発生する。

```
node:internal/process/promises:279
            triggerUncaughtException(err, true /* fromPromise */);
            ^

[UnhandledPromiseRejection: This error originated either by throwing inside of an async function without a catch block, or by rejecting a promise which was not handled with .catch(). The promise rejected with the reason "undefined".] {
  code: 'ERR_UNHANDLED_REJECTION'
}
```

未解決。暫定的に、エラーを引き起こすリレー サーバーを削除する。
