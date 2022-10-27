---
title: Hexo のメモ
date: 2022-04-09 00:50:09
updated: 2022-04-28 12:31:25
---

ブログを作成するための静的サイト ジェネレーターの [Hexo][1] の個人メモ。

随時更新。
<!-- more -->
## 環境

- Hexo 6.1.0
- [NexT][2] 8.x.x (テーマ)

## スタートアップ

### インストールとセットアップ

Node.js がインストールされていることを前提とする。

```
npm install hexo-cli -g
hexo init blog
cd blog
npm install
```

### 静的ファイルを生成

```
hexo generate
```

静的ファイルは `public` フォルダーに生成される。

### ローカルで確認

```
hexo server
```

`http://localhost:4000` にアクセスする。

## カスタマイズ

### ブログの構成を変更

`_config.yml` ファイルを変更する。

設定の内容は、「[Configuration | Hexo][3]」を参照。

### テーマの構成を変更

ブログのルート ディレクトリーに `_config.[テーマ].yml` (例えば、`_config.next.yml`) ファイルを作成して、そのファイルを変更する。

### パーマリンクから日付を削除

`_config.yml` ファイルの URL セクションの `permalink` から `:year/:month/:day/` を削除する。

`_config.yml`:

```yaml
permalink: :title/
```

### 「続きを読む」リンクを追加

記事に `<!-- more -->` を追加する。

例:

```markdown
---
title: Raspberry Pi に電源ボタンを付ける
date: 2020-12-01 23:22:04
updated: 2020-12-17 13:03:46
---

Raspberry Pi に電源ボタンを付けるサンプル。

OS が起動していない状態でボタンを押すと、OS を起動する。

OS が起動している状態でボタンを 3 秒間押し続けると、OS をシャットダウンする。
<!-- more -->
...
```

## NexT

### テーマを変更

Git がインストールされていることを前提とする。

```
git submodule add https://github.com/theme-next/hexo-theme-next themes/next
```

`_config.yml`:

```yaml
theme: next
```

### 編集日を非表示に

公開日と同じ日時の編集日 (Front Matter) を追加する。

例:

```yaml
---
title: Raspberry Pi をバックアップする
date: 2022-02-10 16:27:19
updated: 2022-02-10 16:27:19 # 追加
---
```

### すべてのページでサイドバーをデフォルトで表示

![sidebar-display.png](notes-on-hexo/sidebar-display.png)

`_config.next.yml`:

```yaml
sidebar:
  ...
  display: always
```

https://theme-next.js.org/docs/theme-settings/sidebar.html#Sidebar-Style

### アバター

![avatar.png](notes-on-hexo/avatar.png)

画像を `source\images` に配置して、`_config.next.yml` ファイルの avatar セクションを変更する。

例:

```yaml
avatar:
  # Replace the default image and set the url here.
  url: /images/avatar.jpg
  # If true, the avatar will be dispalyed in circle.
  rounded: true
  # If true, the avatar will be rotated with the cursor.
  rotated: false
```

https://theme-next.js.org/docs/theme-settings/sidebar.html#Configuring-Avatar

### ソーシャル リンク

![social.png](notes-on-hexo/social.png)

`_config.next.yml` ファイルの social セクションを変更する。

例:

```yaml
social:
  GitHub: https://github.com/AsaiToshiya || fab fa-github
  E-Mail: mailto:to.asai.60@gmail.com || fa fa-envelope
  #Weibo: https://weibo.com/yourname || fab fa-weibo
  #Google: https://plus.google.com/yourname || fab fa-google
  Twitter: https://twitter.com/5891_iasa_ot || fab fa-twitter
  #FB Page: https://www.facebook.com/yourname || fab fa-facebook
  #StackOverflow: https://stackoverflow.com/yourname || fab fa-stack-overflow
  #YouTube: https://youtube.com/yourname || fab fa-youtube
  #Instagram: https://instagram.com/yourname || fab fa-instagram
  #Skype: skype:yourname?call|chat || fab fa-skype
```

https://theme-next.js.org/docs/theme-settings/sidebar.html#Sidebar-Social-Links

### RSS

![social.png](notes-on-hexo/rss.png)

1. [hexo-generator-feed][4] をインストールする。

   ```
   npm install hexo-generator-feed --save
   ```

2. `_config.next.yml` ファイルの social セクションに `RSS` を追加する。

   例:

   ```yaml
   social:
     ...
     RSS: /atom.xml || fa fa-rss
   ```

### 目次

![toc.png](notes-on-hexo/toc.png)

`_config.next.yml` ファイルの toc セクションを変更する。

例:

```yaml
toc:
  enable: true
  # Automatically add list number to toc.
  number: false
  # If true, all words will placed on next lines if header width longer then sidebar width.
  wrap: false
  # If true, all level of TOC in a post will be displayed, rather than the activated part of it.
  expand_all: true
  # Maximum heading depth of generated toc.
  max_depth: 6
```

https://theme-next.js.org/docs/theme-settings/sidebar.html#Sidebar-TOC

### サイドバーに「最近の投稿」を追加

![recent-posts.png](notes-on-hexo/recent-posts.png)

