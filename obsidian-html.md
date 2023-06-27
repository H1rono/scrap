---
rss:
  publish_date: 2023-06-25
---

# obsidian-html使った

repo: [obsidian-html/obsidian-html: Python code to convert Obsidian notes to proper markdown and optionally to create an html site too.](https://github.com/obsidian-html/obsidian-html)
docs: [ObsidianHtml/Documentation](https://obsidian-html.github.io/index.html)

tags: #obsidian-html #obsidian

## Quickstart読む

[QuickStart - ObsidianHtml/Documentation](https://obsidian-html.github.io/instructions/quickstart.html)

`pip install obsidianhtml`で入れる
将来的にGitHub Actionsで使うはずなのでとりあえずはこれで

Usage↓

- indexのmdファイルを指定してビルド: `obsidianhtml run -f index.md`
    - サブコマンド`run`はbuild + serve(localhost:8888)
- config(YAML)ファイルを指定してbuild: `obsidianhtml convert -i config.yml`
    - サブコマンド`convert`はbuildのみ

完全理解したのでconfigを見る

## Config

[Configuration Options - ObsidianHtml/Documentation](https://obsidian-html.github.io/configurations/configuration-options.html)

デフォルトのconfigは`obsidianhtml export default-config`で見られる

めちゃくちゃでかいので大事そうなとこだけ抜き出す(値はこのリポジトリの設定)

```yml
# 後述の`obsidian_entrypoint_path_str`を手掛かりに推測されるらしい
obsidian_folder_path_str: "<DEPRECATED>"

# indexのpath
obsidian_entrypoint_path_str: "./README.md"

# ページの左上(多分)に出るやつ、document.titleもこの値っぽい
site_name: "H1rono/scrap"

# 配信する際のルートパス
html_url_prefix: "/scrap"

# favicon設定
file_exports:
  - encoding: binary
    src: assets/favicon.ico
    dst: favicon.ico

# これデフォルトだとコメントアウトされてなくてエラーになる
# no_tabs: "<REMOVED>"

# rss配信の設定
    rss:
      enabled: True
      host_root: "https://h1rono.github.io/scrap"
      styling:
        show_icon: True
      channel:
        title: "H1rono/scrap"
        website_link: "https://h1rono.github.io/scrap"
        description: "Obsidianメモ置き場"
        language_code: "ja-jp"
        managing_editor: "H1rono <hronok66@gmail.com>"
        web_master: "H1rono <hronok66@gmail.com>"
      items:
        selector:
          match_keys: []
          exclude_keys: []
          include_subfolders: []
          exclude_subfolders: [".git", "obs.html"]
          exclude_files: ["not_created.html"]
        description:
          selectors:
            - ["yaml", "rss:description"]
            - ["first-paragraphs", 2, "<br/><br/>"]
            - ["first-header", 1]
        title:
          selectors:
            - ["yaml", "rss:title"]
            - ["first-header", 1]
            - ["path", ["parent", 1], "/", ["stem"]]
        publish_date:
          selectors:
            - ["yaml", "rss:publish_date"]
            - ["yaml_strip", "tags", ["date/"]]
          iso_formatted: True
          format_string: "" #'%Y-%m-%d'
          default_value: "2023-06-25"
```

[RSS](#RSS)で触れたけどconfig例あった: https://github.com/obsidian-html/obsidian-html.github.io/tree/main/__src

## faviconの設定

commit: [🔧 Configure favicon · H1rono/scrap@17fa3af](https://github.com/H1rono/scrap/commit/17fa3af72f16f830614ac5e991a1312278ff6533)
該当ドキュメント: [Export vault files to html output - ObsidianHtml/Documentation](https://obsidian-html.github.io/configurations/tweaking/export-vault-files-to-html-output.html)

[Configuration Options - ObsidianHtml/Documentation](https://obsidian-html.github.io/configurations/configuration-options.html)のページに書いてなくて焦った

## RSS

該当ドキュメント: [RSS Feed - ObsidianHtml/Documentation](https://obsidian-html.github.io/configurations/features/rss-feed.html)

ここではcommit連ねる形で記録

**[🚧 Enable RSS(WIP) · H1rono/scrap@ecf98d9](https://github.com/H1rono/scrap/commit/ecf98d94de0f736745c5af3519e6ad1291f6fcc3)**

```yml
    rss:
      enabled: True
      host_root: "https://h1rono.github.io/scrap"
      styling:
        show_icon: True
      channel:
        title: "H1rono/scrap"
        website_link: "https://h1rono.github.io/scrap"
        description: "Obsidianメモ置き場"
        language_code: "ja-jp"
```

https://h1rono.github.io/scrap/obs.html/rss/feed.xml にフィード配信されてる
が、[vivaldiのRSS購読](https://help.vivaldi.com/ja/mail-ja/mail-feeds-ja/feeds/)で見たら↓の問題点が

- 各記事の日付が`1970/01/01 9:00`になってる
- READMEが入ってない

ところでドキュメント見てたらconfig例見つけた: https://github.com/obsidian-html/obsidian-html.github.io/tree/main/__src

↓は[config_v3.yml](https://github.com/obsidian-html/obsidian-html.github.io/blob/main/__src/config_v3.yml)から引用

```yml
    rss:
      enabled: True
      host_root: 'https://obsidian-html.github.io/'
      styling: 
        show_icon: True
      channel: 
        title: 'ObsidianHtml/Documentation'
        website_link: 'https://obsidian-html.github.io'
        description: 'The documentation site of ObsidianHtml, a package used to convert Obsidian notes to proper markdown and static HTML websites.'
        language_code: 'en-us'
        managing_editor: 'collector@dwrolvink.com'
        web_master: 'collector@dwrolvink.com'
      items:
        selector: 
          match_keys: ['yaml','tags', ['']]
          exclude_keys: ['yaml','tags', ['type/moc']]
          include_subfolders: ['Log', 'Changelog']
          exclude_subfolders: ['.git', 'md', 'index_from_tags', 'obs.html','__src']
          exclude_files: ['not_created.html', 'index.html']
        description:
          selectors:
            - ['yaml','rss:description']
            - ['first-paragraphs', 2, '<br/><br/>']
            - ['first-header', 1]
        title: 
          selectors: 
            - ['yaml','rss:title']
            - ['first-header', 1]
            - ['path', ['parent',1], '/ ', ['stem']]
        publish_date: 
          selectors: 
            - ['yaml','rss:publish_date']
            - ['yaml_strip','tags',['date/']]
          iso_formatted: True
          format_string: '' #'%Y-%m-%d'
          default_value: '1999-12-31'
```

日付設定は[Selector function](https://obsidian-html.github.io/configurations/features/rss-feed.html#!selector-functions)というやつで決まるらしい
yaml frontmatter手書きしないといけなさそう😇
いっそのことdaily notesだけrssに流すとかしてもいいかも？いや日記を書くつもりは現状なくて...

んーとりあえず日付は手書きするとして、README含めるのは`rss.items.exclude_files`いじったら良さそう

**[🔧 Update config of rss · H1rono/scrap@4aff7b5](https://github.com/H1rono/scrap/commit/4aff7b59092249b1bdd6fbafd5c2d5f4f1e7da65)**

vivaldiが悪いんだろうけど、1970/01/01の記事が残って2023/06/25の記事が新たに生成された

まあ動いてそうなので解決

## TOCどこだよ

該当ドキュメント: [ObsidianHtml/Documentation](https://obsidian-html.github.io/configurations/styling/styling.html#!table-of-contents)

生成された該当設定↓

```yml
  features:
    styling:
      add_toc: "<DEPRECATED>"
      toc_pane: "<DEPRECATED>"
      flip_panes: "<DEPRECATED>"
```

早速ドキュメントと違うんですが...
とりあえずTrueにしちゃうか

[🔧 Enable toc · H1rono/scrap@d99fa87](https://github.com/H1rono/scrap/commit/d99fa87a0c232c3321093d12d5f70f44a6ac670b)

いい感じになった

## 気になったとこ/TODO

- タイトルどうにかなりませんか
    - どのページも`site_name`に指定したものになってる
- プラグイン入れられるんだろうか
