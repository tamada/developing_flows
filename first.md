# プログラムを書き始める前に

何か書きたいソフトウェアがあるならば，プログラムを書き始める前に次のことを決める必要がある．

* ソフトウェアの名前を決める．
* ソフトウェアのライセンスを決める．
* ソフトウェアのアイコンを決める．
* ソフトウェアの概要を書く．
* ソフトウェアの外部仕様を決める．
* リポジトリをGitHubに作成し，各種ファイルを追加する．

順番に説明する．

## ソフトウェアの名前を決める

まず，ソフトウェアの名前を決める必要がある．
この名前はGitHubなどのプラットフォーム上でプロジェクトを区別するための識別子（Identifier）となる．
そのため，ソフトウェア開発を始める前に真っ先に決めるべき事項と言える．

* パターン1: そのソフトウェアが行うことがわかるような名前をつける．
  * そのものズバリである．`head`や`tail`,` tee`, `find`などもこのパターン1に当てはまるだろう．
* パターン2: やりたいことの頭文字を取って名付ける（頭字語，acronym）のも良い．
  * その略語が既存の単語と一致する場合（[アプロニム，apronym](https://ja.wikipedia.org/wiki/%E9%A0%AD%E5%AD%97%E8%AA%9E#%E3%82%A2%E3%83%97%E3%83%AD%E3%83%8B%E3%83%A0)と呼ぶらしい）や，[再帰的頭字語](https://ja.wikipedia.org/wiki/%E9%A0%AD%E5%AD%97%E8%AA%9E#%E5%86%8D%E5%B8%B0%E7%9A%84%E9%A0%AD%E5%AD%97%E8%AA%9E)だと格好良いが，Linux (Linux is not Unix) や Wine (Wine is not emulator) みたいな名前はそうそう出てこない．出てくると儲けもの程度に思っておくと良い．
  * `grep`（global regular expression print）や[`ripgrep`](https://github.com/BurntSushi/ripgrep)（Ri.I.P grep），cat（concatnate）などが当てはまる．
* パターン3: そのソフトウェアと関連の深い名詞や動詞など．動物や食べ物などの名前を適当につけるのも良い．関連が説明できれば良い．
  * [Docker](https://www.docker.com/), [夜フクロウ](https://sites.google.com/site/yorufukurou/)など．
* パターン4: 自分の名前や対象のもののアナグラムや逆順なども良いかもしれない．
  * 著者のファミリーネーム，玉田（tamada）を逆順にすると adamatとなる．adamasを連想させ，硬そうなイメージを受ける．
* パターン5: 適当．これまでのパターンに当てはまらないもの．

### 著者が作成したソフトウェアの名前

* [rrh](https://github.com/tamada/rrh)（パターン2）
  * Remote Repositories Head/Repositories, Ready to Hack の略としているが，実は Red Riding Hood の略でもある．短くて，打ちやすくて気に入っている．
* [pochi](https://github.com/pochi)（パターン3）
  * ソフトウェアの盗用を検出するソフトウェア．花咲爺の「ここほれワンワン」からの連想である．
    ただ，名前を付けた後，花咲爺の犬の名前はシロだったことに気付いた．
* [omelette](https://github.com/tamada/omelette)（パターン3）
  * 使い捨てプロダクトとして作成したものが，結構メンテナンスを続けている．
    着想して，作り始めた時に食べたお昼ご飯がオムレツだったことから．
* [purplecat](https://github.com/tamadalab/purplecat)（パターン3）
  * 全くプロダクトの機能と名前に関係がない．プロジェクトのビルドファイルから依存ライブラリとそのライセンスを抽出するという機能を持つ．
  * 名前の由来は，Eic Carlの絵本[Brown Bear, Brown Bear,What do you see](https://www.amazon.co.jp/dp/0141501596)から．開発当時，子供がこの本が好きでよく読み聞かせていたから．
* [9rules](https://github.com/tamada/9rules)（パターン1）
  * ひと昔流行ったオブジェクト指向エクササイズの遵守度を計測するツール．
  * オブジェクト指向エクササイズが9つのルールを挙げているところから．
  * 数値から始まっている点で ninerules と呼称しなければならないケースがあるため，あまり良い名前ではない．
* [fritter](https://github.com/tamada/fritter)（パターン3）
  * これも見事にプロダクトの機能と名前に関係がない．9rulesの後継．
  * 作ろうとしているときにエビのフリッタが喰いてぇなぁと思ったところから．

見事に何をしているプロダクトか名前からはわからない．
しかし，自分の中で定着すれば良いと考える．

### 参考リンク

* [社内システムの名前の決め方とアンチパターン集](https://www.cycle-g.info/entry/2017/04/27/%E7%A4%BE%E5%86%85%E3%82%B7%E3%82%B9%E3%83%86%E3%83%A0%E3%81%AE%E5%90%8D%E5%89%8D%E3%82%92%E4%BB%98%E3%81%91%E3%82%8B%E3%81%9F%E3%82%81%E3%81%AE%E3%83%8D%E3%82%BF%E5%B8%B3)
* [Webサービスの名前をつける時のアイデアいろいろ](https://www.webcreatorbox.com/webinfo/web-service-name-idea)
* [プロダクトに名前をつける時に気をつけたいこと](https://qiita.com/dtan4/items/639928bcfc6ac0a69a57)

## ソフトウェアのライセンスを決める

まず，これから作成するソフトウェアをOSSとするかどうかを決める．OSSとする場合は，ソースコードを公開し，改変も自由となることを認める必要がある．

なお，OSSにする場合次のことに注意する必要がある．

* 利用される分野を制限できない．
  * つまり，軍事関係や商用利用を妨げられない．
* 販売は可能である．
  * ただし，販売した先の人が無償で配布することを妨げられない（OSSは再配布の自由を謳っているため）．

### OSSにする場合

[OSIが認めたOSSライセンス一覧](https://opensource.org/licenses)の中から，ライセンスを決めると良い．独自のOSSライセンスを定めようと思っても，OSSとしての抜けが出てくるし，利用者にそのライセンスの理解を要求することになる．つまり，使いにくいソフトウェアとなる．そのため，既存のものを利用する方が良い．

ライセンスのコンフリクトの問題（利用できるライブラリが制限される場合がある）はあるものの，基本的には次のことを考えた上で選択すれば良い．

* 著作権を放棄するか
* このソフトウェアが他の人に拡張される時に，ライセンスの保持を望むか．
* 著作権は保持しつつも，ライセンスの保持は望まない．

[Creative Commons](https://creativecommons.org/)のように意思を選択した上でライセンスが決まれば良いが，似たようなライセンスがたくさんあるため，一つに絞りきれないのも難しいところである．
しかし，[Choose an open source license](https://choosealicense.com)というサイトもあり，選択が容易になってきている．

#### 著作権を放棄するか

ソフトウェアを利用する立場の人に制限を付けない場合，著作権の放棄を選択することになるであろう．ただし，[日本の法律では著作権の放棄についての概念がない](http://ousar.lib.okayama-u.ac.jp/files/public/1/15058/20160527210054186555/027_193_212.pdf)らしい．それならば，ライセンスで明示しようということで，次のようなライセンスがある．

実際に利用する時には，ライセンスの原文を参照した上で利用されたい．とはいえ，著名な団体（Creative Commons）が出しているライセンスであるため，CC-0 を使うのが無難かもしれない．

* [CC-0](https://creativecommons.jp/sciencecommons/aboutcc0/)
  * Creative Commonsのライセンスの一つ．いかなる権利も主張しないライセンス．
  * GPL-Compatible，FSF Free/Libre
* [WTFPL](https://ja.wikipedia.org/wiki/WTFPL) (Do What The Fxck You Want To Public License)
  * このライセンス条項「You just DO WHAT THE FxCK YOU WANT TO.」にある通り，「好きに利用したらいいんだよ」というライセンス．
  * GPL-Compatible，FSF Free/Libre
  * http://www.wtfpl.net/
* [NYSL](http://www.kmonos.net/nysl/) （煮るなり焼くなり好きにしろライセンス）
  * ライセンス名の通り，好きに利用したら良いよ，というライセンス．
  * ただし，世界的にはそれほど知られていない．

著作権を主張しない，ということはこれから作成するソフトウェアがどのように使われても文句は言えない，ということである．

* 例えば，自分が作成したソフトウェアを別の人物が自分が作成したものとして公開したとしても，文句が言えないということである．
  * ただ，この例の場合でも，自分が作成したソフトウェアが公開されているため，誰が作成したのか，第三者から見ると明らかではある．

#### このソフトウェアが他の人に拡張される時に，ライセンスの保持を望むか

ソフトウェアが他の人に拡張されるとき，というのは，自分の作成したソフトウェアをもとにして，第三者が別のソフトウェアを作成することである．この場合にライセンスを変更して欲しくない場合，[コピーレフト](https://www.gnu.org/licenses/copyleft.ja.html)のソフトウェアとして公開すると良い．コピーレフトとなるライセンスを付与してソフトウェアを公開した場合，例え作成者本人であったとしても，コピーレフトをやめるのは不可能である点に注意されたい．

* [GNU General Public License version 3 (GPLv3)](https://www.gnu.org/licenses/gpl-3.0.ja.html)
  * コピーレフトのライセンスといえばこれ．
* [Lesser GNU General Public License version 3 (LGPLv3)](https://www.gnu.org/licenses/lgpl.html)
  * GPLv3 よりも緩いフリーソフトウェアのライセンス．
* [BB-BY-SA 3.0](https://creativecommons.org/licenses/by-sa/3.0/)
  * Creative Commonsによるコピーレフトのライセンス．ソフトウェア以外にも利用可能なライセンス．

#### 著作権は保持しつつも，ライセンスの保持は望まない

この場合，フリーソフトウェアのライセンスを付与することになる．以下のいずれも，再配布，修正自由であり，改変して公開する場合は，利用者が別のライセンスを付与できる．ただし，著作権は保持しているため，別のライセンスで公開されたとしても，自分の書いた部分の著作権は保持される．

* [MIT License](https://opensource.org/licenses/MIT)
  * [GitHubで一番多く使われているライセンスらしい](https://github.blog/2015-03-09-open-source-license-usage-on-github-com/)．
* [Apache License 2.0](https://apache.org/licenses/LICENSE-2.0)
  * GitHubでMIT, その他，GPLv3に次いで使われているライセンス．

### OSSにしない場合

自分の作成したソフトウェアを，商用や軍事関係，特定の誰かに利用されたくない場合は，OSSではない道もある．この場合，自分でライセンス文書を書くことになる．この時，ライセンスとは開発者とユーザとの間で交わす契約書（使用許諾書）である，ということに気をつける必要がある．つまり，契約書のトラブルが起こらないよう注意を払って文書を作成する必要がある．[AI-CON](https://ai-con.lawyer/)のようなサービスが利用できるかもしれない．

GNUの言う[形式ばらないライセンス](https://www.gnu.org/licenses/license-list.html#informal)で色々な条項を書くことになるのかもしれない．
しかし，書いた文書がライセンスであると認められるかどうかは利用者の国の法律に従い，言い回しの問題もあり，期待通りに受け取られるかわからない．

これらのことから，著者はできるだけ避けた方が良いと考える．

### 参考リンク

* 可知豊の『 わかっておきたい、オープンソースライセンス』
  * [第1回 著作権とライセンスをわかっておきたい](https://tech-lab.sios.jp/archives/what-is-oss-license-01)
  * [第2回 色々なオープンソースライセンスをわかっておきたい](https://tech-lab.sios.jp/archives/what-is-oss-license-02)
  * [第3回 オープンソースライセンスの使い方をわかっておきたい](https://tech-lab.sios.jp/archives/what-is-oss-license-03)

* [今日から始めるOSSライセンス講座](https://thinkit.co.jp/series/5150)

* [Githubによる、オープンソースライセンスの選び](https://www.catch.jp/oss-license/2013/09/10/github/)
* [ちょっとユニークなライセンスたち・まとめ](https://qiita.com/hakatashi/items/eb9f7484e2d23096eb14)
* [SPDX License List](https://spdx.org/licenses/)

## ソフトウェアのアイコンを決める

必須ではないが，そのプロジェクトの顔とも言えるアイコンを決めるのが良い．このアイコンは先に決めたプロジェクト名と一致するものが望ましい．ただし，画像の著作権について注意する必要がある．

アイコンはSVGで作成するか，いくつかの大きさを用意するのが良い．アイコンは，GUIソフトウェアの場合はアプリケーションアイコンとして利用されるほか，Webサイトなどで利用し，ソフトウェアの顔として利用する．

著者の場合，[freesvg.org](https://freesvg.org/)などで公開されている画像を用いる場合や，自作の場合がある．

* [rrh](https://tamada.github.io/rrh/about/#-attributions)
  * [www.iconpon.com](https://www.iconpon.com/)で作成した画像を利用している．
* [pochi](https://tamada.github.io/pochi/about/#-icon-of-pochi)
  * 折り紙で犬を作成し，撮影したものを用いている．
* [omelette](https://tamada.github.io/omelette/about/#-attributions)
  * [www.flaticon.com](https://www.flaticon.com/) で公開されている画像を用いている．
* [purplecat](https://tamadalab.github.io/purplecat/about/#-logo)
  * [pixy.org](https://pixy.org/) から取得した画像を利用している．
* [9rules](https://tamada.github.io/9rules/about/#jack_o_lantern-icons-of-9rules)
  * Boxy SVGで自作した．

## ソフトウェアの概要を書く

`ソフトウェア名/README.md`を用意し，概要を書く．この概要は，1行のキャッチフレーズ的なもの（tagline）となぜこれが必要なのか，何をするものなのかの背景を含めた概要の2つを書く．次のような内容の`README.md`を作成することになる．

```markdown: README.md
# ソフトウェア名

1行概要（tagline）

## Description

ここを書く．３，４行で
```

ここで書いたものは様々なところで公開することになる．

* 例えば，tagline はGitHubのプロジェクトページのAboutに同様のものが掲載されることになる．
* WebページにもDescriptionと同等のものが記載されることになろう．

書き終えたら終わりではなく，節目節目に振り返り，修正していくことになる．

## ソフトウェアの外部仕様を決める

引き続き，`README.md`を編集し，`Usage`の節を書く．具体的な入力とそれに対する出力をデモとして書いても良い．重要なのは，これから作成するソフトウェアのゴールを明らかにすることである．

もちろん，開発を続ける間に多少変わってくることもある．しかし，最初の段階で何を受け取り，どのようなオプションを設けるのかは決めておく必要がある．

また，出力形式も定めておくと開発しやすくなる．どのような形式で出力するのか，出力項目がなんなのかなどである．

### CLIコマンドの場合

`--help`コマンドで表示されるヘルプを記載する．特に引数として何を受け取るのかを明確にする．

#### コマンドライン引数

受け取るフォーマットごとに考えておくべきことについて記しておく．

* ファイルの場合
  * 特定のファイル形式のみなのか，ファイルなら何でも良いのか．
* ディレクトリの場合．
  * ディレクトリを指定した場合，ディレクトリそのものを対象にするのか，ディレクトリ内のファイルを全て指定したことになるのか．
    * ディレクトリを掘り進めて全てのファイルを対象にするのか．
* URLの場合
  * スキーマは省略可能か．
* 特定の文字列の場合
  * 文字列のフォーマットが示されているか．
  * どこが省略可能か．

### RESTful アプリケーションの場合

endpointのURLと有効なリクエスト，レスポンスについて記載する．

### 出力形式

ソフトウェア独自の形式なのか，JSONなのか，YAMLなのか，また，どのような項目があるのかを例を用いて記すとよい．

## リポジトリをGitHubに作成し，各種ファイルを追加する

名前，ライセンス，アイコン，概要，外部仕様の5つを決めたらようやくGitHubにリポジトリを作成し，各種ファイル，`LICENSE`，`README.md`，`.gitignore`を追加する．

この段階でコミットして，pushしておくと良い．

### `.gitignore`

`.gitignore`は手作業で作成するのではなく，[`gibo`](https://github.com/simonwhitaker/gibo)を使う．

ただし，自動生成されるものは `.gitignore` に手作業であっても追加しておく．