1. `source/_data` に `sidebar.njk` ファイルを作成する。

   sidebar.njk:

   ```njk
   <!-- recent posts -->
   {%- if theme.recent_posts %}
     <div class="links-of-blogroll motion-element {{ "links-of-blogroll-" + theme.recent_posts_layout }}">
       <div class="links-of-blogroll-title recent-posts-title">
         <i class="fa fa-history {{ theme.recent_posts_icon | lower }}" aria-hidden="true"></i>
         {{ theme.recent_posts_title }}
       </div>
       <ul class="links-of-blogroll-list recent-posts-list">
         {%- set posts = site.posts.sort('-date').toArray() %}
         {%- for post in posts.slice('0', '5') %}
           <li class="links-of-blogroll-item">
             <a href="{{ url_for(post.path) }}" title="{{ post.title }}" target="">
               {{ post.title }}
             </a>
           </li>
         {%- endfor %}
       </ul>
     </div>
   {%- endif %}
   ```

2. `_config.next.yml` ファイルに以下の内容を追加する。

   _config.next.yml:

   ```yaml
   recent_posts: true
   recent_posts_title: 最近の投稿
   recent_posts_layout: block
   ```

参考: [Hexo NexT v8.x.x - Add recent posts | Egbert Lin's Blog][7]

### サイドバーにリンクを追加

![links.png](notes-on-hexo/links.png)

`_config.next.yml` ファイルの links_settings セクションと links セクションを変更する。

例:

```yaml
links_settings:
  icon: fa fa-sticky-note
  title: メモ
  # Available values: block | inline
  layout: block

links:
  Raspberry Pi のメモ: /notes-on-raspberry-pi
  Linux のメモ: /notes-on-linux
  電子部品のメモ: /notes-on-electronic-components
  Hexo のメモ: /notes-on-hexo
```

https://theme-next.js.org/docs/theme-settings/sidebar.html#Sidebar-Blogrolls

## NexT (スタイル)

`source/_data` に `styles.styl` ファイルを作成して、`_config.next.yml` ファイルの custom_file_path セクションの `style` のコメントアウトを外す。

_config.next.yml:

```yaml
custom_file_path:
  ...
  style: source/_data/styles.styl
```

### ソーシャル リンクのアイコンの前の丸 (●) を非表示に

![hide-circle-in-social-links.png](notes-on-hexo/hide-circle-in-social-links.png)

styles.styl:

```stylus
.links-of-author a::before {
  content: none;
}
```

### ページの上部にある黒い線を非表示に

![hide-headband.png](notes-on-hexo/hide-headband.png)

styles.styl:

```stylus
.headband {
  display: none;
}
```

### アーカイブ ページの「もっと書こう！」を非表示に

![hide-keep-on-posting.png](notes-on-hexo/hide-keep-on-posting.png)

styles.styl:

```stylus
.archive .collection-title {
  display: none !important;
}
```

https://theme-next.js.org/docs/advanced-settings/custom-files#Hide-quot-Keep-on-posting-quot-in-Archive-Page

### 見出しに罫線を追加

![underline-header.png](notes-on-hexo/underline-header.png)

styles.styl:
  
```stylus
.post h2 {
  border-bottom: 1px solid var(--text-color);
}
```

### メニューを非表示に

![hide-menu.png](notes-on-hexo/hide-menu.png)

styles.styl:
  
```stylus
.site-nav-toggle, .site-nav-right, .site-nav {
  display: none;
}
```

### モバイルでサイドバーを表示

<img src="/notes-on-hexo/show-sidebar-on-mobile-1.png" width="49%" style="display: inline"/>
<img src="/notes-on-hexo/show-sidebar-on-mobile-2.png" width="49%" style="display: inline"/>

styles.styl:
  
```stylus
.sidebar-toggle {
  display: inline;
}

.sidebar {
  display: inline;
}
```

### ブログ タイトルの下側のパディングを設定

![header-padding-bottom.png](notes-on-hexo/header-padding-bottom.png)

styles.styl:

```stylus
.header-inner {
  padding-bottom: 100px;

  +mobile() {
    padding-bottom: 50px;
  }
}
```

## Tips

### GitPress の記事を移行

1. 記事 (Markdown ファイル) を `source\_posts` に移動する。

2. 画像を `source` に移動する。

3. 記事にタイトルと公開日 (Front Matter) を追加する。

   例:

   ```yaml
   ---
   title: Raspberry Pi をバックアップする
   date: 2022-02-10 16:27:19
   ---
   ```

4. 記事の冒頭の、最初の見出しレベル 1 (`#`) を削除する。

### Vercel でホスティング

「[Vercel で静的サイトをホスティングする][5]」を参照。

### Android で Hexo

「[Android で Hexo][6]」を参照。

[1]: https://hexo.io/
[2]: https://theme-next.js.org/
[3]: https://hexo.io/docs/configuration.html
[4]: https://github.com/hexojs/hexo-generator-feed
[5]: /hosting-static-site-with-vercel
[6]: /hexo-in-android
[7]: https://egbert-yu-ting.github.io/posts/68394953/
