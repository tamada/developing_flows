# developing_flows

[![License](https://img.shields.io/badge/License-CC--BY--4.0-green.svg)](https://github.com/tamada/developing_flows/blob/master/LICENSE)
[![Version](https://img.shields.io/badge/Version-1.0.1-green.svg)](https://github.com/tamada/developing_flows/releases/tag/v1.0.1)
[![GitHub Discussion](https://img.shields.io/badge/GitHub-Discussions-blue?logo=github)](https://github.com/tamada/developing_flows/discussions)

[![CC-BY-4.0](https://i.creativecommons.org/l/by/4.0/88x31.png)](http://creativecommons.org/licenses/by/4.0/)

## Overview

近年のソフトウェア開発はプログラムを書けば終わりというわけではない．プログラム以外のドキュメントも書かないといけない．

ここでは，著者がソフトウェアを開発するときに行う手順を記す．
新たにソフトウェア開発に臨もうとする初学者の参考になると幸いである．
ただし，以下の点に注意されたい．

* 著者が過去に作成してきたソフトウェアの大半はCLIアプリとRESfulアプリである．
    * その他のアプリについては作り方が違うかもしれない．
* 著者のやり方であって，一般的なやり方とは異なる可能性がある．
    * 2000年くらいから継続的に様々なものを個人的に開発し続けているものの，職業プログラマではなく，顧客に納品することもない．
      ここに書いたことは全くの的外れではないと思うが，検証された情報ではない．
    * [TiDD（Ticket Driven Development）](https://www.amazon.co.jp/dp/4798125067/)や[TDD（Test Driven Development）](https://www.amazon.co.jp/dp/4274217884)ではない．
      これらを実践する場合は，ここに記したことに対して多少のアレンジが必要となろう．
    * [README Driven Development](https://tom.preston-werner.com/2010/08/23/readme-driven-development.html) と言えるかもしれない．
* 著者が主に使用する言語は，Java, JavaScript, Goである．
    * 言語に依存する内容は極力排除して書くつもりであるが，依存する場合もあることを念頭に読んでもらいたい．

## 目次

* [はじめに](#readme)
  * [Overview](#overview)
  * [このドキュメントについて](#このドキュメントについて)
  * [著者の実績](#著者の実績)
  * [参考資料](#参考資料)
  * [About](#about)
* [プログラムを書き始める前に](https://github.com/tamada/developing_flows/blob/main/first.md)
* [プログラムを書き始めよう](https://github.com/tamada/developing_flows/blob/main/development.md)
* [リリースに向けて](https://github.com/tamada/developing_flows/blob/main/shipping.md)
* [用語](https://github.com/tamada/developing_flows/blob/main/terms.md)
* [練習問題](https://github.com/tamada/developing_flows/blob/main/exercise.md)

## このドキュメントについて

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

## 著者の実績

私がこれまでに開発したものについては，以下を参照されたい．

* [tamadalab/purplecat](https://github.com/tamadalab/purplecat)
    * Go, CLI, REST, Docker
    * Mavenプロジェクトの依存ライブラリとそのライセンスを検出する．
* [tamada/rrh](https://github.com/tamada/rrh)
    * Go, CLI
    * gitリポジトリ管理ツール．
* [tamada/pochi](https://github.com/tamada/pochi)
    * Java, CLI, Docker, Groovy
    * Java向けバースマークツール（Javaアプリの盗用検出ツール）．
* [tamada/uniq2](https://github.com/tamada/uniq2)
    * Go, CLI, Docker
    * uniqコマンドの別実装．
* [tamada/fritter](https://github.com/tamada/fritter)
    * Java, CLI, Docker
    * Javaソースコードの品質チェックツール（[tamada/9rules](https://github.com/tamada/9rules)の後継）．

他にも様々なツールを https://github.com/tamada にて公開している．適宜参照されたい．

## 参考資料

* [オープンソースプロジェクトを立ち上げる](https://ja-opensource-guide.github.io/starting-a-project/)
* [オープンソースの育て方](https://producingoss.com/ja/)
* [Command Line Interface Guideline](https://clig.dev)
* [12 Factor CLI Apps](https://medium.com/@jdxcode/12-factor-cli-apps-dd3c227a0e46)

## Navigation

* 前へ
* [次へ](first.md)

## About

### 著者

*  玉田 春昭（@tamada）
  * https://tamada.github.io/

### ご意見・感想など

書かれている内容についての意見や修正案などは[Issue](https://github.com/tamada/developing_flows/issues)や[Pull request](https://github.com/tamada/developing_flows/pulls)などで送付願いたい．
プルリクエストを歓迎する．

また，感想などは[Discussions](https://github.com/tamada/developing_flows/discussions)で送られたい．

### 編集履歴

* 2021-04-12
  * [プログラムを書き始めよう](development.md)の[プログラムを書き始める](development.md#おおっとその前に)にDoD（Definition of Done; 完了の定義）についてのことを追記した．