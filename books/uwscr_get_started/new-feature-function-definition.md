---
title: "新機能: 関数定義の新書式"
free: true
---

UWSCRでは関数定義の書式が拡張されています。

# 記述箇所の拡張

UWSCではスクリプト本文より下に関数定義を書く必要がありましたが、UWSCRではその制限がなくなりました。

```stylus
function f1()
    result = 1
fend

print f1() // 関数定義の下に書いても実行されます
print f2() // 従来通りスクリプト本文下部に書いてもOK

function f2()
    result = 2
fend
```

ただし入れ子になる定義はエラーになります。

```stylus
function f1
    // 入れ子はダメ
    function f2
    fend
fend
```

# resultの省略

`function`定義で`result`を省略できるようになりました。
(`procedure`と同等の動作になります。)
`result`を省略した場合は`EMPTY`を返します。

```stylus
function f
    print 1
fend

f() // 1
```

# refキーワードによる参照渡し

引数に`ref`キーワードを付与することで参照渡しにできます。
これは`var`キーワードのエイリアスです。

```stylus
procedure f(ref a)
    a += 5
fend

n = 10
f(n)
print n // 15
```

# 可変長引数

引数に`args`あるいは`prms`キーワードを付与することで可変長引数にできます。
可変長引数は関数内では配列になります。

```stylus
function f(args v)
    print v
fend

f(1)         // [1]
f(1,2,3,4,5) // [1, 2, 3, 4, 5]
```

可変長引数は最後の引数でなくてはいけません。

```stylus
function f(n, args v) // OK
fend

// 可変長引数のあとに別の引数があるとエラーになる
function f(args v, n) // NG
fend
```

# 引数の型指定

通常の引数、参照渡し、デフォルト引数に対しては受ける型を指定できるようになりました。
関数実行時に異なる型を受けた場合エラーになります。

```
function 関数名(引数名: 型名)
function 関数名(var 引数名: 型名)
function 関数名(引数名: 型名 = デフォルト値)
```

型名には以下を指定できます。

|   型名   |             データ型             |
|----------|----------------------------------|
| string   | 文字列                           |
| number   | 数値                             |
| bool     | 真偽値(TRUE/FALSE)               |
| array    | 配列                             |
| hash     | 連想配列                         |
| func     | 関数 (ユーザー定義、無名関数)    |
| uobject  | UObject                          |
| クラス名 | クラスオブジェクトのインスタンス |

```stylus
function f(str: string)
    result = str
fend

print f("hoge") // OK
print f(123)    // エラー
```

# デフォルト引数の実行時省略表記の拡張

デフォルト引数を持つ関数実行時の引数省略表記が拡張されました。
デフォルト引数を無表記にすることでデフォルト値が使われます。

```stylus
function f(a = 100, b = 200)
    result = a + b
fend

print f() // 300
print f(1) // 201
// 以上は従来通り
// 以下のような書き方ができるようになりました (UWSCではエラーになる)
print f(, 1) // 101
```