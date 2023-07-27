---
title: セマンティックdiff
tags: [version control]
---

http://martinfowler.com/bliki/SemanticDiff.html

バージョンコントロールは成果物のバージョン間の違いを理解する
——Unixコマンド名から名前をとって「diff」と呼ばれる。
良いdiff（とmerge）アルゴリズムは、
テキストファイルにもバイナリファイルにも使える。
だがdiffにも難点があって、ちとアホなのよね。
diffがやってるのは2つのバージョンを見比べて、単に違いを出してるだけ。

セマンティックdiffでは変更の結果だけでなく、
変更の「目的」まで理解することになるだろう。

たとえばツールを使い、
あるクラスに対してメソッドの抽出リファクタリングを行ったとしよう。
変更を加えたのはそこだけだ。
現状のツールはプログラム内のテキストの違いは分かる。
しかし、私がリファクタリングを行ったことまでは分からない。
変更の前後でdiffを調べてみると、変更があったことは伝えてくれるが、
これはリファクタリングなんだと伝えるようなことはしてくれない。
私が行ったことがリファクタリングだと分からなければ、
mergeはもっとややこしいことになるだろう。

（一般に受け入れられる別の呼び名があると思ので、もしあったら教えてください。）