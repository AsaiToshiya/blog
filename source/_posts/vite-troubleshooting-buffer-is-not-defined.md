---
title: "Vite: `Buffer is not defined` のエラーが発生した場合の対処方法"
tags: [Vite, トラブルシューティング]
---

`vite build` コマンドを使用して本番環境用にビルドしたアプリケーションで、`Buffer is not defined` のエラーが発生した場合の対処方法。

<!-- more -->

## 環境

- Vite 5.0.8

## 原因

ブラウザーが Node.js のコア モジュール (ここでは、Buffer オブジェクト) をネイティブにサポートしておらず、オブジェクトが未定義 (`undefined`) になるため。

## 対処方法

ポリフィルの [vite-plugin-node-polyfills](https://github.com/davidmyersdev/vite-plugin-node-polyfills) を使用する。

1. vite-plugin-node-polyfills をインストールする。

    ```bash
    pnpm install --save-dev vite-plugin-node-polyfills
    ```

2. vite-plugin-node-polyfills を `vite.config.js` ファイルに追加する。

    vite.config.js:
    
    ```javascript
    import { defineConfig } from "vite";
    import { nodePolyfills } from "vite-plugin-node-polyfills";
    
    export default defineConfig({
      plugins: [nodePolyfills()],
    });
    ```
