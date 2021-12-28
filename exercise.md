---
title: ":books: 練習問題"
description: >-
  これまでに述べた内容を実践するためには何らかのネタが必要である．
  作りたいものがあるのであれば，それを作れば良いが，具体的なものが思い浮かばない場合は，ここに挙げるようなソフトウェアを作ると良いであろう．
---

なお，作成したソフトウェアの著作権は作成者に属すれば良いが，ソフトウェアの名称や具体的な仕様は以下に述べたものに頼らず，作成者が捻り出すこと． 別の実装例を作成し，掲載しても良いという人がいれば，[Issue](https://github.com/tamada/developing\_flows/issues)や[Pull request](https://github.com/tamada/developing\_flows/pulls)などで連絡されたい．

## :bookmark: 目次

* [:beginner: はじめに](./)
* [:egg: プログラムを書き始める前に](first.md)
* [:black_nib: プログラムを書き始めよう](development.md)
* [:package: リリースに向けて](shipping.md)
* [:closed_book: 用語](terms.md)
* [:books: 練習問題](exercise.md#readme)
  * [ワードカウント](exercise.md#ワードカウント)
  * [最新バージョン情報の取得](exercise.md#最新バージョン情報の取得)
  * [いいねを数えるREST API](exercise.md#いいねを数えるrestapi)
  * [その他](exercise.md#その他)
* [:ballot_box_with_check: チェックリスト](checklist.md)

## ワードカウント

`wc`コマンドはファイルのワード数，バイト数，行数を数えるが，ディレクトリ以下のファイルを辿ってくれない． また，`find`などで見つけたファイルの行数を数えるには`xargs`を併用する必要がある． 加えて，`.gitignore`は考慮しない． そこで，`.gitignore`を考慮しつつ，ディレクトリが指定された場合，そのディレクトリ以下のファイルを対象とするソフトウェアを作成する．

なお，REST APIにも対応すると良い．

* [玉田の実装例 `tamada/wildcat`](https://github.com/tamada/wildcat)
  * ファイルとディレクトリを受け取れる，
  * アーカイブファイルに対応する（jar, zip, tar, tar.gz, tar.bz2）
  * ファイルリストを受け取れる，
  * 複数の出力フォーマットに対応する（default, csv, json, xml），
  * `.gitignore`を見て無視するファイルを決める，
  * REST APIサーバを立てられる，などの機能を盛り込んだ．

## 最新バージョン情報の取得

GitHub や GitLab などで様々なプロジェクトが日々公開されている． そのような中，最新バージョンが何でいつ公開されたのかをコマンドラインで確認したい．

* [玉田の実装例 `tamada/flaver`](https://github.com/tamada/flaver)

## いいねを数えるREST API

例えば，https://tamadalab.github.io/publications/ で Like の数を数えるようなものである．[`tamadalab/momonga`](https://github.com/tamadalab/momonga) として作成しており，上記ページで実稼働中である．

`momonga`はfirebaseで動作しているが，別のPaaS環境で動作させるのも良い．

## その他

例題の候補があれば，Issuesで連絡されたい．

## Navigation

* [前へ](terms.md)
* [次へ](checklist.md)
