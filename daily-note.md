# daily noteのルール

tags: #📅 #strategy

[[strategy#運用ルール]]から切り離して書きます

## templateを使う

```md
---
tags:
  - 📅/YYYY/MM/DD
---

# 📅 YYYY/MM/DD

## 今日書いたノート

**作成した**

- [[hoge]]

**編集した**

- [[fuga]]

## ひとこと感想

眠い。Rust楽しい
```

## daily note作成後にやること

`YYYY/MM/index.md`を更新(その日への参照を付け足す)

## 月が変わったらやること

月まとめとして`YYYY/MM/index.md`を作成して、`YYYY/index.md`にその月への参照を追加

月まとめのフォーマット

```md
# 📅 YYYY/MM

tags: #📅/YYYY/MM

- [[./01]]
- ...
```

## 年が変わったらやること

年まとめとして`YYYY/index.md`を作成して、`README.md`にその年への参照を追加

年まとめのフォーマット

```md
# 📅 YYYY

tags: #📅/YYYY

- [[./01/index]]
- ...
```
