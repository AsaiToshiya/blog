---
title: "Electron Forge: node-abi のエラーが発生した場合の対処方法"
date: 2023-01-24 22:20:28
updated: 2023-01-24 22:20:28
tags: [Electron Forge, トラブルシューティング]
---

```
An unhandled error has occurred inside Forge:
Could not detect abi for version 22.0.1 and runtime electron.  Updating "node-abi" might help solve this issue if it is a new release of electron
Error: Could not detect abi for version 22.0.1 and runtime electron.  Updating "node-abi" might help solve this issue if it is a new release of electron
```

<!-- more -->

## 手順

1. node_modules と package-lock.json を削除する。
2. `npm install` を実行する。

参考: [node-abi needs to be updated · Issue #667 · electron/forge][1]

[1]: https://github.com/electron/forge/issues/667
