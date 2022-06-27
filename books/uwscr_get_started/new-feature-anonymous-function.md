---
title: "新機能: 無名関数"
free: true
---

UWSCRでは無名関数を定義できるようになりました。

# 無名関数定義

`function`/`procedure`の関数名を省略し引数で受けることで無名関数を作ることができます。
引数や処理部分の書式は通常の関数定義と同等です。

```
変数 = function([引数, ...])
    // 処理
fend
変数 = procedure([引数, ...])
    // 処理
fend
```

使用例

```stylus
f = function(a, b)
    result = a + b
fend

print f(3, 5) // 8
```

# 関数式

無名関数は関数式[^1]でも定義できます。
引数の書式は通常の関数定義と同等です。
通常の無名関数と違い処理部分に文が書けず、式のみが記述可能です。
複数の式を書く場合は`;`で区切ります。
最後の式が返す値が戻り値となり、`result`は省略できます。


```
変数 = |[引数, ...] => 式|
変数 = |[引数, ...] => 式; 式; ...|
```

使用例

```stylus
f = |a, b => a + b|
print f(3, 5) // 8

// 引数なし
f = |=>1|
print f() // 1
```

# 無名関数の即時実行

無名関数は即時実行できます。

```stylus
print |a, b => a * b|(3, 5) // 15

print function(a, b)        // 15
    result = a * b
fend(3, 5)
```

# クロージャ

無名関数は定義時点でのローカルスコープを引き継ぐという性質があります。

```stylus
foo = 5
f = function(n: number)
    // この時点でのfooを引き継ぐ
    result = n * foo
fend

print f(3) // 15; 3 * 5 を返す

// fooを書き換えても反映されない
foo = 10
print f(3) // 15; 関数内のfooは5のままなので30にはならない
```

このように関数定義外のローカル変数を保持した関数をクロージャと呼びます。
以下のようにクロージャを返す関数を作ることもできます。

```stylus
function enclosure(n: number)
    // 関数enclosureが受けた引数nを保持したクロージャを返す
    result = |m: number => n * m|
fend

f1 = enclosure(5)  // f1のnは5
print f1(3)        // 15; 5 * 3 を返す
print f1(4)        // 20; 5 * 4 を返す
f2 = enclosure(10) // f2のnは10
print f2(3)        // 30; 10 * 3 を返す
print f2(4)        // 40; 10 * 4 を返す
```

[^1]: C#のラムダ式や、JavaScriptのアロー関数のようなもの