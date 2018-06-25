---
title: 安装java环境遇到的问题
header-img: "header.jpg"
date: 2018-03-26 20:13:56
categories:
 - Tool
tags:
 - 问题
---

今天在`Mac OS`使用`ActiveMQ Apollo`的时候，才发现没装`JDK`。
中间还出了点小波折，`brew`直接安装不了。百度，[`stackoverflow`](https://stackoverflow.com/)最终解决，这里记录一下。

参考[Amazing Code!](https://www.cnblogs.com/lidyan/p/6973492.html);
```shell
brew cask search java   #查询java
brew cask info java     #查询版本
brew cask install java  #安装
java -version           #查看版本 检验安装成功与否
brew caskk uninstall java   #卸载
```

默认安装的最新版本，如果需要安装其他版本，比如`java7`，需要一下命令
```shell
brew tap caskroom/versions
brew cask install java7
```

安装结束后跑`Apollo`命令时遇到以下报错
```shell
$../bin/apollo create mybroker
Error: JAVA_HOME is not defined correctly.
  We cannot execute /System/Library/Frameworks/JavaVM.framework/Home/bin/java
```
是因为环境变量的原因，需要将`java`路径添加到`.bash_profile`文件中
```shell
export JAVA_HOME=$(/usr/libexec/java_home)
export PATH=$JAVA_HOME/jre/bin:$PATH
```
至此，完美结束。
