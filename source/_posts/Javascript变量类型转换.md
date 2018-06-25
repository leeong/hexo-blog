---
title: Javascript变量类型转换
header-img: "header.jpg"
date: 2016-05-26 20:10:36
categories:
 - Javascript
tags:
 - Javascript
 - 读书笔记
---
1. **类型转换**
    ```Javascript
    x + ''      //等价于 `String(x)`
    +x          //等价于 `Number(x)` 也可以写成 `x-0`
    !!x         //等价于 `Boolean(x)`
    ```
2. **toString()将数字转换成字符串**
    ```Javascript
    var n = 17;
    binary_string = n.toString(2);          //转换为二进制 "10001"
    octal_string = "0" + n.toString(8);     //转换为八进制 “021”
    hex_string = "0x" + n.toString(16);     //转换为十六进制 "0x11"
    ```
3. **Number类定义的方法将浮点数转换为字符串**
    ```Javascript
    //toFixed()         根据小数点后的指定位数将数字转换为字符串
    //toExponential()   使用指数计数法将数字转换为指数形式的字符串
    //toPrecision()     根据指定的位数将数字转换成字符串，有效数字小于整数部分，则转换为指数形式
    var n = 123456.789;
    n.toFixed(0);       //  "123456"
    n.toFixed(2);       //  "123456.78"
    n.toFixed(5);       //  "123456.78900"
    n.toExponential(1); //  "1.2e+5"
    n.toExponential(3); //  "1.235e+5"
    n.toPrecision(4);   //  "1.235e+5"
    n.toPrecision(7);   //  "123456.8"
    n.toPrecision(10);   //  "123456.7890"
    ```
4. **parseInt() & parseFloat()**
    ```Javascript
    //parseInt()        只解析整数
    //parseFloat()      只解析浮点数
    //都会跳过前导空格 尽可能解析更多数值字符 并忽略后续内容 如果第一个字符非法数字直接量 返回NaN
    parseInt("3 bind mm")       //  "3"
    parseFloat("3.14 meters")   //  "3.14"
    parseInt("-12.23")          //  "-12"
    parseInt("0xFF")            //  "255"
    parseInt("0xff")            //  "255"
    parseInt("-0xFF")           //  "-255"
    parseFloat(".1")            //  "0.1"
    parseInt(".1")              //  NaN: 整数不能以.开头
    parseFloat("$132.1")        //  NaN: 数字不能以$开头
    //parseInt()        可以接受第二个参数，即制定数字转换基数
    parseInt("11", 2)           //  "3" ( 1 * 2 + 1 )
    parseInt("ff", 16)          //  "255" ( 15 * 16 + 15 )
    parseInt("zz", 36)          //  "1295" ( 35 * 36 + 35 )
    parseInt("077", 8)          //  "63" ( 7 * 8 + 3 )
    parseInt("077", 10)         //  "77" ( 7 * 10 + 7 )
    ```
