---
title: 升级到MySQL8.0使用中遇到的问题汇总
date: 2018-06-25 14:51:34
tags:
 - MySQL
categories:
 - DB
 - MySQL
---

### Every thing is new 
 
新装的主机当然什么都要用最新的, `Ubuntu18.08`, `php7.2`, `MySQL8.0`
`MySQL8.0`性能较`5.x`的版本还是有很大提升的，尤其是`NoSQL`的支持也值得一试
本文记录的就是这个`MySQL8.0`踩的坑

### 默认安装

```shell
sudo apt-get install mysql-client mysql-server
```
这个默认安装的版本在当前是5.7
而5.7适配版本只有`Ubuntu17.04`

### 升级安装
安装最新版本的`MySQL8.0`需要额外安装一个资源库
[MySQL-apt-config_0.8.10-1_all.deb](https://dev.mysql.com/downloads/repo/apt/ "Ubuntu / Debian (Architecture Independent), DEB Package")

```shell
sudo dpkg -i mysql-apt-config_0.8.10-1_all.deb
sudo apt-get update
sudo apt install mysql-client mysql-server
```

重新安装`MySQL`的过程中会选择加密方式(建议选择旧版)
这里需要重点说明一下, 参考官方说明 
[How to Reset the Root Password](https://dev.mysql.com/doc/refman/8.0/en/resetting-permissions.html) 

旧版本的加密字段原本为 `mysql.user`的 `password` 字段, 8.0改为`authentication_string`
旧版本的`password()`也废弃了
所以更改密码的`SQL`变为
```shell
mysql> ALTER USER 'root'@'localhost' IDENTIFIED BY 'new_password';
```

到这里采用PDO调用会发现报错
```log
The server requested authentication method unknown to the client 
[caching_sha2_password]
```
有可能旧有的图形化管理的工具不支持8.0版本的加密方式
旧版本的加密方式为`mysql_native_password`, 8.0 改为 `caching_sha2_password`
需要再进行一步处理
```shell
shell>vim /etc/mysql/my.conf
```
在文件中加入以下代码,将加密方式更改为老版本的
```mysql.conf
[mysqld]
default_authentication_plugin=mysql_native_password
```

### 敲黑板！！划重点！！
到这里还不能使用新版本的加密账户
需要将以前的用户更新, 或者新建用户, 操作方法见以上官方链接

↖(▔^▔)↗ 以上 ↖(▔^▔)↗ `Enjoy Coding...`

