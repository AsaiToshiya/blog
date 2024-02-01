---
title: Git コマンドのチート シート
date: 2022-11-12 00:04:08
updated: 2024-02-01 19:12:48
tags: [Git]
---
<p></p>

<!-- more -->
## HEAD とインデックスを比較

```bash
git diff --staged
```

## コミット (複数行のメッセージ)

```bash
git commit -F- <<EOF
タイトル

説明
EOF
```

## ファイルをインデックスに追加 (ステージング)

```bash
git add <ファイル>
```

## `main` をリモート リポジトリにプッシュ

```bash
git push origin main
```

## リモート リポジトリからプル

```bash
git pull
```

## HEAD と作業ツリーを比較

```bash
git diff
```

## コミット ログを表示

```bash
git log --pretty=short
```

例:

```bash
$ git log --pretty=short
commit c46978e00eb221f4cd0bda32ce638b444cc11476 (HEAD -> main)
Author: Asai Toshiya <to.asai.60@gmail.com>

    Ant Design の依存関係を更新する

commit db4242a027cf5f0dd419970b94097f67cb95e7cb
Merge: 1f4da56 3f4553a
Author: Asai Toshiya <to.asai.60@gmail.com>

    Merge pull request #81 from AsaiToshiya/dependabot/npm_and_yarn/vitejs/plugin-react-2.2.0

commit 1f4da568c06cf90cb891c303d4aa0e62ce9ea5eb
Merge: 99e3dc5 71f2464
Author: Asai Toshiya <to.asai.60@gmail.com>

    Merge pull request #84 from AsaiToshiya/dependabot/npm_and_yarn/vite-3.2.2

commit 71f24649dbb75e1683f9ea3c529e59364945e8de
Author: dependabot[bot] <49699333+dependabot[bot]@users.noreply.github.com>

    Bump vite from 3.1.3 to 3.2.2

commit 3f4553a6632b06a287f724fe3dc13c07cc709915
Author: dependabot[bot] <49699333+dependabot[bot]@users.noreply.github.com>

    Bump @vitejs/plugin-react from 2.1.0 to 2.2.0

commit 99e3dc5641ce71caebf90ae917751ab6d75ff978
Merge: f863f36 62691d2
:
```

## HEAD とインデックスを比較 (ファイル名のみ)

```bash
git diff --name-only --staged
```

## コミット ログを表示 (グラフ、一行)

```bash
git log --graph --pretty=oneline
```

例:

```bash
$ git log --graph --pretty=oneline
* c46978e00eb221f4cd0bda32ce638b444cc11476 (HEAD -> main) Ant Design の依存関係を更新する
*   db4242a027cf5f0dd419970b94097f67cb95e7cb Merge pull request #81 from AsaiToshiya/dependabot/npm_and_yarn/vitejs/plugin-react-2.2.0
|\
| * 3f4553a6632b06a287f724fe3dc13c07cc709915 Bump @vitejs/plugin-react from 2.1.0 to 2.2.0
* |   1f4da568c06cf90cb891c303d4aa0e62ce9ea5eb Merge pull request #84 from AsaiToshiya/dependabot/npm_and_yarn/vite-3.2.2
|\ \
| |/
|/|
| * 71f24649dbb75e1683f9ea3c529e59364945e8de Bump vite from 3.1.3 to 3.2.2
|/
*   99e3dc5641ce71caebf90ae917751ab6d75ff978 Merge pull request #80 from AsaiToshiya/dependabot/npm_and_yarn/eslint-8.26.0
|\
| * 62691d2ae9e197d2388c42f81786ac4192993ec4 Bump eslint from 8.25.0 to 8.26.0
|/
*   f863f362e85f141eee84ec7c17272a785868611e Merge pull request #79 from AsaiToshiya/dependabot/npm_and_yarn/eslint-8.25.0
|\
| * 40b85938191568604481f11212e2a10d9f2290bf Bump eslint from 8.24.0 to 8.25.0
|/
* 62565dc160e0780dfa487991c06feb9c3091101e いくつかのコメントを削除する
* b4be0c97194ea8cc4b02eb1ad31c6d0deb2d8f4e コメントを変更する
* 8b58bb3f5d4b43ab42101df3264719f38f67a68e いくつかの空行を削除する
*   83a9149121fa055987e5c3c3ac4191a46df84c22 Merge pull request #78 from AsaiToshiya/dependabot/npm_and_yarn/eslint-8.24.0
|\
| * 8b2967e0f5464c97430d9362463fe838dab0d285 Bump eslint from 8.23.1 to 8.24.0
:
```

## コミット

```bash
git commit -m "<メッセージ>"
```

## 最新のコミット ログを表示

```bash
git log -p -1
```

例:

