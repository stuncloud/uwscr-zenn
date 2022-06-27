---
title: "新機能: Module定義の新書式"
free: true
---

Module定義の書式が拡張されました。

# 記述箇所の拡張

関数定義と同様記述箇所がスクリプト本文下部以外でも良くなりました。

```stylus
module m
    public p = 1
endmodule

print m.p // 1
```

# globalの拡張

UWSCRではmodule関数内で `global.定数名` および `global.public変数名` の表記が可能になりました。
UWSC同様 `global.関数名()` の記述も可能です

```stylus
const HOGE = "global const"
public fuga = "global public"

module m
    const HOGE = "module const"
    public fuga = "module public"

    // グローバルスコープにメンバと同名の変数・定数が存在する場合はglobal.変数名でアクセス可能
    procedure p
        print HOGE        // module const
        print fuga        // module public
        print this.HOGE   // module const
        print this.fuga   // module public
        print global.HOGE // global const
        print global.fuga // global public
    fend
endmodule

m.p()
```

# プライベート関数

モジュールメンバのdim宣言 + 無名関数定義によりプライベート関数を定義できるようになりました。

```stylus
module m
    dim private = function()
        result = "private!"
    fend

    function f()
        result = private()
    fend
endmodule

print m.f()       // private!
print m.private() // エラー
```