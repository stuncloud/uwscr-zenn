---
title: "新機能: enum-endenum (列挙体の定義)"
free: true
---

enum-endenumは列挙体を宣言するためのブロック構文です。
列挙体はグローバル定数として定義されます。

```
enum 列挙体名
    定数名
    定数名
    […]
endenum
```

列挙体のメンバには数値(0から)が割り当てられます

```stylus
enum e
    foo
    bar
    baz
endenum

// 0から順に割り当てられる
print e.foo // 0
print e.bar // 1
print e.baz // 2
```

また、各メンバには任意の数値を割り当てることができます。

```stylus
enum e
    foo = 100
    bar = 200
    baz = 300
endenum

// 割り当てた数値になる
print e.foo // 100
print e.bar // 200
print e.baz // 300
```

任意割り当てと動的割り当てを混在させることもできます。

```stylus
enum e
    foo = 100
    bar
    baz
endenum

// 1ずつ増えて割り当てられる
print e.foo // 100
print e.bar // 101
print e.baz // 102
```

負の数や、上の値より小さな数値の割り当てはできません。
数値以外の値もエラーになります。

```stylus
enum e
    foo = -1  // 負の数はエラーになる
    bar = 100
    baz = 99  // 上の数が100なのでそれより大きい値(101～)を割り当てないとエラーになる
    qux = "a" // 数値ではないのでエラーになる
endenum
```
