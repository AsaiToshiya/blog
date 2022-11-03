---
title: "SolidJS: For コンポーネントを React のように記述するためのワンライナー"
tags: [SolidJS]
---

![logo.svg](solidjs-one-liner-for-writing-for-component-like-react/logo.svg)

以下の [`For`](https://www.solidjs.com/tutorial/flow_for) コンポーネントを、

```javascript
<For each={cats()}>{(cat, i) =>
  <li>
    <a target="_blank" href={`https://www.youtube.com/watch?v=${cat.id}`}>
      {i() + 1}: {cat.name}
    </a>
  </li>
}</For>
```

以下の React のように記述するためのワンライナー。

```javascript
{cats.map((cat, i) =>
  <li>
    <a target="_blank" href={`https://www.youtube.com/watch?v=${cat.id}`}>
      {i + 1}: {cat.name}
    </a>
  </li>
)}
```

<!-- more -->
## 環境

- SolidJS 1.5.1


## ソースコード

```javascript
const _ = (array) => ({ map: (fn) => <For each={array()}>{fn}</For> })
```

以下のように使用する。

```javascript
{_(cats).map((cat, i) =>
  <li>
    <a target="_blank" href={`https://www.youtube.com/watch?v=${cat.id}`}>
      {i() + 1}: {cat.name}
    </a>
  </li>
)}
```

[Solid Playground](https://playground.solidjs.com/?version=1.4.1#NobwRAdghgtgpmAXGGUCWEwBowBcCeADgsrgM4Ae2YZA9gK4BOAxiWGjIbY7gAQi9GcCABM4jXgF9eAM0a0YvAOR0ANmhEBaAFZkA9AHc4AIyUBuADoQOXHv17MhUXHADKaAObRVWXgDFuKVl5RRVadS1dcysrZloIMj4AfV4AXl4ACihGRih8RF4oCHwASjSAPkyBVEICjJkIAqLSit4AHgCJOChmAAtUkGzc-AySyXKQBsk2vU7KyRKYiBl6CGZcNHjeAEFCQlH+K14HeMTeYGZnMl8yOFwAYSuAXTSHJxd3LyhVDOAj4-sGgKSgAUppweh8AAvCAAcQAikpfNB4MCANJwfDGWjZES8R64JRSLD-Y4CIHKKFJbbGGQABQAGgAVNEwMhI3gouDAgCy2XoRMkJIgAMBImBAHkAKq4CAAZkIADcAOqcDwcrnAgASwkYaF4TN6cF4AFEKGhEsINt98c5Bf8niVLCLeP8hLgmCKMqT2vRVOUfWSkhlLuQSgA6GoZEPOJrFXxoOMtVIBl2i45tdSp9PptpQXi4bIeO6pCxgJLGVRFADWZd4vSEMgGAANerhcIQyIg9IYDAZw-gGB7jHBw3EYIZnH0APyK1IAEhAofDGkkzfGgZz-DQBwA1LwAIySApL5zhrmSTeimZQbNbmZZzdjH0zP13p1WS8QKxCUTiaNlCm7S7IQvB6OUvgiLQzD0PAEC4OGxa4CaqhwHBuAAEL4AAkiI3pgFAexliUACEH6YJITxAA)