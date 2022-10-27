---
title: Vite + React に Jest をセットアップする
date: 2022-08-10 12:00:17
updated: 2022-08-10 12:00:17
---

Vite + React に Jest をセットアップする覚え書。

<!-- more -->

## 環境

- Node.js 16.16.0
- npm 8.12.0
- React 18.2.0
- Vite 3.0.0

## TL;DR

```bash
npm install --save-dev jest babel-jest @babel/preset-env @babel/preset-react @testing-library/react
```

\_\_mocks\_\_/fileMock.js:

```javascript
module.exports = 'test-file-stub';
```

\_\_mocks\_\_/styleMock.js:

```javascript
module.exports = {};
```

babel.config.cjs:

```javascript
module.exports = {
  presets: [
    '@babel/preset-env',
    ['@babel/preset-react', {runtime: 'automatic'}],
  ],
};
```

jest.config.cjs:

```javascript
module.exports = {
  moduleNameMapper: {
    "\\.(jpg|jpeg|png|gif|eot|otf|webp|svg|ttf|woff|woff2|mp4|webm|wav|mp3|m4a|aac|oga)$":
      "<rootDir>/__mocks__/fileMock.js",
    "\\.(css|less)$": "<rootDir>/__mocks__/styleMock.js",
  },
  testEnvironment: "jsdom",
};
```

package.json:

```json
{
  ...
  "scripts": {
    ...
    "test": "jest"
  }
  ...
}
```

## ステップ バイ ステップ

### プロダクション コード

```bash
npm create vite@latest my-react-app -- --template react
```

### テスト コード

src/App.test.js:

```javascript
import { render, screen } from '@testing-library/react';
import App from './App';

test('renders learn react link', () => {
  render(<App />);
});
```

### Jest をインストール

```bash
npm install --save-dev jest
```

package.json:

```json
{
  ...
  "devDependencies": {
    ...
    "jest": "^28.1.3",
    ...
  }
  ...
}
```

### React Testing Library をインストール

```bash
npm install --save-dev @testing-library/react
```

package.json:

```json
{
  ...
  "devDependencies": {
    ...
    "@testing-library/react": "^13.3.0",
    ...
  }
  ...
}
```

### npm スクリプト

package.json ファイルの `scripts` プロパティーにテストを実行するためのスクリプトを追加する。

package.json:

```json
{
  ...
  "scripts": {
    ...
    "test": "jest"
  }
  ...
}
```

### `SyntaxError: /path/to/my-react-app/src/App.test.js: Support for the experimental syntax 'jsx' isn't currently enabled`

テストを実行する。

```bash
$ npm test
```

以下のエラーが表示される。

```bash
SyntaxError: /path/to/my-react-app/src/App.test.js: Support for the experimental syntax 'jsx' isn't currently enabled (5:10):

  3 |
  4 | test('renders learn react link', () => {
> 5 |   render(<App />);
    |          ^
  6 | });
  7 |

Add @babel/preset-react (https://github.com/babel/babel/tree/main/packages/babel-preset-react) to the 'presets' section of your Babel config to enable transformation.
If you want to leave it as-is, add @babel/plugin-syntax-jsx (https://github.com/babel/babel/tree/main/packages/babel-plugin-syntax-jsx) to the 'plugins' section to enable parsing.
```

Babel をインストールする。

```bash
npm install --save-dev babel-jest @babel/preset-env @babel/preset-react
```

package.json:

```json
{
  ...
  "devDependencies": {
    "@babel/preset-env": "^7.18.10",
    "@babel/preset-react": "^7.18.6",
    ...
    "babel-jest": "^28.1.3",
    ...
  }
  ...
}
```

`babel.config.cjs` ファイルを作成する。

babel.config.cjs:

```javascript
module.exports = {
  presets: [
    '@babel/preset-env',
    ['@babel/preset-react', {runtime: 'automatic'}],
  ],
};
```

