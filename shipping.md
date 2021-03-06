# リリースに向けて

ソフトウェア開発がある程度落ち着いたら，リリースに向けて，次のことを行う必要がある．

## 目次

* [はじめに](README.md)
* [プログラムを書き始める前に](first.md)
* [プログラムを書き始めよう](development.md)
* [リリースに向けて](#readme)
  * [バージョンを決める．](#バージョンを決める)
  * [Webサイトを構築する．](#webサイトを構築する)
  * [Dockerfileを用意する．](#dockerfileを用意する)
  * [パッケージマネージャでのインストールを整備する．](#パッケージマネージャでのインストールを整備する)
  * [必要に応じてDOIを発行する．](#必要に応じてdoiを発行する)
  * [リリースを公開する．](#リリースを公開する)
  * [宣伝しよう．](#宣伝しよう)
* [用語](terms.md)
* [練習問題](exercise.md)

## バージョンを決める

[セマンティックバージョニング（semantic versioning）](https://semver.org/lang/ja/)でバージョンを付ける．リリースの時の具体的なバージョン番号は何でも良いが，一度リリースすると，同じバージョン番号で異なる内容のものをリリースしてはいけない点に注意されたい．

また，バージョン番号がソースコードやドキュメントの様々な箇所に点在していると修正して回るのが困難になる．そのため，ビルドファイル中にバージョン番号を書いておき，そこを変更すると，全てのバージョン番号が変更されるようにしておくと良い．

## Webサイトを構築する

[Jekyll](https://jekyllrb.com/)でも[Hugo](https://gohugo.io)でも[Gatsby](https://www.gatsbyjs.com/)でも何でも良いが，静的サイト構築ツールを使い，Webサイトを構築する．

Webサイトは，[GitHub Pages](https://pages.github.com/)や[GitLab Pages](https://docs.gitlab.com/ee/user/project/pages/)などで公開すると良い．

Webサイトで公開する内容は，少なくとも`README.md`で書いた内容は全て公開する必要がある．

## Dockerfileを用意する

作成したソフトウェアがDockerableであればDockerfileを用意しておこう．

Dockerfileを用意すれば，[DockerHub](https://hub.docker.com/)や[GitHub Registry](https://github.com/features/packages)，[JFrog Artifactory](https://jfrog.com/artifactory/)などのいずれかに登録し，`README.md`にDockerイメージの名前やDockerを使った利用例を示しておこう．

## パッケージマネージャでのインストールを整備する

インストールを簡易化するために各OS向けにパッケージマネージャが存在する．全てに対応する必要はないと思うが，自分が主に使う環境向けのレシピは用意しておきたい．

* `apk`: Alpine Linux
* `pacman`: Arch Linux
* `apt`: Debian
* `dnf`: Fedora
* `emerge`: Gentoo
* `brew`: macOS（Homebrew）
* `port`: macOS（MacPorts）
* `chocolatey`: Windows

レシピの書き方などの詳細は各ドキュメントなどを参照されたい．

## 必要に応じてDOIを発行する

DOI（Digial Object Identifier）とは，インターネット上のドキュメントに恒久的に与えられるIDのことで，学術論文などで使われている．ソフトウェアに対してもDOIを発行できるようになっている．もし，作成したソフトウェアを論文中で引用する場合，DOIを発行しておくと良いかもしれない．

* [Making Your Code Citable](https://guides.github.com/activities/citable-code/)

## リリースを公開する

ここまでできれば，gitでtagを打ち，zipなどで成果物をまとめよう．そして，まとめた成果物を公開しよう．

* `git tag`でタグを発行する．
* zipで成果物をまとめてダウンロードできるようにする．
* GitHubなどのリリースページでリリースを公開する．

なお，これも自動化されていると良い．言語ごとにツールが提供されているようだ．

* Go lang
  * [`goreleaser`](https://github.com/goreleaser/goreleaser)
* Java (Maven)
  * [`maven-release-plugin`](https://maven.apache.org/maven-release/maven-release-plugin/)
* Java (Gradle)
  * [`gradle-release-plugin`](https://github.com/researchgate/gradle-release)

## 宣伝しよう

リリースが作成できれば，宣伝しよう．従来であれば，[http://freecode.com](http://freecode.com) などで広報できたが，2014-06-18 以降アップデートされていない．今日の媒体としては，TwitterなどのSNSや[Hacker News](https://news.ycombinator.com)や[Reddit.com](https://www.reddit.com) などを使うのが良いらしい．

* [あなたのプロジェクトのユーザーを見つけよう](https://opensource.guide/ja/finding-users/)

* [前へ](development.md)
* [次へ](terms.md)
