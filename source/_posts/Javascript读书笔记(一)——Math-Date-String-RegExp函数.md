---
title: 'Javascript读书笔记(一)——Math,Date,String,RegExp函数'
header-img: "header.jpg"
date: 2016-05-21 23:32:57
categories:
 - Javascript
tags:
 - Javascript
 - 读书笔记
---

还不曾系统地学过Javascript, 也就是会点jQuery, 勉强够用, 现在在读《Javascript权威指南》, 顺便做下读书笔记。
说的够文艺, 其实就是copy书里的代码了。

下面是一些常用的Math,Data,String,RegExp函数

* ### Math
    ```Javascript
    Math.pow(2, 53)     //2的53次幂
    Math.pow(3, 1/3)    //3的立方根
    Math.round(.6)      //1.0 四舍五入
    Math.ceil(.6)       //1.0 向上取整
    Math.floor(.6)      //0.0 向下取整
    Math.abs(-5)        //5 绝对值
    Math.max(x,y,z)     //最大值
    Math.min(x,y,z)     //最小值
    Math.random()       //返回一个大于0 小于1.0的伪随机数
    Math.PI             //圆周率
    Math.E              //自然对数的底数
    Math.sqrt(3)        //3的平方根
    Math.sin(0)         //三角函数 Math.cos,Math.atan
    Math.log(10)        //10的自然对数
    Math.log(100)/Math.LN10 //以10为底100的对数
    Math.log(512)/Math.LN2  //以2为底512的对数
    Math.exp(3)         //e的3次幂
    ```
* ### Data
    ```Javascript
    var then = new Date(1990, 4, 3);    //1990年5月3日
    var later = new Date(1990, 4, 3, 18, 24, 13);   //1990年18点24分13秒
    var now = new Date();   //当前日期和时间
    var elapsed = now - then;   //计算时间间隔的毫秒数
    later.getFullYear() //2011
    later.getMonth()    //4 以0为起点的月份
    later.getDate()     //3 从1为起点的天数
    later.getDay()      //4 0为星期日 4代表星期日
    later.getHours()    //18 小时
    later.getUTCHours() //用UTC表示小时的时间
    ```
* ### String
    ```Javascript
    var s = "hello, world!"
    s.charAt(0)     //"h" 第一个字符
    s.charAt(s.length - 1)  //"d" 最后一个字符
    s.substring(1, 3)       //"el" 第2~3个字符
    s.slice(1, 4)           //"ell" 第2~4个字符
    s.indexOf("l")          //2 字符“l”第一次出现的位置
    s.lastIndexOf("l")      //10 字符"L"最后一次出现的位置
    s.indexOf("l", 3)       //3 字符“l”在位置3及之后首次出现的位置
    s.split(', ')           //["hello", "world"] 分割字符串
    s.replace("h", "H")     //"Hello, world" 替换
    s.toUpperCase()         //"HELLO, WORLD" 全转大写
    ```
* ### RegExp
    ```Javascript
    var text = "testing: 1, 2, 3";
    var pattern = /\d+/g    //匹配一个或多个数字实例
    pattern.test(text)      //true 匹配成功
    text.search(pattern)    //9 首次匹配成功的位置
    text.match(pattern)     //["1", "2", "3"] 所有匹配的结果数组集
    text.replace(pattern, "#")   //"testing: #, #, #"
    text.split(/\D+/);      //["", "1", "2", "3"] 使用非数字分割字符串
    ```
