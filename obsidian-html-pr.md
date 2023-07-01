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

ちょっといじる

```diff

```

## タグの始まりがemojiだとタグとして認識されない

non-asciiだといけない？要検証

## `rss:managing_editor`に`<>`を使ったらXMLと干渉する
