# obsidian-html使った

repo: [obsidian-html/obsidian-html: Python code to convert Obsidian notes to proper markdown and optionally to create an html site too.](https://github.com/obsidian-html/obsidian-html)
docs: [ObsidianHtml/Documentation](https://obsidian-html.github.io/index.html)

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

features:
  rss:
    TODO  # まだ未設定
```

## faviconの設定

[参考commit](https://github.com/H1rono/scrap/commit/17fa3af72f16f830614ac5e991a1312278ff6533)
該当ドキュメント: [Export vault files to html output - ObsidianHtml/Documentation](https://obsidian-html.github.io/configurations/tweaking/export-vault-files-to-html-output.html)

[Configuration Options - ObsidianHtml/Documentation](https://obsidian-html.github.io/configurations/configuration-options.html)のページに書いてなくて焦った

## RSS

ドキュメント: [RSS Feed - ObsidianHtml/Documentation](https://obsidian-html.github.io/configurations/features/rss-feed.html)

ここではcommit連ねる形で記録

[🚧 Enable RSS(WIP) · H1rono/scrap@ecf98d9](https://github.com/H1rono/scrap/commit/ecf98d94de0f736745c5af3519e6ad1291f6fcc3)

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
が、[vivaldiのRSS機能]

## 気になったとこ/TODO

- タイトルどうにかなりませんか
    - どのページも`site_name`に指定したものになってる
- RSS
- プラグイン入れられるんだろうか
- ページ右側のカラムがTOCになるはずなのになってない
