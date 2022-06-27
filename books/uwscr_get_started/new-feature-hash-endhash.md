---
title: "新機能: hash-endhash (連想配列定義の糖衣構文)"
free: false
---

連想配列の宣言と初期化を行うための構文です。

```stylus
hash h
    foo = 1   // 左辺は文字列として扱われる
    "bar" = 2 // 左辺は文字列リテラル表記でも良い
    3 = 3     // 通常の連想配列と同じく数値キーも文字列扱いになる
endhash
```

結果はこうです。

```stylus
print h // {"FOO": 1, "BAR": 2, "3": 3}
// 連想配列なので後から要素の追加も可能
h["baz"] = 4
```

先の宣言は以下と同等(シンタックスシュガー)です。

```stylus
hashtbl h
h["foo"] = 1
h["bar"] = 2
h[3] = 3
```

# public宣言

```stylus
// 変数名の前にpublicと書く
hash public p
endhash
```
# 連想配列オプション

```stylus
// 変数名の後に = 定数 と書く
hash o = HASH_SORT or HASH_CASECARE
endhash
```