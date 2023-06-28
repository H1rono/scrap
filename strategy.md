# scrap運営戦略

tags: #obsidian

雑に考えます

## 参考文献

- [📘Obsidian Publishの運営戦略 - Minerva](https://minerva.mamansoft.net/%F0%9F%93%98Articles/%F0%9F%93%98Obsidian+Publish%E3%81%AE%E9%81%8B%E5%96%B6%E6%88%A6%E7%95%A5)
- [📘ObsidianでPKMを続けられた理由を振り返る - Minerva](https://minerva.mamansoft.net/%F0%9F%93%98Articles/%F0%9F%93%98Obsidian%E3%81%A7PKM%E3%82%92%E7%B6%9A%E3%81%91%E3%82%89%E3%82%8C%E3%81%9F%E7%90%86%E7%94%B1%E3%82%92%E6%8C%AF%E3%82%8A%E8%BF%94%E3%82%8B)
- [日本語で書かれている Obsidian Publish サイト - nNodes](https://notes.naney.org/Notes/%E6%97%A5%E6%9C%AC%E8%AA%9E%E3%81%A7%E6%9B%B8%E3%81%8B%E3%82%8C%E3%81%A6%E3%81%84%E3%82%8B+Obsidian+Publish+%E3%82%B5%E3%82%A4%E3%83%88)

## 欲しいもの/やりたいこと

- H1ronoとしてやったこと全てを記したい
    - 一度得た知見を2度と失わないように
- 習慣化して、ゆっくり育てる感じで
- [Minerva](https://minerva.mamansoft.net/Home)を目標にしたい

## こうなってはいけない

- 続かない
- わかりづらい
- 孤立したノートが存在する

## 具体的な方針

**孤立してはいけない、習慣化したい**

- daily noteで「今日はこれをやった」というのを積み重ねればいいかも
    - [[obsidian-html#RSS|RSS配信]]はこのdaily noteだけに絞るとyaml frontmatter周りで楽になる？
- タグで日付入れるのもアリ🐜
    - [[obsidian-html]]がタグ → RSSをサポートしてるか怪しい
    - 既存のノートに追記する時もやりやすい
    - ↑RSSの日付が複数になって ??? に
- H1ronoの生活習慣的に、daily noteを日記的につけるのは厳しい
    - これを機に頑張る...

ノート頭にタグをつける、追記部分にはタグ、RSSはdaily noteだけ

**やったこと全てを記したい**

- とは言ってもこれで作業効率が落ちるのは避けたい
- 一度やって「後でやるか」となったら**絶対にやらない**のでしょうがないか

守秘義務なしで他にも転用できそうな知見とかは何がなんでも書く

## 運用ルール

#📅/2023/06/28 時点

- 毎日何かしら書く
    - これはscrapが育ってきたらやめていい
- daily noteを↓の形式でとる(パスは`YYYY/MM/DD`)

```md
---
rss:
  publish_date: YYYY/MM/DD
tags:
  - 📅/YYYY/MM/DD
---

# 📅 YYYY/MM/DD

## 今日書いたノート

- [[hoge]]
- [[fuga]]

## ひとこと感想

眠い。Rust楽しい
```

- シリーズものはフォルダにまとめる
- それ以外はルート直下に←マジで？

TODO: template作る
