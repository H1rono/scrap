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
```

## 気になったとこ

- タイトルどうにかなりませんか
