# README

## ライブラリのインストール

`Sphinx` をはじめとした必要なライブラリをインストール

```bash
pip install sphinx
pip install commonmark
pip install recommonmark
pip install nbsphinx
pip install sphinx_rtd_theme
```

## 資料作成

```
.
├── Makefile
├── README.md
├── _build
│   ├── doctrees
│   └── html
├── conf.py
├── index.rst
├── make.bat
└── src
    ├── 1.md
    ├── 2.ipynb
    ├── 3.ipynb
    └── 4.md
```

### 資料の設定

資料に関する設定は`conf.py`に記述します。

変更するであろう主な部分は以下くらいです。

```python
project = 'プロジェクト名'
copyright = '2018, 会社名'
author = '会社名'
```

また、Sphinxのテーマは以下に設定していますが、こちらはお好きなものに変更していただければと思います。必要に応じて、テーマをインストールしてください。テーマ一覧は最下部の**参考URL**を御覧ください。

```python
html_theme = "sphinx_rtd_theme"
```

### 資料の構成を定義

`index.rst`内の以下に構成を定義します。

```reStructuredText
====================================

.. toctree::
   :maxdepth: 2
   :caption: Contents:
   :glob:

   src/1
   src/2
   src/3

====================================
```

重要なのは以下の部分になります。

```reStructuredText
   src/1
   src/2
   src/3
```

こちらがファイルの読み込み先を示しています。`src` フォルダの`1`というファイルを読み込んでいます。
基本的に`.md`or `.ipynb`の拡張子であれば読み込んでくれます。

## ビルド

作業ディレクトリにて

```bash
make html
```

`_build > html`フォルダの中の`index.html`を開けばOKです。

```bash
cd _build/html
open index.html
```

## 備考

### PDF作成

作業ディレクトリに移ってから下記のコマンドで`_build`以下にpdfができます

```
docker run --rm -it -v ${PWD}:/docs/ kikagaku/sphinx
```

### 参考URL

- Sphinxを便利にして、みんなに使ってもらいたい
   https://qiita.com/pashango2/items/d1b379b699af85b529ce
- Sphinxテーマ一覧
  https://sphinx-themes.org/







