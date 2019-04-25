# [ゼロから学ぶPython](https://kaityo256.github.io/python_zero/)

[リポジトリ(kaityo256/python_zero)](https://github.com/kaityo256/python_zero)

[HTML版](https://kaityo256.github.io/python_zero/)

## この記事について

プログラム初学者がPythonを学ぶための資料にする予定。

## 目的

Pythonをゼロから学び、簡単な機械学習ができるようになることを目指す。Google Colabを使うことで環境構築をせず、ブラウザだけで実習形式で学ぶ。読者としてはプログラムをほとんど触ったことがない学生を想定する。

## はじめに

この講義では、Pythonをゼロから学ぶ。しかし、始める前になぜPythonを学ぶべきなのか？Pythonを学んでどうするのか？について少し伝えたいことがある。

この講義の目的は「これまでプログラムを組めなかった人がプログラムを組めるようになること」ではない。また、Pythonを扱うが、「Pythonをマスターすること」を目的とはしない。そもそも全くプログラムを組んだことがない状態から、半期の講義を受けたらPythonをバリバリ組めるようになる、というのは不可能だ。

では何を目的とするか。それは「これくらいのプログラムを書けば、これくらいのことができるんだなぁ」という「感覚」を身につけることだ。これから短いプログラムから、それなりに長いプログラムを多数組むことになるが、そこで文法とか、ライブラリの使い方などを覚える必要はない。ざっくりと「Pythonにはこんなライブラリがあり、それを使うとわずか数行でこれくらいのことができる」ということを頭の片隅に置いてくれればそれでよい。

なぜプログラムを覚えるべきか。それは今後プログラムが就職活動に必須スキルになるからでもなく、ましてAIがブームだからでもない。「プログラマ的な感覚」を身につけるためだ。たとえ普段プログラムをバリバリ組んでいなくても、「プログラマ的な感覚」を身に着けた人は、そうでない人に比べて作業能力が桁違いに上がる可能性がある。

例を挙げよう。今、あなたは卒論もしくは仕事で、あるフォルダの中にある100枚くらいの画像を全て半分にリサイズする必要が出てきた。とりあえずWindowsユーザだとして、「ペイント」を使ってファイルを開き、「Ctrl+E」でイメージのプロパティを開き、そこで幅と高さを調整して上書き保存できることは知っているとしよう。

ここで、この講義を受けた人は、詳細は覚えていなくとも「少なくともPythonには画像を扱うライブラリがあり、リサイズもできるはずで、またフォルダの中のファイル一覧も簡単に取れるに違いない」と思うだろう。そして「Python 画像 リサイズ」や「Python フォルダ ファイル 一覧」などのキーワードでググって、以下のようなコードを書く。

```py
import glob
from PIL import Image

for file in glob.glob("*.png"):
    img = Image.open(file)
    (w, h) = img.size
    img.resize((w//2, h//2), Image.LANCZOS).save("resized/"+file)
```

カレントディレクトリにあるPNGファイルを、半分のサイズにしては`resized`というフォルダに放り込んでいくスクリプトである。たった6行だ。

もしくは、「これくらいのことならPythonいらないかもしれない」と思って、「画像　リサイズ　一括」というキーワードで検索して、ImageMagickというツールにたどり着くかもしれない。それなら一行でできる。

```sh
mogrify -path resized -resize 50% *.png
```

ここで重要なのは「PythonのglobやPILというライブラリの存在や使い方を覚えていること」でも「ImageMagickというツールを知っていること」でもない。「これくらいのことなら数行でできるに違いない」という感覚である。プログラマ的な感覚を身に着けていない人は、そもそも「これは簡単にできるだろう」という発想がないため、検索もできない。

もしかしたら「プログラムの素養がなくたって画像のリサイズくらいなら自動でできると思いつくだろ」と思うかもしれない。では、こんな課題はどうだろう？

あなたは卒論でトランジスタの特性を調べることになった。それぞれのトランジスタにはあるパラメータがあり、それを変えて作られている。そのトランジスタの電圧ー電流特性が、以下のようなファイルに保存されているとしよう。

```dat
0.0 0.0
0.1 0.01
0.2 0.2
0.3 0.8
...
```

このようなデータが、トランジスタのパラメタを含めて`data_48.dat`といった名前で保存されており、それが100個近くある。トランジスタは、ゲートにかける電圧がある「しきい値」を超えると電流が流れ始める。このデータに適当にフィッティングをかけることで、「しきい値」を求めたいとしよう。ファイルそれぞれのデータにフィッティングをかけて、ファイル名のうしろにある値(この場合は48)をx軸に、しきい値をy軸にしてプロットしたい。

「画像のリサイズ」は一般的なニーズだからツールはあるが、この卒論のテーマはあなたしかやっていないから、当然そんな便利なツールはない。ここで、もしあなたが「プログラマ的な感覚」がなければ、一つ一つエクセルでファイルを開き、スレッショルドを求めて、別のエクセルシートにパラメタとして記入していくかもしれない。そして徹夜で作業して「卒論がんばってる！」と錯覚するかもしれない。しかし、もしあなたが「プログラマ的な感覚」を持っていれば、「これはPythonを使えば、長くても数十行でできるな」と思うはずだ。

くりかえしになるが、必要なのは「知識」ではなく「感覚」である。「`glob`を使ってファイル一覧を取得し、`scipy`の`curve_fit`でフィッティングをかけることができる」ということを覚えておく必要はない。大事なのは「そういうことが簡単にできるはずだ」と思うことで、そう思うことができれば「Python フィッティング」で検索すればすぐに`scipy.curve_fit`にたどり着けるはずだ。

こういった考えは別にPythonに限らない。エクセルを使っていても、面倒な処理を見た時に「これは一括でできるマクロがあるに違いない」と思って探すかどうか。毎日決まった時間に、あるウェブサイトにアクセスして、ある値を読み取らないといけないという「仕事」が与えられた時に、「ウェブサイトにアクセスして値を読み込めるツールがあるに違いない。毎日決まった時間に何かを自動的に実行する方法があるに違いない。それを組み合わせれば良い」と思えるかどうか。これが「プログラマ的発想」である。

こういう発想ができるようになれば、日々の作業効率が飛躍的に向上するのが想像できるであろう。別に全ての作業を自動化する必要はない。プログラムは何かの目的を達成するための手段の一つに過ぎず、プログラムするか、ツールを導入するか、それとも今回は手でやるか、自動化のためのコストと、自動化しなかった時のコストを考えて、その時その時に最適と思える選択をすればよい。

細かい文法などは最初は気にせず、必要に応じて調べれば良い。「Pythonはこういうことができるんだな」「それはこれくらいの作業量でできるんだな」という「感覚」を頭の片隅に残すこと、それを目的として講義を受けて欲しい。

## [Pythonとは](what/README.md)

* プログラミング言語について
* ライブラリとは
* 余談：スクリプト言語とコンパイラ言語
* Pythonのインストール
* Pythonの基本文法

## [Google Colabの使い方とPythonの基礎](hello/README.md) (ほぼ完成)

* Google Colabの使い方に慣れる
* Pythonに触れてみる
* 余談：タッチタイピングについて

## [条件分岐と繰り返し処理1](basic/README.md) (ほぼ完成)

* 組み込み型
* 関数の宣言と利用方法
* for文による繰り返し処理
* if文による条件分岐
* ニュートン法
* 余談：バグについて

## [条件分岐と繰り返し処理2](while/README.md) (ほぼ完成)

* 変数とは何か？
* while文
* Collatz問題
* 余談：数論について

## [リストやタプルの使い方](list/README.md)

* list, tupple, dict, setなど。
* 浅いコピーと深いコピー
* 参照の値渡し
* コッホ曲線
* Pythonらしく書く(内包表記やreduce)

## 文字列、ファイル処理

* 文字列処理
* 正規表現
* ファイル入出力
* コンテキストマネージャ
* 統計処理

## [再帰処理](recursion/README.md)

* 再帰呼び出しとは
* 状態遷移図の可視化
* 木構造の編集
* 余談：エレファントな解法

## [クラスとオブジェクト指向](class/README.md)

* オブジェクト指向とは？
* 割り箸ゲーム
* 余談：オブジェクト指向プログラミングの意義

## Numpyの使い方

* numpyとは？
* SVDを用いた画像圧縮

## [Pythonが動く仕組み](howtowork/README.md)

* コンピュータはなぜ動くのか？
* Pythonが動く仕組み
* 抽象構文木
* dis.dis
* 仮想マシンハック
* 余談：機械がやるべきこと、やるべきでないこと

## [計算量とアルゴリズム1](complexity/README.md)

TODO: 構成を変更中。内容を目次に追随させること

* 計算のオーダー(ランダウ表記)
* 分割統治法
  * [最近点対問題](https://en.wikipedia.org/wiki/Closest_pair_of_points_problem)を題材に
  * ボロノイ図の作成

## 計算量とアルゴリズム2

* 動的計画法
* フィボナッチとメモ化
* ナップザック問題
* 貪欲法
* 最短経路探索とダイクストラ法
* 巡回セールスマン問題


## [乱数を使ったプログラム](random/README.md) (ほぼ完成)

* 疑似乱数とモンテカルロ法
* 余談：疑似乱数とゲーム
* モンティ・ホール問題
* パーコレーション
* 余談：確率の難しさ

## [数値シミュレーション](simulation/README.md) (ほぼ完成)

* 空気抵抗がない場合の弾道計算
* 空気抵抗がある場合の弾道計算
* 反応拡散方程式(Gray-Scott Model)
* 余談：パーソナルスーパーコンピュータ

## 機械学習

* 簡単な機械学習
* 画像認識
* 顔認識

## 参考文献

昨今、ウェブに大量に情報があるため、本など買わなくてもプログラムは独習できると思うかもしれない。しかし、ある程度わかってから見ると、いかにウェブに転がっている情報がいい加減で、薄いかがわかるようになる。特にプログラム言語に関しては誤り、誤解、意味のない文章が大量にあり、それらガラクタをかき分けて重要な情報にたどり着く努力をするよりは、さっさと数千円〜1万円ほど払って古典的名著を購入したほうが早いし有用だ。もちろん本にも当たり外れはあるが、以下は筆者が良いと思った本なので、一つの参考にしてほしい。

### 初学者向け

まったくPythonなどを触ったことが無い人が読む本。

* [入門Python3 Bill Lubanovic (著), 斎藤 康毅  (監修), 長尾 高弘  (翻訳)](https://www.amazon.co.jp/dp/4873117380) プログラムに限らずなにかを学ぶ際、最初は「軽い、薄い」本を読みたくなるが、真面目にやろうとすると、どこかで「重い、厚い」本を読む必要が出てくる。とりあえずオライリーの本を買っておけば間違いない。
* [15時間でわかるPython 集中講座 小田切 篤 (著), 露木 誠  (著)](https://www.amazon.co.jp/dp/4774178926) 全体の構成の参考にした。
* [Chainer Tutorial](https://tutorials.chainer.org/ja/tutorial.html) 機械学習フレームワーク「Chainer」のチュートリアルだが、最初の[Python入門](https://tutorials.chainer.org/ja/src/02_Basics_of_Python_ja.html)はPythonのことが簡潔にまとまっており、初学者におすすめ。

### 中級者向け

Pythonでだいたいプログラムが書けるようになった、もしくは複数のプログラム言語が書けるようになってきた人が読む本。

* [コーディングを支える技術 ~成り立ちから学ぶプログラミング作法 (WEB+DB PRESS plus) 西尾 泰和著](https://www.amazon.co.jp/dp/477415654X) プログラムを構成する要素について、様々な言語にまたがって説明することで「なぜその文法が導入されたのか、廃止されたのか」などを紐解く。一つの言語があらかたマスターできたあたりで読むといろいろ発見があるだろう。

* [リーダブルコード ―より良いコードを書くためのシンプルで実践的なテクニック (Theory in practice)](https://www.amazon.co.jp/dp/4873115655) 文法がわかり、とりあえず「動く」プログラムがかけるようになったら、次は「どのように書くべきか」を気にするべき。この本は読みやすいコード(リーダブルコード)を書くためのテクニックが詰まった古典的名著。手元において、たまに読んでみよう。その度に新たな発見があることだろう。

* [実践的低レイヤプログラミング](https://tanakamura.github.io/pllp/docs/index.html) [tanakamura](https://github.com/tanakamura)さんによる、低レベルプログラムの解説。アセンブリやリンカの解説がある。CやC++をある程度書ける人が読むと新たな発見があることだろう。

### 上級者向け

上級者といっても、別にプログラムがバリバリかけるという意味ではなく、たとえばプログラム書いてご飯を食べるようになっているとか、そういう感じの人が読むと面白いかな、と思う本。

* [闘うプログラマー G パスカル ザカリー (著), 山岡 洋一 (翻訳)](https://www.amazon.co.jp/dp/B00GSHI04M) マイクロソフトでWindows NTを開発した伝説のプログラマー「デイヴィッド・カトラー」の伝記のような本。Windows NTは、文字通りマイクロソフトの命運をかけたプロジェクトだった。「デスマーチ」と気軽に呼ぶのもおぞましい強行軍の描写に、僕は最初吐きそうになった。複数人である程度大きなプロジェクトに携わったことがある人は必読。

### その他参考にしたサイトや書籍

プログラムについて書いた記事や、本稿の題材(元ネタ)となった数学や科学の本など。

プログラムについて。

* [オブジェクト指向と20年戦ってわかったこと @Qiita](https://qiita.com/shibukawa/items/2698b980933367ad93b4) 「オブジェクト指向」について改めて考える良いきっかけになった。
* [「例外」がないからGo言語はイケてないとかって言ってるヤツが本当にイケてない件  @Qiita](https://qiita.com/Maki-Daisuke/items/80cbc26ca43cca3de4e4) 「例外」について改めて考える良いきっかけになった。
* [Pythonの処理系はどのように実装され，どのように動いているのか？ 我々はその実態を調査すべくアマゾンへと飛んだ． @Slideshare](https://www.slideshare.net/utgw/python-73389442) PythonのVMについて参考にした。
* [len が関数になっている理由](https://methane.hatenablog.jp/entry/20090702/1246556675) Pythonが`a.len()`ではなく、なぜ`len(a)`を採用したか(Thanks to yohhoi)。
* [Pythonはどうやってlen関数で長さを手にいれているの？](https://www.slideshare.net/shimizukawa/how-does-python-get-the-length-with-the-len-function) Pythonのlenなどがどのように動作しているか(Thanks to yohhoi)。
* [プログラミングコンテストでの動的計画法](https://www.slideshare.net/iwiwi/ss-3578511) 動的計画法の題材や計算量について参考にした。
* [計算量オーダーの求め方を総整理！ 〜 どこから log が出て来るか 〜](https://qiita.com/drken/items/872ebc3a2b5caaa4a0d0) 計算量の複雑さや題材について参考にした。
* [計算量](https://www.slideshare.net/catupper/ss-26238956) 様々なアルゴリズムの計算量について参考にした。
* [再帰関数を学ぶと、どんな世界が広がるか](https://qiita.com/drken/items/23a4f604fa3f505dd5ad)再帰の考え方の参考にした。

数学や科学について。

* [『フカシギの数え方』 おねえさんといっしょ！ みんなで数えてみよう！](https://www.youtube.com/watch?v=Q4gTV4r0zRs) 日本科学未来館による、組み合わせ爆発を題材としたムービー。8分と短い動画ながら面白いのでおすすめ。
* [数学ガール シリーズ (結城浩 著)](https://www.hyuki.com/girl/) 高校生達の青春ドラマに、数学の楽しさ美しさを織り込んでいったような本。魅力的な登場人物の会話を追いかけているうちに「数学は面白く、そして美しい」ことが実感できると思う。
* [数学をつくった人びと I, II, III (E. T. Bell著、田中 勇、銀林 浩 訳)](https://www.amazon.co.jp/dp/4150502838) 数学という巨大で美しい学問の構築に携わった人々のドラマを描いた本。数学に興味があればもちろん、なくても楽しめる。大変おすすめ。
* [カオス―新しい科学をつくる (ジェイムズ・グリック 著, 大貫 昌子 訳)](https://www.amazon.co.jp/dp/4102361014) 決定論的なしくみから予想不可能な振る舞いが生まれる「カオス」。その「カオス」に立ち向かった人々のドラマ。本講でも頻繁に「カオス」を題材にしているが、それで興味を持った人は読んでみると面白いと思う。おすすめ。
* [複雑系―科学革命の震源地・サンタフェ研究所の天才たち (M. M. Waldrop著、田中 三彦、遠山 峻征 訳)](https://www.amazon.co.jp/dp/4102177213) こちらは「複雑系」という学問(哲学?)を構築した人々のドラマ。全体は部分の和以上のものだろうか？こちらも面白い。

## ライセンス

Copyright (C) 2018-2019 Hiroshi Watanabe

この文章と絵(pptxファイルを含む)はクリエイティブ・コモンズ 4.0 表示 (CC-BY 4.0)
で提供する。

This article and pictures are licensed under a [Creative Commons Attribution 4.0 International License](https://creativecommons.org/licenses/by/4.0/).

本リポジトリに含まれるプログラムは、[MITライセンス](https://opensource.org/licenses/MIT)で提供する。

The source codes in this repository are licensed under [the MIT License](https://opensource.org/licenses/MIT).

なお、HTML版の作成に際し、CSSとして[github-markdown-css](https://github.com/sindresorhus/github-markdown-css)を利用しています。