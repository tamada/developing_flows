---
title: "ソフトウェアを作り始める前にすべきこと"
description: >-
  近年のソフトウェア開発はプログラムを書けば終わりというわけではない．プログラム以外のドキュメントも書かないといけない．ここでは，著者がソフトウェアを開発するときに行う手順を記す．
  新たにソフトウェア開発に臨もうとする初学者の参考になると幸いである．
---

# ソフトウェアを作り始める前にすべきこと

[![License](https://img.shields.io/badge/License-CC--BY--4.0-green.svg)](https://github.com/tamada/developing\_flows/blob/main/LICENSE)
[![Version](https://img.shields.io/badge/Version-1.0.4-green.svg)](https://github.com/tamada/developing\_flows/releases/tag/v1.0.4)
[![DOI](https://zenodo.org/badge/335323499.svg)](https://zenodo.org/badge/latestdoi/335323499)
[![GitHub Discussion](https://img.shields.io/badge/GitHub-Discussions-blue?logo=github)](https://github.com/tamada/developing\_flows/discussions)

[![CC-BY-4.0](https://i.creativecommons.org/l/by/4.0/88x31.png)](http://creativecommons.org/licenses/by/4.0/)

## :beginner: はじめに

### :loudspeaker: 注意

ここでは，著者がソフトウェアを開発するときに行う手順を記す． 新たにソフトウェア開発に臨もうとする初学者の参考になると幸いである． ただし，以下の点に注意されたい．

* 著者が過去に作成してきたソフトウェアの大半はCLIアプリとRESfulアプリである．
  * その他のアプリについては作り方が違うかもしれない．
* 著者のやり方であって，一般的なやり方とは異なる可能性がある．
  * 2000年くらいから継続的に様々なものを個人的に開発し続けているものの，職業プログラマではなく，顧客に納品することもない． ここに書いたことは全くの的外れではないと思うが，検証された情報ではない．
  * [TiDD（Ticket Driven Development）](https://www.amazon.co.jp/dp/4798125067/)や[TDD（Test Driven Development）](https://www.amazon.co.jp/dp/4274217884)ではない． これらを実践する場合は，ここに記したことに対して多少のアレンジが必要となろう．
  * [README Driven Development](https://tom.preston-werner.com/2010/08/23/readme-driven-development.html) と言えるかもしれない．
* 著者が主に使用する言語は，Java, JavaScript, Goである．
  * 言語に依存する内容は極力排除して書くつもりであるが，依存する場合もあることを念頭に読んでもらいたい．

### :bookmark: 目次

* [:beginner: はじめに](./README.md)
  * [:loudspeaker: 注意](./README.md#laudspeaker-注意)
  * [:page_facing_up: このドキュメントについて](./README.md#page_facing_up-このドキュメントについて)
  * [:bust_in_silhouette: 著者の実績](./README.md#bust_in_silhouette-著者の実績)
  * [:link: 参考資料](./README.md#link-参考資料)
  * [:card_index: About](./README.md#card_indexab-out)
* [:egg: プログラムを書き始める前に](first.md)
* [:black_nib: プログラムを書き始めよう](development.md)
* [:package: リリースに向けて](shipping.md)
* [:closed_book: 用語](terms.md)
* [:books: 練習問題](exercise.md)
* [:ballot_box_with_check: チェックリスト](checklist.md)

### :page_facing_up: このドキュメントについて

* 記されていること
  * 全くの白紙の状態からソフトウェアプロジェクトを開始し，リリースするまでの一連の流れを記す．
  * リリースするとは，次のものを公開することである．
    * バージョン管理されたプロダクト（ソースコードとビルドスクリプト）
    * ドキュメント
    * もしあれば Dockerイメージ，ダウンロードファイルのサーバへのデプロイ．
* 記されていないこと
  * プログラムの書き方など，実装の詳細や設計手法，要求定義の方法などは書かれていない．別のドキュメントを参照されたい．
* このドキュメントの想定読者
  * 一通りのプログラムが書けるようになったものの，まだ一つのプロジェクトを経験していない開発者，もしくは幾つかのプロジェクトを経験し，思い通りに開発できなかった開発者．

### :bust_in_silhouette: 著者の実績

私がこれまでに開発したものについては，以下を参照されたい．

* [`tamadalab/purplecat`](https://github.com/tamadalab/purplecat)
  * Go, CLI, REST, Docker
  * Mavenプロジェクトの依存ライブラリとそのライセンスを検出する．
* [`tamada/rrh`](https://github.com/tamada/rrh)
  * Go, CLI
  * gitリポジトリ管理ツール．
* [`tamada/pochi`](https://github.com/tamada/pochi)
  * Java, CLI, Docker, Groovy
  * Java向けバースマークツール（Javaアプリの盗用検出ツール）．
* [`tamada/uniq2`](https://github.com/tamada/peripherals)
  * Go, CLI, Docker
  * uniqコマンドの別実装や Stream の take や skip のような操作を CLI でもできるようにした．
* [`tamada/fritter`](https://github.com/tamada/fritter)
  * Java, CLI, Docker
  * Javaソースコードの品質チェックツール（[tamada/9rules](https://github.com/tamada/9rules)の後継）．
* [`tamada/btmeister`](https://github.com/tamada/btmeister)
  * Rust, CLI, Docker
  * どのようなビルドツールを利用しているのかを判定するツール．

他にも様々なツールを https://github.com/tamada にて公開している．適宜参照されたい．

### :link: 参考資料

* [オープンソースプロジェクトを立ち上げる](https://ja-opensource-guide.github.io/starting-a-project/)
* [オープンソースの育て方](https://producingoss.com/ja/)
* [Command Line Interface Guideline](https://clig.dev)
* [12 Factor CLI Apps](https://medium.com/@jdxcode/12-factor-cli-apps-dd3c227a0e46)
* [The Missing Semester of Your CS Education (日本語版)](https://missing-semester-jp.github.io)

### Navigation

* 前へ
* [次へ](first.md)

### :name_badge: About

#### :man_office_worker:著者 :woman_office_worker:

* 玉田 春昭（@tamada）
  * [https://tamada.github.io/](https://tamada.github.io)
  * [https://tamada.gitbook.io/developing-flows](https://tamada.gitbook.io/developing-flows/)

#### :thought_balloon: ご意見・感想など

書かれている内容についての意見や修正案などはGitHub上の[Issue](https://github.com/tamada/developing_flows/issues)や[Pull request](https://github.com/tamada/developing_flows/pulls)などで送付願いたい． プルリクエストを歓迎する．

また，感想などはGitHubの[Discussions](https://github.com/tamada/developing_flows/discussions)で送られたい．

#### 引用方法

* 玉田 春昭，"ソフトウェアを作り始める前にすべきこと"，https://github.com/tamada/developing_flows，Feb 27, 2024. 

[![DOI](https://zenodo.org/badge/335323499.svg)](https://zenodo.org/badge/latestdoi/335323499)

```tex
@misc { 2021sdf_tamada,
  author       = {玉田 春昭},
  title        = {ソフトウェアを作り始める前にすべきこと},
  howpublished = {\url{https://github.com/tamada/developing_flows}},
  month        = {Feburaury},
  year         = {2024},
}
```

#### :pushpin: 編集履歴

* 2024-02-24
  * [CI/CD環境](https://github.com/tamada/developing_flows/blob/main/development.md#building_construction-ciを整備する)に[Dagger](https://dagger.io)を追加した．
  * [用語集](terms.md)に[バッジ](terms.md#バッジbadge)を追加した．
  * [:black_nib: プログラムを書き始めよう](development.md)に[:name_badge: バッジを貼ろう](development.md#name_badge-バッジを貼ろう)を追加した．
* 2023-11-04
  * [ライセンス選択のフローチャート](first.md#フローチャート)を追加した．
  * [`.gitignore`](first.md#gitignore)で，具体例を書くように更新した．
  * 色々な箇所の参考リンクを追加した．
* 2022-12-26
  * 引用方法を記した．
  * v1.0.3 リリース
* 2022-04-20
  * [:package: リリースに向けて](shipping.md) でパッケージマネージャへのリンクを貼った．
* 2021-12-28
  * GitBookで公開した．
  * 絵文字を追加した．
  * v1.0.2 リリース
* 2021-05-11
  * [チェックリスト](checklist.md)を追加した．
* 2021-05-02
  * [参考資料](./#参考資料)に [The Missing Semester of Your CS Education (日本語版)](https://missing-semester-jp.github.io) を追加した．
* 2021-04-12
  * [プログラムを書き始めよう](development.md)の[プログラムを書き始める](development.md#おおっとその前に)にDoD（Definition of Done; 完了の定義）についてのことを追記した．
  * v1.0.1 リリース
* 2021-03-06
  * v1.0.0 リリース