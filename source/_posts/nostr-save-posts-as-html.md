---
title: "Nostr: 投稿を HTML として保存する"
date: 2023-02-16 00:08:08
updated: 2023-11-27 12:42:07
tags: [Nostr]
---

以下のスクリプトを使用して、Nostr (ノスター、ノストラ、ノストル) の投稿を HTML として保存する。

vercel-nostr-posts: https://github.com/AsaiToshiya/vercel-nostr-posts

[![vercel-nostr-posts](https://opengraph.githubassets.com/39a24f2f4dc156f9732241d014dae016eacbe8f0d0a0680cc1520179ce90a416/AsaiToshiya/vercel-nostr-posts)](https://github.com/AsaiToshiya/vercel-nostr-posts)

<!-- more -->

## 手順

### 1. リポジトリをセットアップ

```bash
git clone --recursive https://github.com/AsaiToshiya/vercel-nostr-posts.git
cd vercel-nostr-posts
npm install
```

### 2. index.js 内の投稿者の公開鍵を変更

index.js:

```javascript
// 投稿者の公開鍵 (16 進数)
const PK = "0a2f19dc1a185792c3b0376f1d7f9971295e8932966c397935a5dddd1451a25a";
```

### 3. スクリプトを実行

```bash
$ node index.js
```

カレント ディレクトリーに index.html と hashtag.html が作成される。

index.html:

![index-html.png](nostr-save-posts-as-html/index-html.png)

hashtag.html:

![hashtag-html.png](nostr-save-posts-as-html/hashtag-html.png)
