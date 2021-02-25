# 練習問題

これまでに述べた内容を実践するためには何らかのネタが必要である．
作りたいものがあるのであれば，それを作れば良いが，具体的なものが思い浮かばない場合は，ここに挙げるようなソフトウェアを作ると良いであろう．

なお，作成したソフトウェアの著作権は作成者に属すれば良いが，ソフトウェアの名称や具体的な仕様は以下に述べるに頼らず，作成者が捻り出すこと．
別の実装例を作成し，掲載しても良いという人がいれば，[Issue](https://github.com/tamada/developing_flows/issues)や[Pull request](https://github.com/tamada/developing_flows/pulls)などで連絡されたい．

## 目次

* [はじめに](README.md)
* [プログラムを書き始める前に](first.md)
* [プログラムを書き始めよう](development.md)
* [リリースに向けて](shipping.md)
* [用語](terms.md)
* [練習問題](#readme)
  * [ワードカウント](#ワードカウント)
  * [ファイルコピー](#ファイルコピー)
  * [その他](#その他)

## ワードカウント

`wc`コマンドはファイルのワード数，バイト数，行数を数えるが，ディレクトリ以下のファイルを辿ってくれない．
また，`find`などで見つけたファイルの行数を数えるには`xargs`を併用する必要がある．
加えて，`.gitignore`は考慮しない．
そこで，`.gitignore`を考慮しつつ，ディレクトリが指定された場合，そのディレクトリ以下のファイルを対象とするソフトウェアを作成する．

なお，REST APIにも対応すると良い．

* [玉田の実装例 `tamada/wildcat`](https://github.com/tamada/wildcat)
  * ファイルとディレクトリを受け取れる，
  * アーカイブファイルに対応する（jar, zip, tar, tar.gz, tar.bz2）
  * ファイルリストを受け取れる，
  * 複数の出力フォーマットに対応する（default, csv, json, xml），
  * `.gitignore`を見て無視するファイルを決める，
  * REST APIサーバを立てられる，などの機能を盛り込んだ．

## いいねを数えるREST API

例えば，https://tamadalab.github.io/publications/ で Like の数を数えるようなものである．[`tamadalab/momonga`](https://github.com/tamadalab/momonga) として作成しており，上記ページで実稼働中である．

`momonga`はfirebaseで動作しているが，別のPaaS環境で動作させるのも良い．

## その他

例題の候補があれば，Issuesで連絡されたい．