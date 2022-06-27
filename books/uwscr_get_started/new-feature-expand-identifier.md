---
title: "新機能: 文字列内での変数展開"
free: true
---

UWSCでは文字列リテラル内で特殊文字 (`<#DBL>`, `<#CR>`, `<#TAB>`) の展開が可能でしたが、UWSCRではそれに加えて変数名(識別子)を展開できるようになりました。

```stylus
// <#識別子> が展開される
foo = 123
print "foo is <#foo>" // foo is 123
print `foo is <#foo>` // foo is <#foo> (シングルクォーテーションでは展開されない)
```

現時点で展開可能なのは変数名(識別子)のみで、式は対象外です。

```stylus
bar = [1, 2, 3]
// 配列にインデックスを指定するのはダメ (式なので)
print "bar[0] is <#bar[0]>" // bar[0] is <#bar[0]>
// 一旦別の変数に入れればOK
bar0 = bar[0]
print "bar[0] is <#bar0>" // bar[0] is 1
// 変数名そのものを入れるのであればどのような値でもOK
print "bar is <#bar>" // bar is [1, 2, 3]
```

展開されるのは文字列リテラル評価時に存在する変数名のみです

```stylus
// この時点でfooは存在しないため展開されない
print "foo is <#foo>" // foo is <#foo>
// 定数は実行前に評価されているため展開される
print "bar is <#bar>" // bar is 1

foo = 1
const bar = 1
```