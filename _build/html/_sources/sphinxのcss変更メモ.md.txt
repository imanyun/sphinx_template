# SphinxのCSSを変更する方法

## Sphinxのテーマ

sphinx_rtd_theme

## 変更箇所

- teach4meカラーになるようにCSSを一部変更しました。
- テキスト部分の右側余白を無くしました。
- ファビコンの画像を追加方法を記載します。（今回はロゴ画像が見当たらなかったためやっていません。）

### conf.py

ファイルの階層

- プロジェクトディレクトリ名/conf.py

以下を追加しました。

```conf.py
def setup(app):
（省略）
    app.add_transform(AutoStructify)
    # ↓追記
    app.add_stylesheet('custom.css')
```

```conf.py
html_static_path = ['_static']
# ↓追記（CSS読み込み→画像は「_static/css」に保存）
html_style = "css/my_theme.css"
# ↓追記（ファビコン読み込み→画像は「_static」に保存）
html_favicon = "about_bg.png"
```

### ファビコンの画像ファイルの保存先

- プロジェクトディレクトリ名/_build/html/_static/logo.png

### custom.css

以下のファイルの階層にcustom.cssを作成します。

- プロジェクトディレクトリ名/_build/html/_static/custom.css

以下を追加しました。

```custom.css
@import url("theme.css");

/* テキスト部分の幅（余白をなくす） */
.wy-nav-content {
    max-width: none;
}
/* .wy-nav-content {
  max-width: 1200px !important;
} */

/* 検索バーの部分の色の変更 */
.wy-side-nav-search {
  /* background: linear-gradient(-45deg, rgb(254, 102, 125), rgb(255, 163, 117)); */
  /* background: -webkit-linear-gradient(left, #fb8c01, #fe3000); */
  background: -webkit-linear-gradient(left, #fe3000, #fb8c01);
}

h1,h2,h3,h4,h5,h6 {
    border-bottom: 1px solid #ccc;
}

.wy-table-responsive table td, .wy-table-responsive table th {
    white-space: normal;
}

colgroup {
    display: none;
}

/* 画面幅を縮めた時にヘッダー部分の色の変更 */
@media screen and (max-width: 768px) {
  .wy-nav-top {
      display: block;
      background: -webkit-linear-gradient(left, #fe3000, #fb8c01);
  }
}
```

### my_theme.css

以下のファイルの階層にcustom.cssを作成します。

- プロジェクトディレクトリ名/_build/html/_static/css/my_theme.css

以下を追加しました。（custom.cssと同じです。）

```my_theme.css
@import url("theme.css");

/* テキスト部分の幅（余白をなくす） */
.wy-nav-content {
    max-width: none;
}
/* .wy-nav-content {
  max-width: 1200px !important;
} */

/* 検索バーの部分の色の変更 */
.wy-side-nav-search {
  /* background: linear-gradient(-45deg, rgb(254, 102, 125), rgb(255, 163, 117)); */
  /* background: -webkit-linear-gradient(left, #fb8c01, #fe3000); */
  background: -webkit-linear-gradient(left, #fe3000, #fb8c01);
}

h1,h2,h3,h4,h5,h6 {
    border-bottom: 1px solid #ccc;
}

.wy-table-responsive table td, .wy-table-responsive table th {
    white-space: normal;
}

colgroup {
    display: none;
}

/* 画面幅を縮めた時にヘッダー部分の色の変更 */
@media screen and (max-width: 768px) {
  .wy-nav-top {
      display: block;
      background: -webkit-linear-gradient(left, #fe3000, #fb8c01);
  }
}
```

## 参考URL

[custom.cssについて](https://stackoverflow.com/questions/23211695/modifying-content-width-of-the-sphinx-theme-read-the-docs)
[my_theme.cssについて](http://kuttsun.blogspot.com/2016/11/sphinx-sphinxrtdtheme.html)

[CSSカラー](https://gradienthunt.com/gradient/429)

[ちょっとだけ参考にした](https://stackoverflow.com/questions/44793811/change-the-colors-of-the-sphinx-read-the-docs-theme)

[ファビコン挿入について](http://candyhouse.black/confpy.html)