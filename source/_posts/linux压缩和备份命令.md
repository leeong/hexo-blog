---
title: linux压缩和备份命令
header-img: "header.jpg"
date: 2016-05-31 10:14:55
categories:
 - OS
 - shell
tags:
 - shell
---
`linux` 下常用管理文件集合的程序主要有
1. 文件压缩程序
    + `gzip` – 压缩或者展开文件
    + `bzip2` – 块排序文件压缩器
2. 归档程序
    + `tar` – 磁带打包工具
    + `zip` – 打包和压缩文件
3. 文件同步程序
    + `rsync` – 同步远端文件和目录

### `gzip`
+ 格式 `gzip [OPTION]... [FILE]...`

| 选项 | 说明 |
| --- | --- |
| `-c` | 把输出写入到标准输出，并且保留原始文件。也有可能用 `--stdout` 和 `--to-stdout` 选项来指定。 |
| `-d` | 解压缩。正如 `gunzip` 命令一样。也可以用 `--decompress` 或者 `--uncompress` 选项来指定。 |
| `-f` | 强制压缩，即使原始文件的压缩文件已经存在了，也要执行。也可以用 `--force` 选项来指定。 |
| `-h` | 显示用法信息。也可用--help 选项来指定。 |
| `-l` | 列出每个被压缩文件的压缩数据。也可用 `--list` 选项。 |
| `-r` | 若命令的一个或多个参数是目录，则递归地压缩目录中的文件。也可用 `--recursive` 选项来指定。 |
| `-t` | 测试压缩文件的完整性。也可用 `--test` 选项来指定。 |
| `-v` | 显示压缩过程中的信息。也可用 `--verbose` 选项来指定。 |
| `-num` | 设置压缩指数。 `num` 1（最快最小压缩）到9（最慢最大压缩）之间的整数。也可以用 `--fast` 和 `--best` 来表示。默认6 |

### `tar` 模式

| 模式 | 说明 |
| :------------- | :------------- |
| `c` | 为文件和／或目录列表创建归档文件。 |
| `x` | 抽取归档文件。 |
| `r` | 追加具体的路径到归档文件的末尾。 |
| `t` | 列出归档文件的内容。 |

`gzip` 使用选项 `z` , 一般用后缀 `.tgz` ，也用 `tar.gz`
```
$ find playground -name 'file-A' | tar czf playground.tgz -T -
```
`bzip2` 使用选项 `j` , 一般用后缀 `.tbz` ，也用 `tar.bz2`
```
$ find playground -name 'file-A' | tar cjf playground.tbz -T -
```
