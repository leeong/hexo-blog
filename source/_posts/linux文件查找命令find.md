---
title: linux文件查找命令find
date: 2016-05-30 10:39:02
categories:
 - OS
 - shell
tags:
 - shell
---
+ **命令格式**
    `find [-H] [-L] [-P] [-Olevel] [-D help|tree|search|stat|rates|opt|exec] [path...] [expression]`
其中，`-H` `-L` `-P` 三个选项主要是用来处理符号连接， `-H` 表示只跟随命令行中指定的符号连接， `-L` 表示跟随所有的符号连接， `-P` 是默认的选项，表示不跟随符号连接。

格式中的 `[expression]` 是一个表达式。最基本的表达式分为三类：设置项 `(option)` 、测试项( `test` )、动作项( `action` )，这三类又可以通过逻辑运算符( `operator` )组合在一起形成更大更复杂的表达式。设置项（如 `-depth,-maxdepth` 等）针对这次查找任务，而不是仅仅针对某一个文件，设置项总是返回 `true` ；测试项( `test` )则不同，它针对具体的一个文件进行匹配测试，如 `-name,-num,-user` 等，返回 `true` 或者 `false` ；动作项( `action` )则是对某一个文件进行某种动作（最常见的如 `-print` ），返回 `true` 或者 `false` 。

+ **操作符&优先级**
    优先级递减；未做任何指定时默认使用 `-and`
```shell
( EXPR )
! EXPR
-not EXPR
EXPR1 -a EXPR2
EXPR1 -and EXPR2
EXPR1 -o EXPR2
EXPR1 -or EXPR2
EXPR1 , EXPR2
```

+ **实例**
    1.  `-name` 属于表达式中的测试项( `test` )，它按照文件名模式来匹配文件，若匹配则返回 `true` ，否则返回 `false` 。最好用引号将文件名模式引起来，防止 `shell` 自己解析要匹配的字符串。
    在文件夹 `/var/www` 中匹配以数字开头，后缀为 `.html` 的文件
    ```shell
    $ find /var/www/ -name "[0-9]*.html"
    ```
    2. `-regex` 同样属于测试项。使用 `-regex` 时有一点要注意： `-regex` 不是匹配文件名，而是匹配完整的文件名（包括路径）。
    在文件家 `/var/www` 中匹配以数字开头，后缀为 `.html` 的文件
    ```shell
    $ find /var/www -regex "./[0-9][a-zA-z]+.html"
    ```

## 妈蛋。写不下去了～～以后再完善吧。
