---
title: ubuntu安装Redis
date: 2016-06-13 16:29:42
tags:
 - Redis
categories:
 - DB
 - Redis
---
### 以下是安装步骤:
1. 以管理员身份进入 `/usr/` 目录
```shell
$ sudo su
# cd /usr/
```
2. 安装 `Redis` 服务
```shell
# apt-get install redis-server
```
3. 安装完成后，服务会自动启动。检查 `Redis` 服务器程序
```shell
# ps -aux|grep redis
```
4. `Redis` 默认端口号6379, 检查 `Redis` 服务器状态
```shell
# netstat -nlt|grep 6379
```
5. 命令行启动客户端程序
```shell
$ redis-cli
```
对于那些不习惯用命令行的同学，推荐一款 `Redis` 可视化图形管理工具 [`Redis Desktop Manager`](https://github.com/uglide/RedisDesktopManager/ 'Redis Desktop Manager') ,支持 `Mac OS X` ， `Windows` , `Ubuntu` 还有源码安装。
