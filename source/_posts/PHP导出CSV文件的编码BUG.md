---
title: PHP导出CSV文件的编码BUG
header-img: "header.jpg"
date: 2016-08-04 16:38:34
categories:
 - PHP
 - Others
tags:
 - 其它
---

1. **BUG描述：**
    今天使用PHP导出CSV文件发现在windows下使用Office excel打开的时候乱码，而用WPS打开却是正常的。

2. **原因：**
    百度了下才知道，是因为创建的文件没有BOM，而Windows就是使用BOM来标记文本文件的编码方式的。需要做的就是在文件的开头加上EF BB BF的字符来告诉系统是UTF-8的文件。下面上代码：

```php
$fileUrl = 'fileName.csv';
$fp = fopen($fileUrl, 'wb');
//添加文件bom头，识别UTF-8编码
fwrite($fp,chr(0xEF).chr(0xBB).chr(0xBF));
fputcsv($fp, $array);
fclose($fp);
//下载文件
$fileName=basename($fileUrl);
header('Content-Description: File Transfer');
header('Content-Type: application/octet-stream');
header('Content-Disposition: attachment; filename='.$fileUrl);
header('Content-Transfer-Encoding: binary');
header('Expires: 0');
header('Cache-Control: must-revalidate, post-check=0, pre-check=0');
header('Pragma: public');
header('Content-Length: ' . filesize($fileUrl));
ob_clean();
flush();
readfile($fileUrl);
unlink($fileUrl);
```
