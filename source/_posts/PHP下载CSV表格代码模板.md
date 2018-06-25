---
title: PHP下载CSV表格代码模板
header-img: "header.jpg"
date: 2016-10-11 09:55:48
categories:
 - PHP
 - Others
tags:
 - 其它
---

前段时间写了一篇[PHP导出CSV文件的编码BUG](/2016/08/04/PHP%E5%AF%BC%E5%87%BACSV%E6%96%87%E4%BB%B6%E7%9A%84%E7%BC%96%E7%A0%81BUG/);
文章中下载的文件是优先缓存的。
下面再记录一份不需要缓存的版本，可以当作导出CSV模板使用。
```php
<?php
$fileName = 'filename' . time() . '.csv';
header('Content-Type: application/csv;charset=utf8');
header("Content-Disposition: inline;filename={$fileName}");
header('Cache-Control: max-age=0');
//echo chr(0xEF).chr(0xBB).chr(0xBF); //bom头(utf8)，避免乱码，需要时添加
$content = '列A,列B,列C,' . "\n";
echo $content;
ob_flush();
flush();
exit();
```
