---
title: linux文件查找命令locate
date: 2016-05-30 10:38:53
categories:
 - OS
 - shell
tags:
 - shell
---
`locate` 命令让使用者可以很快速的搜寻系统内是否有指定的文件。其方法是先建立一个包括系统内所有文件名称及路径的数据库，之后当寻找时就只需查询这个数据库，而不必实际深入文件系统之中了。`locate` 数据库由另一个叫做 `updatedb` 的程序创建。通常，这个程序作为一个 `cron` 工作例程周期性运转；也就是说，一个任务在特定的时间间隔内被 `cron` 守护进程执行。大多数装有 `locate` 的系统会每隔一天运行一回 `updatedb` 程序。因为数据库不能被持续地更新，所以当使用 `locate` 时，你会发现 目前最新的文件不会出现。为了克服这个问题，可以手动运行 `updatedb` 程序， 更改为超级用户身份，在提示符下运行 `updatedb` 命令。

+ **命令格式**
    `locate [OPTION]... [PATTERN]...`

+ **命令参数**

| 简拼 | 全拼 | 示意 |
| --- | --- | --- |
| `-A` | `--all` | 打印匹配所有匹配的条目 |
| `-b` | `--basename` | 打印匹配文件名的条目 |
| `-c` | `--count` | 打印匹配文件名的条目 |
| `-d` | `--database DBPATH` | 使用新的locate数据库替代默认数据库(`/var/lib/mlocate/mlocate.db`) |
| `-e` | `--existing` | 只打印现有的文件 |
| `-L` | `--follow` | 打印符号链接指向的条目 |
| `-h` | `--help` | 打印符号链接指向的条目 |
| `-i` | `--ignore-case` | 打印匹配忽略大小写的条目 |
| `-l` | `--limit, -n LIMIT` | 打印匹配数量的的条目 |
| `-P` | `--nofollow, -n LIMIT` | 打印匹配数量的的条目 |
| `-S` | `--statistics` | 不搜索条目，打印统计信息使用的数据库 |
| `-q` | `--quiet` | 安静模式，不会显示任何错误讯息 |
| `-r` | `--regexp REGEXP` | 使用正则匹配 |
| `-w` | `--wholename` | 使用全名称呢个匹配 |
| `-V` | `--version` | 打印版本信息 |
