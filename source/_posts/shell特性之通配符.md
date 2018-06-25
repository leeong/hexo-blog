---
title: shell特性之通配符
header-img: "header.jpg"
date: 2016-05-25 15:12:58
categories:
 - OS
 - shell
tags:
 - shell
---
向想学 `linux shell` 的同学们推荐一本书 [`TLCL(The Linux Command Line)`](http://book.haoduoshipin.com/tlcl/) 。

正则可谓无处不在, `shell` 里面的文字处理大家应该都在计算机上接触过, 像 `?` 跟 `*` 这样的在计算机课上都有介绍。

平常总会在系统内对文件进行一些批量操作, 光会这俩已经不足以解决问题了。所以适当深化技能还是很有必要的。下面是对shell字符匹配及其应用的一些总结。
来源大部分来自 [`TLCL`](http://book.haoduoshipin.com/tlcl/) ,也有网上的一些摘录, 并都有实际操作。

+ 通配符

| 字符 | 含义 | 实例 |
| --- | --- | --- |
| `*` | 匹配0个或多个字符 | `a*.txt` 匹配以 `a` 开头且格式后缀为 `.txt` 的所有文件 |
| `？` | 匹配任意一个字符（不包括零个） | `a?b` 可以匹配类似 `acb` 或者 `a2b` |
| `[def]` | 匹配 `def` 中的任意单一字符 | `a[def]b` 可以匹配类似 `adb` , `aeb` , `afb` |
| `[!def]` 或 `[^def]` | 匹配除 `def` 外的任意单一字符 | `a[!def]b` 或 `a[^def]b` 可以匹配不是 `adb` , `aeb` , `afb` 的所有 `a?b` |
| `[str1-str2]` | 匹配序列中的单一字符，如[0-9][a-z][A-Z] | `a[0-9]b` 可以匹配 `a0b` , `a1b` …… `a9b` |
| `{str1, str2 ……}` | 匹配 `str1` 或 `str2` (或更多)其一字符串 | `a{de,dd,df}b` 可以匹配 `adeb` , `addb` , `adfb` |

+ 常用的字符类

| 字符类 | 意义 |
| --- | --- |
| `[:alnum:]` | 匹配任意一个字母或数字 |
| `[:alpha:]` | 匹配任意一个字母 |
| `[:digit:]` | 匹配任意一个数字 |
| `[:lower:]` | 匹配任意一个小写字母 |
| `[:upper]` | 匹配任意一个大写字母 |
