---
title: "SolidJS: 強制的にコンポーネントを再描画する"
date: 2022-10-28 00:41:19
updated: 2022-10-28 00:41:19
tags: [SolidJS]
---

![logo.svg](solidjs-force-component-to-rerender/logo.svg)

[SolidJS](https://www.solidjs.com) で強制的にコンポーネントを再描画する方法。

Signal の値をキーとして使用して、キーを変更することにより、コンポーネントを再描画する。

ここでは、「再描画」ボタンをクリックしたときに、1 秒ごとにカウントをインクリメントする以下の `CountingComponent` コンポーネントを再描画する。

CountingComponent.jsx:

```javascript
import { createSignal, onCleanup } from "solid-js";

const CountingComponent = () => {
  const [count, setCount] = createSignal(0);
  const interval = setInterval(
    () => setCount(c => c + 1),
    1000
  );
  onCleanup(() => clearInterval(interval));
  return <div>Count value is {count()}</div>;
};

export default CountingComponent;
```

<!-- more -->
## 環境

- SolidJS 1.5.1


## 方法 1: [`For`](https://www.solidjs.com/tutorial/flow_for) コンポーネントを使用する

App.jsx:

```javascript
import { createSignal, For } from "solid-js";
import CountingComponent from "./CountingComponent";

const App = () => {
  const [key, setKey] = createSignal([{}]);
  const rerender = () => setKey([{}]);

  return (
    <>
      <For each={key()}>{() => <CountingComponent />}</For>
      <button type="button" onClick={rerender}>
        再描画
      </button>
    </>
  );
};

export default App;
```

[Solid Playground](https://playground.solidjs.com/?version=1.4.1#NobwRAdghgtgpmAXGGUCWEwBowBcCeADgsrgM4Ae2YZA9gK4BOAxiWGjIbY7gAQi9GcCABM4jXgF9eAM0a0YvADo1aAGzQiAtACsyAegDucAEYqA3EogcuPfr2ZCouOAGU0Ac2hqsvWhABhNTgoCHpCXwAxbilZeUUVOg1tPQsrK2Z-Mj4AhghcDA9czn9hPgBeXgAKAEpecoA+fiteByy+YEz6fN8yOFxc7twAXXqHJxd3Lyg1KoAGGssIVsyIbN4MF0YANxmxvtwASXzxXdmW1uq6xt4Dwfyq5nqmp4BqXgBGGqwL1o+5gEXRYXfxBEJhQhVWrPBzBKCMY5bM5VTanGY1YHLQT9JjLAA8IjQ2wa9z4Z3ocA2ZH4XQeNUkeP0hOJS0kSwy7V4AEFCIQxtCbiALqt1sAANZwfC9foAaUlo0qjhCk083iqoEkw0xK05QiEonE-OuTQOcvw6pAmsxFyEuFx1V+vDxDUdrTx0QkIWYAAtyiAJeb6Q0QAKmnjSYVilwIGVePoGgz9B6XVjLk6TPRcLh-LwCMRyioM1n-Co-IENMwxX69cIxIxJCm02nALGKgHnjQDcrq6nfoi9mII3LoyB5i2ekIPq61DjU6eXz474RLRmPR4PkAHQefoAUWCq9wACF8IcRFUVFBeSoagBCTFgTVAA)

キーは、項目が 1 つの配列である必要がある。


## 方法 2: `For` コンポーネントをラップしたコンポーネントを使用する

`For` コンポーネントをラップした `Key` コンポーネントを使用する。

Key.jsx:

```javascript
import { createMemo, For } from "solid-js";

const Key = (props) => {
  const key = createMemo(() => [props.is()]);
  const fn = props.children;
  return <For each={key()}>{fn}</For>;
};

export default Key;
```

App.jsx:

```javascript
import { createSignal } from "solid-js";
import CountingComponent from "./CountingComponent";
import Key from "./Key";

const App = () => {
  const [key, setKey] = createSignal({});
  const rerender = () => setKey({});

  return (
    <>
      <Key is={key}>{() => <CountingComponent />}</Key>
      <button type="button" onClick={rerender}>
        再描画
      </button>
    </>
  );
};

export default App;
```

[Solid Playground](https://playground.solidjs.com/?version=1.4.1#NobwRAdghgtgpmAXGGUCWEwBowBcCeADgsrgM4Ae2YZA9gK4BOAxiWGjIbY7gAQi9GcCABM4jXgF9eAM0a0YvADo1aAGzQiAtACsyAegDucAEYqA3EogcuPfr2ZCouOAGU0Ac2hqsDpy4BZOBhaX1oIAGE1OCgIekJfADFuKVl5RRU6DW09CysrZnCyPgiGCFwMD1LOcOE+AF5eAAoASl56gD5+K14HIr5gQvpy3zI4XFLh3ABddr8Yl3cvKDUmgAYWywhewohi3gwXRgA3Fbmx3ABJcvFT1Z7e5rbO3gvJ8qbmdq6vgGpeACMLSwD16ALWEIemwe4SiMTihCarW+DmiUEY1yOdyah1uKxa0O2gnGTG2AB4RGhjh13nw7vQ4AcyPwhh8WpIyfpKdStpItgV+rwANJwfBzJqEeSEMiIXixfDPLogB67fYAa1Fc0cCzgQRCSMVvGAkto0oAdGgyK1poSdoKZNtGibzcwABZoNQiIQQLa9IS4Um8MnJCQxN31EAa-CtSQdEAOjn6EMdXn8iCqvgAQUIhHFhuVRIzRqjo3GIvws0a2ucbk83iaIEktr6ez4Qm9YgkjWRLwu5YbTbTfpJjG2TVBQY6E96ZPLTIjUdjIB7XTJtMq1S4EDqvH0HUT5anRMeQZM9FwuHCvAIxHqKjPF-CKl4sI0zDVEfbwk7senj0AsYqAPPGgDcrn+nIPpeEBHienLQbwhJ8vkEAduIBoomS2a5nuvgiLQzD0PA5Rmh44wAKLRIRuAAEL4JcIjjmAUA5ioLQAISEmAkjTEAA)


## 方法 3: 独自のコンポーネントを使用する

`For` コンポーネントを使用しない独自の `Key` コンポーネントを使用する。

`App.jsx` は方法 2 と同じ。

Key.jsx:

```javascript
import { createRoot, createMemo, onCleanup, on } from "solid-js";

const Key = (props) => {
  const key = props.is;
  const fn = props.children;
  let disposer;
  onCleanup(() => disposer && disposer());

  return createMemo(
    on(key, () => {
      disposer && disposer();
      return createRoot((dispose) => {
        disposer = dispose;
        return fn();
      });
    })
  );
};

export default Key;
```

[Solid Playground](https://playground.solidjs.com/?version=1.4.1#NobwRAdghgtgpmAXGGUCWEwBowBcCeADgsrgM4Ae2YZA9gK4BOAxiWGjIbY7gAQi9GcCABM4jXgF9eAM0a0YvADo1aAGzQiAtACsyAegDucAEYqA3EogcuPfr2ZCouOACVatXFgdOXAZTQAc2g1b0c4ZzgAWTgYWm9aCABhNQiIekIEiClZeUUVOg1tPQsrK2ZEsj4khghcDECazkThPgBeXgAKAEpeNoA+fiteB0q+YAr6Ou8yOFwaqdwAXT6fCP8gkM6ABm7LbNGIKt4MF0YANyg1VdncAEk68Uu1TuGRrt6B3luFus7mPqDAEAal4AEZulg3iMwds4W89m9Eik0hlOj1AQ5UlBGA8zs9OqcnlduoiDkJcExsgAeERoc79X58Z70OAnMj8SZ-bqSan6OkM-aSfblMa8ADScHwq06hHkhDIiF4UAg+E+gxAbwqRz4AGspas5bQFQA6NBkfYjbXHGTZDpG03MAAWaDUIiEEEtvFSfDpZC4s0YSpV+C9yOx6UI6PVvD9AfEvAAZInY+b44wemS3hSqWtIjE4q8DiNEp19fhvBivpri+847RA0mU-XAz0ve9BHNc+FIu5POiW3AYzWOx3BxIOoP26Oc4xsra29D3pIyR2VwihSKINa+ABBQiEGXDrVi4DlmZzSX4FYdHsbYJXTogFdenedj1iCcfTG3K9Pl9lOSXZzl0S7Uv0S4jNSV7sm0IDlpI-QgFWgzUkyDRNFwECtLw+j9Ly+hXhBtZQSY9C4LgiS8AQxBtCoZEUYkKi8OGaDMLqcFCB+4iIZB7yALGKgDzxoA3K58XyDGURAxEdny0m8GSwqAdxGYobw1L7oeeHeCItDMPQ8B1CagRzAAoqkBm4AAQvgdwiK8YBQAeKjdAAhGSYCSEsQA)