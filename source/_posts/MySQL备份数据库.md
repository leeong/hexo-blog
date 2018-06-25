---
title: MySQL备份数据库
date: 2016-05-20 14:40:54
tags:
 - MySQL
 - 备份
categories:
 - DB
 - MySQL
---

### 备份MySQL数据库的命令

1. **备份MySQL数据库为带删除表的格式，能够让该备份覆盖已有数据库而不需要手动删除原有数据库。**
    ```shell
    $ mysqldump -hhostname -uusername -ppassword databasename > backupfile.sql
    ```
    **等同于**
    ```shell
    $ mysqldump --add-drop-table -uusername -ppassword databasename > backupfile.sql
    ```
    **即在 `CREATE TABLE` 前 `DROP TABLE IF EXISTS TABLE_NAME`**
2. **备份MySQL数据库为不带删除表的格式。**
    ```shell
    $ mysqldump --skip add-drop-table -uusername -ppassword databasename > backupfile.sql
    ```
3. **备份MySQL数据库内一个或多个表**
    ```shell
    mysqldump -hhostname -uusername -ppassword databasename tablename1 tablename2 > backupfile.sql
    ```
4. **将MySQL数据库压缩备份**
    ```shell
    $ mysqldump -hhostname -uusername -ppassword databasename | gzip > backupfile.sql.gz
    $ mysqldump -hhostname -uusername -ppassword databasename | bzip2 > backupfile.sql.bz2
    ```
5. **同时备份多个MySQL数据库**
    ```shell
    $ mysqldump -hhostname -uusername -ppassword --databases databasename1 databasename2 > backupfile.sql
    ```
6. **仅仅备份数据库结构**
    ```shell
    $ mysqldump --no-data --databases databasename1 databasename2 > structurebackupfile.sql
    ```
7. **备份服务器上所有数据库**
    ```shell
    $ mysqldump --all-databases > allbackupfile.sql
    ```
8. **还原MySQL数据库的命令**
    ```shell
    $ mysql -hhostname -uusername -ppassword databasename < backupfile.sql
    ```
9. **还原压缩的MySQL数据库**
    ```shell
    $ gunzip < backupfile.sql.gz | mysql -uusername -ppassword databasename
    ```
10. **将数据库转移到新服务器**
    ```shell
    $ mysqldump -uusername -ppassword databasename | mysql --compress -uusername -ppassword -h*.*.*.* -C databasename
    ```
    **注意：**
    * **如果目的服务器没有该数据库需要添加 `-C`;**
    * **`--compress` 是使用压缩方式传递，可省略;**
