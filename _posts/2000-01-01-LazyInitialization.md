---
title: LazyInitialization
tags: [object collaboration design]
---

http://martinfowler.com/bliki/LazyInitialization.html

遅延初期化とは、変数（オブジェクト指向の文脈ではクラスのフィールド値）を最初にアクセスしたときに初期化する手法である。基本的には以下のような形になる。

```java
public FooClass Foo {
  get {
    if (_foo = null) _foo = calculateFoo();
    return _foo;
  }
}
```

遅延初期化は、フィールド値の演算に時間がかかる場合や、実際に値が必要になるまで演算をしたくない場合に便利である。つまり、フィールド値を必要としない場面が数多くあったり、オブジェクトを素早く初期化してあとで使ったりする場合に便利なのだ。

これはクライアントがすぐに値を必要としない状況において、応答性を向上させるための最適化手法であることを忘れないでほしい。他の最適化と同様、この手法も、解決すべき重要なパフォーマンス問題が出てくるまで使用しないようにすることだ。

特に遅延初期化は、デバッグが困難になることがある。なぜなら、デバッグ中にフィールド値を見ようとなると、システムの状態を変更する必要があるからだ。それは普通に使っていては起こらないものだ。（ObservableStateは実際の状態は変更しない）プリント文を追加したらバグが消えた（ように見える）状況も起こりうる ——★いつも大きな潰瘍の処方は金曜日の午後なのだ★。