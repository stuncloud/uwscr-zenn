---
title: "値の型について"
free: false
---

# 型の種類

UWSCRにおける値は以下のような型を持っています。

|         型          |                       詳細                       | 参照 |
|---------------------|--------------------------------------------------|------|
| 数値                | double (倍精度浮動小数点型)                      |      |
| 文字列              | 文字列                                           |      |
| 真偽値              | TRUE/FALSE                                       |      |
| 配列                | 要素として異なる値型を格納できる                 |      |
| 連想配列            | 連想配列                                         | ✓    |
| 無名関数            | 名前なしで定義されたfunction/procedure           |      |
| 関数                | 名前ありで定義されたfunction/procedure           |      |
| 非同期関数          | async宣言した関数                                |      |
| 組み込み関数        | 組み込み関数                                     |      |
| モジュール          | module定義                                       | ✓    |
| クラス定義          | class定義                                        |      |
| クラスインスタンス  | `クラス名()`で得られる                           | ✓    |
| NULL                | def_dllにおけるNULL文字(chr(0))、UObjectのnull値 |      |
| EMPTY               | 空の値、場合により空文字や0として扱われる        |      |
| NOTHING             | 空オブジェクト                                   |      |
| 正規表現            | 正規表現パターン                                 |      |
| UObject             | UObject                                          |      |
| 列挙型              | enum定義                                         |      |
| タスク              | 非同期に行われる処理                             | ✓    |
| DLL関数             | def_dll定義                                      |      |
| 構造体              | struct定義                                       |      |
| 構造体インスタンス  | `構造体名()`で得られる                           | ✓    |
| COMオブジェクト     | createoleobj/getactiveoleobj                     | ✓    |
| VARIANT             | COMで使われる値型                                |      |
| SafeArray           | COMで使われる配列                                |      |
| Browserオブジェクト | BrowserControl                                   |      |
| Browser関数         | Browserオブジェクトの関数                        |      |
| Elementオブジェクト | WebElementを示すオブジェクト                     |      |
| Element関数         | Elementオブジェクトの関数                        |      |
| Elementプロパティ   | Elementオブジェクトのプロパティ                  |      |
| ファイルID          | fopen                                            | ✓    |
| バイト配列          | encode                                           |      |

# print対応

いずれの型もprint文等で文字列として評価されます。
例えば配列変数はUWSCではprintできませんでしたが、UWSCRでは可能です。

```stylus
dim arr[] = 1, 2, 3
print arr // [1, 2, 3]
```

# UWSCからの変更点

配列や関数などの値型が追加されたため、UWSCでは不可能だった以下のような記述ができるようになりました。

```stylus
// 配列変数のコピー
dim foo[] = 1, 2, 3
bar = foo // 配列を別の変数にコピー
print bar[0] // 1

// 組み込み関数のエイリアス
mb = msgbox // msgbox関数を別の変数にコピー
mb("hello world!") // msgbox関数が実行される
```