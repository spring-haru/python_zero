# ゼロから学ぶPython

## この記事について

プログラム初学者がPythonを学ぶための資料にする予定。とりあえず書きなぐってあとで整形する？

## 目的

Pythonをゼロから学び、簡単な機械学習ができるようになることを目指す。Google Colabを使うことで環境構築をせず、ブラウザだけで実習形式で学ぶ。プログラミング言語としてはPythonを用いるが、適宜他のプログラミング言語を参照することで「ある言語の常識は他の言語の非常識」であり、やりたいことが同じでも実現方法はいろいろあること、プログラミング言語にはそれぞれ固有の哲学があることなどを実感する。読者としてはプログラムをほとんど触ったことがない学生を想定する。

## なにを書こうかな

とりあえず思いつくままに。

* REPLについて
  * ipythonにも触れておく
* コーディングスタイル
  * PEP8の簡単な説明
  * よいプログラムを書くために
  * VCSの説明も軽くしておきたい
* 基本型と文法
  * 型について
  * 変数の問題はリストやタプルの時に再訪したほうが良さそう。
* ファイル入出力、文字列処理
* 例外処理はどうしようかな(多分やらない)
* Chainerやっちゃう？

## [Google Colabの使い方](hello/README.md)

* Google Colabの使い方に慣れる
* Pythonに触れてみる
* 余談：タッチタイピングについて

## [条件分岐と繰り返し処理1](basic/README.md)

* 組み込み型
* 関数の宣言と利用方法
* for文による繰り返し処理
* if文による条件分岐
* ニュートン法
* 余談：バグについて

## [条件分岐と繰り返し処理2](while/README.md)

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

## イテレータ・ジェネレータ・クロージャ

TODO: これだけで90分かける必要ない気がしてきた。要検討。

## オブジェクト指向

* オブジェクト指向とは？
* クラスとオブジェクト
* ダックタイピング

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

TODO: 2回にわける？

* 計算のオーダー(ランダウ表記)
* フィボナッチとメモ化
* 貪欲法
* ナップザック問題
* 最短経路探索とダイクストラ法
* 巡回セールスマン問題

## 計算量とアルゴリズム2

* Union Findアルゴリズム
* ランダムアルゴリズム

## [再帰処理](recursion/README.md)

* 再帰呼び出しとは
* 割り箸ゲーム
* ユニットテスト
* 状態遷移図の可視化
* 木構造の編集
* 余談：エレファントな解法

## [乱数を使ったプログラム](random/README.md)

* 疑似乱数とは
* モンティ・ホール問題
* パーコレーション
* 迷路
* 余談：確率の難しさ

## [数値シミュレーション](simulation/README.md)

* 弾道計算: 抵抗がない場合
* 弾道計算: 抵抗がある場合
* 反応拡散方程式(Gray-Scott Model)

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

### 中級者向け

Pythonでだいたいプログラムが書けるようになった、もしくは複数のプログラム言語が書けるようになってきた人が読む本。

* [コーディングを支える技術 ~成り立ちから学ぶプログラミング作法 (WEB+DB PRESS plus) 西尾 泰和著](https://www.amazon.co.jp/dp/477415654X) プログラムを構成する要素について、様々な言語にまたがって説明することで「なぜその文法が導入されたのか、廃止されたのか」などを紐解く。一つの言語があらかたマスターできたあたりで読むといろいろ発見があるだろう。

* [リーダブルコード ―より良いコードを書くためのシンプルで実践的なテクニック (Theory in practice)](https://www.amazon.co.jp/dp/4873115655) 文法がわかり、とりあえず「動く」プログラムがかけるようになったら、次は「どのように書くべきか」を気にするべき。この本は読みやすいコード(リーダブルコード)を書くためのテクニックが詰まった古典的名著。手元において、たまに読んでみよう。その度に新たな発見があることだろう。

* [実践的低レベルプログラミング](https://tanakamura.github.io/pllp/docs/index.html) [tanakamura](https://github.com/tanakamura)さんによる、低レベルプログラムの解説。アセンブリやリンカの解説がある。CやC++をある程度書ける人が読むと新たな発見があることだろう。

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