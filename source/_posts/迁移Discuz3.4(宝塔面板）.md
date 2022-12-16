---
abbrlink: ''
categories: []
cover: https://img.timero.xyz/i/2022/12/16/639c4e3525b78.webp
date: '2022-12-16 18:07:11'
description: 高效迁移Discuz3.4,，不使用官方的备份功能。
tags: []
title: title
updated: '2022-12-16 18:55:04'
---
## 前言

记录一次Discuz的迁移，不使用discuz自带的功能。

## 备份

### 打包网站

将需要备份的网站整体打包，下载到本地。可以使用宝塔面板（我这里使用的是国际版宝塔aapanel，差不多）的备份功能。
![](https://img.timero.xyz/i/2022/12/16/639c45e4b09ee.webp)
别下错了，要下刚刚备份的，注意文件日期。

### 导出数据库

将数据库导出，保存到本地。也可以使用宝塔面板的功能，进phpMyAdmin自己导出也行。这里演示的是使用宝塔面板的。
![](https://img.timero.xyz/i/2022/12/16/639c4762e659d.webp)

## 恢复

在新服务器中安装宝塔面板并新建网站，将刚刚打包的网站上传并解压至新网站目录。
将刚刚导出的数据库重新导入。
![](https://img.timero.xyz/i/2022/12/16/639c4978f2ca7.webp)
进入config/config_global.php，找到下面一段，按照提示将【】替换为自己的内容。

```
$_config['db']['1']['dbhost'] = 'localhost';
$_config['db']['1']['dbuser'] = '【新数据库用户名】'; 
$_config['db']['1']['dbpw'] = '【新数据库密码】'; 
$_config['db']['1']['dbcharset'] = 'utf8'; 
$_config['db']['1']['pconnect'] = '0'; 
$_config['db']['1']['dbname'] = '【新数据库名】'; 
$_config['db']['1']['tablepre'] = 'pre_'; 
$_config['db']['slave'] = ''; 
$_config['db']['common']['slave_except_table'] = '';
```

进入config/config_ucenter.php。

```
define('UC_DBHOST', 'localhost');
define('UC_DBUSER', '【新数据库用户名】');
define('UC_DBPW', '【新数据库密码】');
define('UC_DBNAME', '【新数据库名】');
define('UC_DBCHARSET', 'utf8');
define('UC_DBTABLEPRE', '`【新数据库名】`.pre_ucenter_');
define('UC_DBCONNECT', 0);
```

进入uc_server/data/config.inc.php

```
define('UC_DBHOST', 'localhost');
define('UC_DBUSER', '【新数据库用户名】');
define('UC_DBPW', '【新数据库密码】');
define('UC_DBNAME', '【新数据库名】');
define('UC_DBCHARSET', 'utf8');
define('UC_DBTABLEPRE', 'pre_ucenter_');
define('UC_COOKIEPATH', '/');
```

## 完成

## 后言

简单方便高效，鬼知道我在官方的方法上浪费了多少时间🙂