https://jestjs.io/ja/docs/tutorial-react#create-react-app%E3%82%92%E4%BD%BF%E3%82%8F%E3%81%AA%E3%81%84%E3%82%BB%E3%83%83%E3%83%88%E3%82%A2%E3%83%83%E3%83%97

### `SyntaxError: Unexpected token '<'`

テストを実行する。

```bash
$ npm test
```

以下のエラーが表示される。

```bash
SyntaxError: Unexpected token '<'

  1 | import { useState } from 'react'
> 2 | import reactLogo from './assets/react.svg'
    | ^
  3 | import './App.css'
  4 |
  5 | function App() {
```

以下のファイルを作成する。

jest.config.cjs:

```javascript
module.exports = {
  moduleNameMapper: {
    "\\.(jpg|jpeg|png|gif|eot|otf|webp|svg|ttf|woff|woff2|mp4|webm|wav|mp3|m4a|aac|oga)$":
      "<rootDir>/__mocks__/fileMock.js",
  },
};
```

\_\_mocks\_\_/fileMock.js:

```javascript
module.exports = 'test-file-stub';
```

https://jestjs.io/ja/docs/webpack#%E9%9D%99%E7%9A%84%E3%82%A2%E3%82%BB%E3%83%83%E3%83%88%E3%81%AE%E7%AE%A1%E7%90%86

### `SyntaxError: Private field '#root' must be declared in an enclosing class`

テストを実行する。

```bash
$ npm test
```

以下のエラーが表示される。

```bash
SyntaxError: Private field '#root' must be declared in an enclosing class

  1 | import { useState } from 'react'
  2 | import reactLogo from './assets/react.svg'
> 3 | import './App.css'
    | ^
  4 |
  5 | function App() {
  6 |   const [count, setCount] = useState(0)
```

`jest.config.cjs` ファイルの `moduleNameMapper` プロパティーに以下の内容を追加する。

jest.config.cjs:

```javascript
module.exports = {
  moduleNameMapper: {
    ...
    "\\.(css|less)$": "<rootDir>/__mocks__/styleMock.js",
  },
};
```

`styleMock.js` ファイルを作成する。

\_\_mocks\_\_/styleMock.js:

```javascript
module.exports = {};
```

https://jestjs.io/ja/docs/webpack#%E9%9D%99%E7%9A%84%E3%82%A2%E3%82%BB%E3%83%83%E3%83%88%E3%81%AE%E7%AE%A1%E7%90%86

### `ReferenceError: document is not defined`

テストを実行する。

```bash
$ npm test
```

以下のエラーが表示される。

```bash
ReferenceError: document is not defined

  3 |
  4 | test('renders learn react link', () => {
> 5 |   render(<App />);
    |   ^
  6 | });
  7 |
```

`jest.config.cjs` ファイルに `testEnvironment` プロパティーを追加する。

jest.config.cjs:

```javascript
module.exports = {
  ...
  testEnvironment: "jsdom",
};
```

### `Validation Error`

テストを実行する。

```bash
$ npm test
```

以下のエラーが表示される。

```bash
● Validation Error:

  Test environment jest-environment-jsdom cannot be found. Make sure the testEnvironment configuration option points to an existing node module.

  Configuration Documentation:
  https://jestjs.io/docs/configuration


As of Jest 28 "jest-environment-jsdom" is no longer shipped by default, make sure to install it separately.
```

jest-environment-jsdom をインストールする。

```bash
npm install --save-dev jest-environment-jsdom
```

package.json:

```json
{
  ...
  "devDependencies": {
    ...
    "jest-environment-jsdom": "^28.1.3",
    ...
  }
  ...
}
```

### `PASS src/App.test.js`

テストを実行する。

```bash
$ npm test
```

以下のメッセージが表示される。

```bash
 PASS  src/App.test.js
  √ renders learn react link (26 ms)

Test Suites: 1 passed, 1 total
Tests:       1 passed, 1 total
Snapshots:   0 total
Time:        2.205 s
Ran all test suites.
```
