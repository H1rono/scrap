# Obsidian HTMLにPR出したい

tags: #obsidian-html #github

[[obsidian-html#気になったとこ/TODO]]あたりの内容

- タグの始まりがemojiだとタグとして認識されない
- `rss:managing_editor`に`<>`を使ったらXMLと干渉する

このへんとりあえずissue探しからやりたい

## とりあえずsandbox作る

検証のために[リポジトリ](https://github.com/obsidian-html/obsidian-html)のmasterからインストールしておく

```
$ pip install git+https://github.com/obsidian-html/obsidian-html.git
```

sandboxのフォルダ作成

```bash
$ cd どこか適当な場所
$ mkdir obsidian-html-dev
$ code obsidian-html-dev
```

[[gha-scrap|GitHub Actionsで使う]]時に`.obsidian`はフォルダとして存在してさえいればいいことがわかったのでVSCodeで開く

config生成

```bash
$ obisidanhtml export default-config -o config.yml
```

ちょっといじる 以下diffだけ

```diff
- obsidian_folder_path_str: '<DEPRECATED>'
+ # obsidian_folder_path_str: '<DEPRECATED>'

- obsidian_entrypoint_path_str: '<REQUIRED_INPUT>'
+ obsidian_entrypoint_path_str: "index.md"

- no_tabs: '<REMOVED>'
+ # no_tabs: "<REMOVED>"
```

entrypointタッチしてからconvert

```bash
$ touch index.md
$ obsidianhtml convert -i config.yml
```

v4から`obsidianhtml run`でserveができなくなったようなので↓

```bash
$ python -m http.server -d output/html 8080
```

## タグの始まりがemojiだとタグとして認識されない

non-asciiだといけない？要検証

---

index.md↓

```md
# index

##📝

#タグ

    #?-tag
```

結果: 全て`h1`として認識された
ちなみにobsidian本家だと↓

![[obsidian-tag-test.png]]

問題点は3つかな

- `#`の次にnon-ASCIIな文字が続くとtagとして認識されない
- 空白をstripした後の行頭に`#`があってtagでなければ`hn`になる
- 空白をstripするので、インデントでコードブロックにならない

## `rss:managing_editor`に`<>`を使ったらXMLと干渉する
