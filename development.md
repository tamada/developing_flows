---
title: ":black_nib: プログラムを書き始めよう"
description: >-
  前項に書かれた内容が全てできていれば，ソフトウェアのリポジトリがSCPに作成され，ローカルにもリポジトリのコピーが存在するはずである．
  それを踏まえて，次の手順でプログラムを書き始めよう．
---

## :bookmark: 目次

* [:beginner: はじめに](./README.md)
* [:egg: プログラムを書き始める前に](first.md)
* [:black_nib: プログラムを書き始めよう](development.md#readme)
  * [:tractor: ビルドファイルを用意する．](development.md#tractor-ビルドファイルを用意する)
  * [:building_construction: CIを整備する．](development.md#building_constructionci-を整備する)
  * [:desert: テストデータを準備する．](development.md#desert-テストデータを準備する)
  * [:name_badge: バッジを貼ろう](development.md#name_badge-バッジを貼ろう)
  * [:hatching_chick: プログラムを書き始める．](development.md#hatching_chick-プログラムを書き始める)
* [:package: リリースに向けて](shipping.md)
* [:closed_book: 用語](terms.md)
* [:books: 練習問題](exercise.md)
* [:ballot_box_with_check: チェックリスト](checklist.md)

## :tractor: ビルドファイルを用意する

プログラムを書き始めてすぐに準備すべきことはCI（Continuous Integration）である．push時にコンパイル，テスト，デプロイまで行う必要がある．CIを準備するのは大変な作業である．であるが故に，最初に用意し，実施できるようにする必要がある．そうでなければ，いつまで経ってもCIが実施されないまま開発が進むことになる．

そして，CIを実施するためには，ビルドツールによるビルドが必須である．そのため，リポジトリが準備できてすぐに行うべきことがビルドファイルの用意である．

### :traffic_light: ビルドで行うべきこと

ビルドでは，依存ライブラリの取得，コンパイル，テストを行う．そのため，ビルドファイルではコンパイル，テストが速やかに行われるように設定する．

依存ライブラリの取得では，作成するソフトウェアが依存するライブラリをダウンロードし，コンパイルに利用できるようにすることである．コンパイルとは，ソースファイルからオブジェクトファイル，実行ファイルに変換することである．

テストは，[xUnit](https://ja.wikipedia.org/wiki/XUnit)を用いて自動テストを実施することである．続くCIにも関連するが，ここでカバレッジ計測まで行っておく．もう一度言う．テストを実施するだけでは不十分で，カバレッジ計測まで行う必要がある．カバレッジ計測を行わない場合，テストが十分であるかを判断する材料がなくなるためである．カバレッジは作成するソフトウェアにどの程度の品質を求めるかによって変わってくるが，80%〜90%程度になると著者は考える．80%以下だと低すぎるし，90%以上だと，カバレッジ向上に必要となるコストが跳ね上がる． なお，カバレッジは指標であって，カバレッジの向上だけを目的としないように注意する必要がある．しっかりとテストを実施する必要がある（assertなしで実行するだけでカバレッジは向上する）．

また，個人的には単体テストは不要である．ここでいう単体テストとは，関数単位でバグを検出するための自動テストのことを指す．このような単体テストは，容易に書ける反面，仕様が変わるたびに当該テストの修正が必要となる． そこで単体テストではなく，結合テストを中心に実施すると良い．つまり，ビジネスロジック的に意味のある単位でテストを書くと良いであろう． もちろん，ユーティリティ的な関数（メソッド）のテストは単体テストとなろう．そこまでを否定するものではない．

#### :link: 参考資料

* [単体テストは限りなく無駄](http://hide1024.hatenablog.com/entry/2016/01/30/014800)
* [お前らにユニットテストの真髄を伝授する](https://qiita.com/takutoy/items/c684f761c655d832e5d2)
* [Why Most Unit Testing is Waste](https://rbcs-us.com/documents/Why-Most-Unit-Testing-is-Waste.pdf)
  * [Seque](https://rbcs-us.com/documents/Segue.pdf) （上記の追加記事）
  * [「ほとんどのユニットテストが役に立たない理由」を読んで](https://postd.cc/a-response-to-why-most-unit-testing-is-waste/)（上記の反論記事の日本語訳，[原文](http://henrikwarne.com/2014/09/04/a-response-to-why-most-unit-testing-is-waste/)）
* [TDD再考 (1) – テストファーストとユニットテストへの死刑宣告](https://ubiteku.oinker.me/2015/07/21/tdd-is-dead-long-live-testing/)
* [TDD再考 (2) – 何故、ほとんどのユニットテストは無駄なのか？](https://ubiteku.oinker.me/2015/07/27/why-most-unit-testing-is-waste/)
* [TDD再考 (3) – TDDが解決しようとした問題は何か？](https://ubiteku.oinker.me/2015/08/10/rip-tdd/)
* [TDD再考 (4) – TDDはプログラム初心者にとって自然な方法になり得るか？](https://ubiteku.oinker.me/2015/08/10/tdd-for-programming-newbies/)
* [TDD再考 (5) – ユニットテストの「ユニット」とは何を指すのか？](https://ubiteku.oinker.me/2015/10/27/what-is-unit/)
* [TDD再考 (6) – テスト容易性 ≠ 良いデザイン](https://ubiteku.oinker.me/2015/11/17/tdd%E5%86%8D%E8%80%83-6-%E3%83%86%E3%82%B9%E3%83%88%E5%AE%B9%E6%98%93%E6%80%A7-%E2%89%A0-%E8%89%AF%E3%81%84%E3%83%87%E3%82%B6%E3%82%A4%E3%83%B3/)
* [TDD再考 (7) – テストはどこまで書けば良いのか？](https://ubiteku.oinker.me/2015/12/03/tdd%E5%86%8D%E8%80%83-7-%E3%83%86%E3%82%B9%E3%83%88%E3%81%AF%E3%81%A9%E3%81%93%E3%81%BE%E3%81%A7%E6%9B%B8%E3%81%91%E3%81%B0%E8%89%AF%E3%81%84%E3%81%AE%E3%81%8B%EF%BC%9F/)
* [TDD再考 (8) – 凝集性（cohesion）とは何なのか？](https://ubiteku.oinker.me/2016/03/22/tdd%E5%86%8D%E8%80%83-8-%E5%87%9D%E9%9B%86%E6%80%A7%EF%BC%88cohesion%EF%BC%89%E3%81%A8%E3%81%AF%E4%BD%95%E3%81%AA%E3%81%AE%E3%81%8B%EF%BC%9F/)

### :small_airplane: どのビルドツールを利用するか

言語ごとに標準的なものを利用すると良い．ただし最低限の条件として，パッケージマネージャがついていることがあげられる．パッケージマネージャとは，インターネット上に存在する依存ライブラリを検索でき，自動的にダウンロードしてくれるものである．もちろん，自分自身がよく知っているものがあれば，レガシーなものでない限り，それを使い続ければ良い．

* Java
  * これから勉強を始めるのであれば，[Gradle](https://gradle.org)一択．
  * [Maven](https://maven.apache.org)を使い慣れているのでれば使い続けるのは良いかもしれない．ただし，Gradleへの速やかな移行を検討する方が良い．`pom.xml`は意外と様々なことを書かないといけないし，XMLはやはり書きにくい．
  * [Apache Ant](https://ant.apache.org)は捨てた方が良い． パッケージマネージャが使えない，手続き的に書いてしまうなど，今日の開発における問題が多すぎる．ビルドファイルのメンテナンスに手間がかかり過ぎる．
    * [Apache Ivy](https://ant.apache.org/ivy/)もあるが，XMLが必要となるし，メンテナンスするファイルが2つになってしまうのが困る．
* Go
  * Makeになるであろう．
  * [Bazelも便利らしい](https://medium.com/mixi-developers/go-project-with-bazel-ad807ba19f5c)．
* Ruby（よく知らない）
  * Rakeになると思う．
* Rust（よく知らない）
  * Cargo一択．
* JavaScript（よく知らない）
  * npm もしくは yarn
    * npmもyarnもパッケージマネージャであるが，`package.json`の中に`scripts`という要素が書ける．`npm run`や`yarn run`で`scripts`の中の特定の要素を実行できるため，ビルドツールとしての運用も可能であろう．

## :building_construction: CIを整備する

### :vertical_traffic_light: CIで行うべきこと

CIはpushやプルリクエストの発行の度に，主に以下のことを自動的に実行するよう設定する必要がある．

* テストカバレッジを計測する．
* プログラムの品質を計測する．
* ソフトウェアをデプロイする．

これらのことを実行するようになると，ソースコードの品質の低下をいち早く検出でき，改善すべき箇所がわかるようになる．品質を一定以上に保つためには必要なことである． 加えてCIで検査することにより，テストで失敗した場合にプルリクエストがマージできなくなるため，`main`（`master`）ブランチのビルドが壊れないことがある程度保証される．

CIの設定が済めば`README.md`に必要なバッジ（少なくとも以下のもの）を追加しよう．

* CIのビルドが通ったこと
* テストカバレッジ
* プログラムの品質

これにより，CIをやっている，テストを通している，カバレッジがどの程度であることを利用者に示せることになり，最低限のことをしているとアピールできる．

#### :link: 参考リンク

* [継続的インテグレーション](http://objectclub.jp/community/XP-jp/xp_relate/cont-j)
* [継続的インテグレーション (CI) とは？](https://circleci.com/ja/continuous-integration/)

### :airplane: 利用するCIツール

基本的に好きなものを利用すれば良いが，自前で準備する場合，有償でも良い場合，無償で行う場合などがある．著名なCIサービスは次の通り．OSS向けには無料で使えるものが多い．

* [Circle CI](https://circleci.com)（[料金プラン](https://circleci.com/ja/pricing/)）
* [TravisCI](https://travis-ci.com)（[料金プラン](https://www.travis-ci.com/plans)）

GitHubやGitLabには標準機能としてCI/CDが用意されている．

* [GitHub Actions](https://github.co.jp/features/actions)
* [GitLab CI/CD](https://docs.gitlab.com/ee/ci/)

自らサーバを立てるのであれば，[Jenkins](https://www.jenkins.io)が古くから使われていて良い．
また，[Dagger.io](https://dagger.io) はコンテナ環境でCIを実行でき，加えて，
TypeScript，JavaScript，Python，Goなどの言語でCIスクリプトを書けるため，柔軟な利用が可能である．

いずれのCIサービス/ツールを使うにしろ，行うべき処理をスクリプトとして記述する必要がある．スクリプトの詳細は，各CIサービス/ツールのドキュメントを参照されたい．

### :triangular_ruler: テストカバレッジを計測する

テストカバレッジはビルドツールで計測しているハズである．そのカバレッジがどのように推移しているのかをテストカバレッジの履歴を記録，閲覧できるサービスを利用しよう．

* [coveralls](https://coveralls.io)
* [codecov](https://about.codecov.io)

どちらもコミットごとにカバレッジの計測結果が記録され，そのカバレッジの推移がグラフで閲覧できるようになっている．これにより，ソフトウェアの品質（の一部）の推移を確認できるようになる．そして，大きく減少した場合は，テストが不十分であると確認できるようになる．

なお，これらのサービスのサイト上で，どの部分が未テストかを確認できるが，著者は開発者はこれを利用しない方が良いと考える． その代わりに，ローカル環境でのテストレポートを見て確認しよう． coverallsやcodecovなどのサイト上のレポートを更新するにはコミットが必要となるが，未テストかを確認するのはコミットの前である方が望ましいためである． サービスのサイト上でのテスト実施部分の確認は，開発者以外が利用するものと考えよう．

### :straight_ruler: プログラムの品質を測定する

プログラムの品質測定ツールやサービスを利用して，品質を自動測定しよう（2021-03-06時点の情報）．

* [codebeat](https://codebeat.co)（[サポート言語](https://hub.codebeat.co/docs/language-supported)，9言語）
* [sonarqube](https://www.sonarqube.org)（[サポート言語](https://www.sonarqube.org/features/multi-languages/)，27言語）
* [spotbugs](https://spotbugs.github.io)（Java）
* [codeclimate](https://codeclimate.com)（[サポート言語](https://codeclimate.com/quality/#home\_integration)，11言語）

どのようなサービスでも構わないが，できればプロダクトの初期から継続して計測し続けてみると良い．今までこのようなツールを使ったことがない場合，山のように指摘されることになる．ある程度プログラムを書いてからそのような指摘事項に対応するのは困難である．そのため，ソフトウェア開発の最初の方に，CIでプログラムの品質を測定するようにすると良い．

### ソフトウェアをデプロイする

できればCIでテストが成功するとデプロイできるようにしよう．

デプロイとは，ソフトウェアを利用できる状態に設置することであり，サーバソフトウェアであれば，外部からアクセスできるところでソフトウェアを動かし，クライアントからのリクエストを受け付ける状態にすることである．

近年は無料でサーバを立てられるPaaS（Platform as a Service）環境も揃っているので，それらを利用するのが良いであろう．AWS，GCP，Azure，IBM Cloudなどの主要PaaSベンダを利用するのも良いし，以下のようなベンダを利用するのも良いであろう．とにかく，一つに絞らず，適度に使い分ける，使ってみるのが良いと思う．

* [Heroku](https://heroku.com)
* [netlify](https://www.netlify.com)
* [vercel](https://vercel.com)
* [期限の制約なく無料で使えるクラウド「Free Tier」主要サービスまとめ　2023年版](https://www.itmedia.co.jp/news/articles/2307/10/news078.html)
* [ずっと無料で使えるクラウド「Free Tier」主要サービスまとめ（主にIaaS・PaaS）　2020年版](https://www.itmedia.co.jp/news/articles/2005/13/news069\_2.html)

## :desert: テストデータを準備する

ここでは，サンプルの入力データを準備する．`README.md`に書いたようなデータが良いであろう． このデータを準備することにより，プログラムを書いた直後にテストが行えるようになる．

特に複雑な入力データを要する場合は，テストデータの準備は必須である．後回しにすればするほど，準備のハードルが上がり，準備に対する心理的障害が増大していく．

なお，テストデータが，JSONやXML，Markdownなどの何らかのフォーマットであった場合，lintツールでフォーマットを検証しておくことを推奨する．フォーマットが間違っていたり，読みにくかったりすると，後々修正しなければならなくなる．それを防止するため，事前に検証しておこう．

* [htmllint](https://www.npmjs.com/package/htmllint)
* [xmllint](http://xmlsoft.org/xmllint.html)
* [jsonlint](https://github.com/zaach/jsonlint)
* [markdownlint](https://github.com/DavidAnson/markdownlint)
* [yamllint](https://github.com/adrienverge/yamllint)

## :name_badge: バッジを貼ろう

[バッジ](terms.md#バッジbadge)とはプロジェクトのステータスを利用者に一目で示すための画像である．
例えば，バージョン情報や，ライセンス，テストカバレッジ，CIのステータス，プログラムの品質などを示すことができる．
多くのGitHub，GitLab のリポジトリの `README.md` に貼られており，そのプロダクトのステータスを示している．

多くの場合，バッジの画像にリンクを貼ることでバッジは成り立つ．
例えば，バージョン情報やライセンスのバッジは，[shields.io](https://shields.io)などで
`https://img.shields.io/badge/License-MIT-blue` のようなパラメータを与えることでバッジ画像を生成できる．
この画像にプロジェクト内のライセンスファイルへのリンク，もしくは OSI のライセンスのページへのリンクを貼ることでバッジは完成する．

例えば，このリポジトリのバッジ（の一部）とそのMarkdownのソースは次の通りである．

[![License](https://img.shields.io/badge/License-CC--BY--4.0-green.svg)](https://github.com/tamada/developing\_flows/blob/main/LICENSE)
[![Version](https://img.shields.io/badge/Version-1.0.4-green.svg)](https://github.com/tamada/developing\_flows/releases/tag/v1.0.4)
[![DOI](https://zenodo.org/badge/335323499.svg)](https://zenodo.org/badge/latestdoi/335323499)

```markdown
[![License](https://img.shields.io/badge/License-CC--BY--4.0-green.svg)](https://github.com/tamada/developing\_flows/blob/main/LICENSE)
[![Version](https://img.shields.io/badge/Version-1.0.4-green.svg)](https://github.com/tamada/developing\_flows/releases/tag/v1.0.4)
[![DOI](https://zenodo.org/badge/335323499.svg)](https://zenodo.org/badge/latestdoi/335323499)
```

また，テストカバレッジやプログラムの品質のバッジは，[coveralls](https://coveralls.io)や[codecov](https://about.codecov.io)などのサービスで生成できる．

## :hatching_chick: プログラムを書き始める

### :ticket: おおっとその前に

これから何を行うかをチケットに登録しよう． 登録するチケットは一つで構わない． これから何に取り組むのかを明らかにするためである． ここで登録したチケットが完成すれば，commit，pushし，プルリクエストを発行することになる． そのため，その程度の規模（数十分〜数時間で出来上がる程度の粒度）でチケットを登録しよう．

チケットは DoD（Definition of Done; 完了の定義）を意識して内容を書こう．何ができればそのチケットが完了したのかを予め決めておくのである．これを最初に決めておくだけで，途中で道に迷うことが少なくはるハズである．

また，これからの作業を全て洗い出して全てをチケットに登録するようにすると，[TiDD](https://www.amazon.co.jp/dp/4798125067/)となるであろう．

### :trident: ブランチを切る

利用する開発フローが[GitLabフロー](https://postd.cc/gitlab-flow/)でない限り，`main`ブランチに直接コミットは行わない．`main`ブランチから新たなブランチを派生させ，そこで開発を始めよう．

gitのブランチの名前の決め方は色々とあるが，どのような命名方法でも良い．とにかくブランチを切って，`main`は常に動作する状態に置いておくことが重要である．

### :walking: IDEを開いてプログラムを書き始める

ここまで準備してようやくプログラムを書き始める．どのような順序で書いても良いが，著者の場合は次のような順番で書く（以下の箇条書きの各項目が一つのチケットの単位とすることが多い）．

* `main`メソッドでオプション解析を行う．
  * `README.md`に書いたヘルプメッセージと同じものが出力できるようにする．
* オプションなしで実行した時の，デフォルトの結果が出力されるようにする．
* オプションに一つずつ対応していく．

動作確認のため，テストコードも書いておくと良い． テストコードを書いておくと，CI時にカバレッジなども計測してくれる（ように設定したハズである）．

なお，プロダクトコードに先駆けてテストコードから書くと，[TDD](https://www.amazon.co.jp/dp/4274217884/)となるが，筆者はTDDを実践したことがない（これまで実践しようとしたけど，できなかった）．

### commit, pushする

さて，チケットに登録した分のプログラムを書き，動作確認も済めばいよいよcommitである．commitするときは，関係する変更を一回のコミットに含めるようにする必要がある．

コミットにはコミットコメントを含める必要がある．コミットコメントは，[1行目に概要，2行目は空行で，3行目以降に詳細を書け](https://postd.cc/how-to-write-a-git-commit-message/)，というように言われている．本来であれば，それに従い，書けば良いのであるが，コミットメッセージを書き慣れていない状態でそのような書き方を要求されると疲れてしまう．そのため，まずは1行目の概要のみのコミットメッセージでコミットしてみよう．

また，[Conventional Commits](https://www.conventionalcommits.org/ja/v1.0.0/)に従ってコミットメッセージを書くのも良いであろう．とにかく，プロジェクトの中でコミットメッセージの書き方を統一しておくことが重要である．

コミットできれば，pushしよう．

#### :link: 参考リンク

* [GitHubで使われている実用英語コメント集](https://qiita.com/shikichee/items/a5f922a3ef3aa58a1839)
* [ネイティブと働いて分かった英語コミットメッセージの頻出動詞10つ](https://qiita.com/gogotanaka/items/b65e1b081fa976e5d754)
* [英語で書いてあるコミットログの動詞が現在形のわけ](https://moznion.hatenadiary.com/entry/20130122/1358834668)
* [よいコミットメッセージの書き方（翻訳＋要約）](https://qiita.com/siida36/items/ed3103e27e0f6ac531f2)
* [Github : コミットメッセージにおけるタイトルの「文法」](https://note.com/haru_notes/n/n3d9c406e9ac6)
* [Git でコミットする時のルールを言語化してみた](https://pyteyon.hatenablog.com/entry/2020/02/27/092101)
* [提言: コミットメッセージの一行目には要求仕様を書け](https://qiita.com/magicant/items/882b5142c4d5064933bc)
* [commit typeは誰に向けたものなのか](https://times.hrbrain.co.jp/entry/how-to-write-commit-message-type)
* [コミットメッセージとバージョンアップとタグ付けと更新履歴を自動化しよう](https://oucrc.net/articles/i-fohjgc\_f/)

### プルリクエストを発行し，マージする

pushができれば，GitHubの画面を開き，プルリクエストを発行しよう．プルリクエストを発行すると，CIが動作し出すハズである．CIでの検査が終わるのを待とう．

CIでのビルドをパスすれば，プルリクエストをマージし，ローカルにcloneしたリポジトリにも変更を取り込もう（`main`ブランチをpullしよう）．これが終われば，再び[プログラムを書き始める](development.md#プログラムを書き始める)の項目を最初から実践し，ソフトウェアを完成に近付けていこう．

## Navigation

* [前へ](first.md)
* [次へ](shipping.md)
