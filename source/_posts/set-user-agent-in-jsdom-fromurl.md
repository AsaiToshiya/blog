---
title: JSDOM の fromURL で User-Agent を設定する
date: 2022-05-16 15:45:12
updated: 2022-05-16 15:45:12
---
<p></p>

<!-- more -->
## 環境

- JSDOM 19.0.0


## 方法

`ResourceLoader` を使用する。

```javascript
import { JSDOM, ResourceLoader } from "jsdom";
...
const resourceLoader = new ResourceLoader({
  userAgent: "Mozilla/5.0",
});
const dom = await JSDOM.fromURL(url, { resources: resourceLoader });
```

ただし、この方法はリソースの読み込みが発生する。

リソースが不要な場合は、一度だけリソースをフェッチする独自の `ResourceLoader` を使用する。

注: フェッチされるリソースは `fromURL` の `url`。

one-time-fetch-resource-loader.js:

```javascript
import { ResourceLoader } from "jsdom";

export class OneTimeFetchResourceLoader extends ResourceLoader {
  constructor(options) {
    super(options);
    this._fetched = false;
  }

  fetch(url, options) {
    if (this._fetched) {
      return null;
    }
    this._fetched = true;
    return super.fetch(url, options);
  }
}
```

```javascript
import { JSDOM } from "jsdom";

import { OneTimeFetchResourceLoader } from "./one-time-fetch-resource-loader.js";
...
const resourceLoader = new OneTimeFetchResourceLoader({
  userAgent: "Mozilla/5.0",
});
const dom = await JSDOM.fromURL(url, { resources: resourceLoader });
```
