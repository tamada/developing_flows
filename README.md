# developing_flows

近年のソフトウェア開発はプログラムを書けば終わりというわけではない．プログラム以外のドキュメントも書かないといけない．

ここでは，私がソフトウェアを開発するときに行う手順を記す．
新たにソフトウェア開発に臨もうとする初学者の参考になると幸いである．
ただし，以下の点に注意されたい．

* 私が過去に作成してきたソフトウェアの大半はCLIアプリとRESfulアプリである．
    * その他のアプリについては作り方が違うかもしれない．
* 私のやり方であって，一般的なやり方とは異なる可能性がある．
    * 2000年くらいから継続的に様々なものを個人的に開発し続けているものの，職業プログラマではなく，顧客に納品することもない．
      ここに書いたことは全くの的外れではないと思うが，検証された情報ではない．
    * TiDD（Ticket Driven Development）やTDD（Test Driven Development）ではない．
      これらを実践する場合は，ここに記したことに対して多少のアレンジが必要となろう．
    * [README Driven Development](https://tom.preston-werner.com/2010/08/23/readme-driven-development.html) と言えるかもしれない．
* 私が主に使用する言語は，Java, JavaScript, Goである．
    * 言語に依存する内容は極力排除して書くつもりであるが，依存する場合もあることを念頭に読んでもらいたい．


## 記されていること

* 全くの白紙の状態からソフトウェアプロジェクトを開始し，リリースするまでの一連の流れを記す．
* リリースするとは，次のものを公開することである．
    * バージョン管理されたプロダクト（ソースコードとビルドスクリプト）
    * ドキュメント
    * もしあれば Dockerイメージ，サーバへのデプロイ．

## 記されていないこと

* プログラムの書き方など，実装の詳細は書かない．別のドキュメントを参照されたい．

## 実績

私がこれまでに開発したものについては，以下を参照されたい．

* [tamadalab/purplecat](https://github.com/tamadalab/purplecat)
    * Go言語, CLI, REST, Docker
    * Mavenプロジェクトの依存ライブラリとそのライセンスを検出する．
* [tamada/rrh](https://github.com/tamada/rrh)
    * Go, CLI
    * gitリポジトリ管理ツール．
    * CLIアプリケーション．
* [tamada/pochi](https://github.com/tamada/pochi)
    * Java, CLI, Docker
    * Java向けバースマークツール（Javaアプリの盗用検出ツール）．
* [tamada/uniq2](https://github.com/tamada/uniq2)
    * Go, CLI, Docker
    * uniqコマンドの別実装．
* [tamada/fritter](https://github.com/tamada/fritter)
    * Java, CLI, Docker
    * Javaソースコードの品質チェックツール（[tamada/9rules](https://github.com/tamada/9rules)の後継）．

他にも様々なツールを https://github.com/tamada にて公開している．適宜参照されたい．

## 目次

* [プログラムを書く前に](https://github.com/tamada/developing_flows/blob/main/first.md)
* [プログラムを書き始めよう](https://github.com/tamada/developing_flows/blob/main/development.md)
* [リリースに向けて](https://github.com/tamada/developing_flows/blob/main/shipping.md)
* [用語](https://github.com/tamada/developing_flows/blob/main/terms.md)

## 参考資料

* [オープンソースプロジェクトを立ち上げる](https://ja-opensource-guide.github.io/starting-a-project/)
* [オープンソースの育て方](https://producingoss.com/ja/)