```bash
$ git log -p -1
commit c46978e00eb221f4cd0bda32ce638b444cc11476 (HEAD -> main)
Author: Asai Toshiya <to.asai.60@gmail.com>
Date:   Sat Nov 5 03:09:20 2022 +0900

    Ant Design の依存関係を更新する

diff --git a/package-lock.json b/package-lock.json
index 73acb3a..420e736 100644
--- a/package-lock.json
+++ b/package-lock.json
@@ -9,7 +9,7 @@
       "version": "0.0.0",
       "dependencies": {
         "@ant-design/icons": "^4.7.0",
-        "antd": "^4.23.2",
+        "antd": "^4.24.1",
         "react": "^18.2.0",
         "react-dom": "^18.2.0"
       },
@@ -704,6 +704,23 @@
         "node": ">= 8"
       }
     },
+    "node_modules/@rc-component/portal": {
+      "version": "1.0.1",
+      "resolved": "https://registry.npmjs.org/@rc-component/portal/-/portal-1.0.1.tgz",
+      "integrity": "sha512-aIxMEupUXhVARDSeRgiAuYA8K9VR1a6emLt9a2RpujMX5aRrtMES3rdMQOjBcD9eb64fzdCYt4/NrjmKk5r5vQ==",
+      "dependencies": {
+        "@babel/runtime": "^7.18.0",
:
```

## HEAD と作業ツリーを比較 (ファイル名のみ)

```bash
git diff --name-only
```

## コミットを打ち消す

```bash
git revert <コミット ID> --no-edit
```

## サブモジュールの初期化と取得

```bash
git submodule update --init --recursive
```

## ファイルの変更を破棄

```bash
git checkout <ファイル>
```

## カレント ディレクトリー配下のすべてのファイルをインデックスに追加

```bash
git add .
```

## サブモジュールを追加

```bash
git submodule add <URL>
```

## コミット メッセージを変更

```bash
git commit --amend -m "<メッセージ>"
```

## サブモジュールを更新

```bash
git submodule update --remote
```

## リモート リポジトリを追加

```bash
git remote add origin <URL>
```

## リモート リポジトリからフェッチ

```bash
git fetch
```

## インデックスと作業ツリーを `origin/main` にリセット

```bash
git reset --hard origin/main
```

## リモート リポジトリからフェッチしてリベース

```bash
git pull --rebase
```

## ファイルの名前を変更

```bash
git mv <ファイル> <新しいファイル名>
```

## タグを作成

```bash
git tag <タグ名>
```

## すべてのタグをプッシュ

```bash
git push origin --tags
```

## 最後のコミットを取り消す

```bash
git reset --soft HEAD^
```

注: 作業ツリーとインデックスの変更はそのまま残る。

## ベア リポジトリをクローン

```bash
git clone --bare <URL>
```

`git push --mirror` と組み合わせてリポジトリを複製できる。

参考: [Duplicating a repository - GitHub Docs](https://docs.github.com/ja/repositories/creating-and-managing-repositories/duplicating-a-repository)

## ミラー プッシュ

```bash
git push --mirror <URL>
```

`git clone --bare` と組み合わせてリポジトリを複製できる。

参考: [Duplicating a repository - GitHub Docs](https://docs.github.com/ja/repositories/creating-and-managing-repositories/duplicating-a-repository)

## ファイルをインデックスから削除 (アンステージング)

```bash
git reset <ファイル>
```

## フォークした上流のリモート リポジトリを追加

```bash
git remote add upstream <URL>
```

## すべてのファイルをインデックスから削除 (アンステージング)

```bash
git restore --staged .
```

## 最後のコミットのコミッター日付 (CommitterDate) を作者日付 (AuthorDate) に変更

```bash
git rebase HEAD~1 --committer-date-is-author-date
```

## チェリーピックを中止

```bash
git cherry-pick --abort
```

## スタッシュのリストを表示

```bash
git stash list
```

## 最新のスタッシュを適用して削除

```bash
git stash pop
```

## ファイルの一部をインデックスに追加

```bash
git add -p
```

コマンドを実行すると対話モードに入る。

```bash
diff --git a/src/index.html b/src/index.html
index 122d41c..4ef223e 100644
--- a/src/index.html
+++ b/src/index.html
@@ -1,4 +1,4 @@
-<!DOCTYPE html>
+<!doctype html>
 <html style="height: 100%; margin: 0; padding: 0; width: 100%">
   <head>
     <link
(1/5) Stage this hunk [y,n,q,a,d,j,J,g,/,e,?]?
```

インデックスに追加する場合は `y`、スキップする場合は `n`。

## サブモジュールを含めてクローン

```bash
git clone --recursive <URL>
```

## 特定のディレクトリーのみクローン (スパース チェックアウト)

```bash
git clone --filter=blob:none --no-checkout --sparse <URL>
cd <リポジトリ>
git sparse-checkout set <ディレクトリー>
git checkout <ブランチ>
```
