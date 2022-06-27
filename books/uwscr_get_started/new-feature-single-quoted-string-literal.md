---
title: "新機能: シングルクォーテーション文字列リテラル"
free: true
---

UWSCの文字列リテラルは`"`(ダブルクォーテーション)で括ったもののみでしたが、UWSCRではそれに加えて`'`(シングルクォーテーション)で括るものが存在します。

```stylus
print "abc" // abc
print 'abc' // abc
```

これらの違いは文字列中の`<# >`表記を展開するか否か、です。

```stylus
// "" では展開される
print "<#DBL>foo<#DBL>" // "foo"
// '' では展開されない
print '<#DBL>foo<#DBL>' // <#DBL>foo<#DBL>
```