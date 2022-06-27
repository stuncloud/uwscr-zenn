---
title: "変数及びその宣言"
free: true
---

UWSCRはUWSCと同じく動的型付け言語であり、変数にはあらゆるデータ型を区別なく格納できます。

# 変数の宣言

```stylus
// 宣言の省略
foo = 1 // 存在しない変数に代入を行うと宣言を省略できる

// dimによるローカル変数の宣言
dim bar // 宣言のみ
dim baz = 2 // 値の初期化も行う

// publicによるグローバル変数の宣言
public qux = 3

// constによる定数の宣言及び初期化
// constは必ず初期化しなければいけない
const QUUX = 4

// 一括宣言
// 一つのdim構文で複数の変数を宣言及びその初期化が可能
dim a, b, c = 5, d
// publicやconstでも可
public x, y, z = 6
const S = 7, T = 8, U = 9
```

# 配列宣言

UWSCと同じく `dim 変数名[] (= 初期値)` で宣言(及び初期化)が行なえますが、UWSCRでは **配列リテラル** の使用を推奨します。
配列リテラルについてはデータ型の項で解説します。

```stylus
// 旧来の宣言
dim array[]
dim arr1d[] = 1, 2, 3
dim arr2d[][1] = 4, 5, 6, 7

// 推奨
array = []
arr1d = [1, 2, 3]
arr2d = [ [4, 5], [6, 7] ]
```