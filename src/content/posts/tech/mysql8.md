---
title: M1 Docker 安装 mysql 踩坑
published: 2023-08-06
description: 之前本机安装了mysql 5.7，后面转用 docker 使用
tags: [backend]
image: ''
category: 'tech'
draft: false
lang: ''
---

# 前言

之前使用 mysql 都是本机安装的 5.7 使用。

后面为了方便，转用了 docker，所以一些东西也都迁移过来。

直接按照网上的卸载方式，把 mysql 卸载掉

```bash
sudo rm /usr/local/mysql
sudo rm -rf /usr/local/mysql*
sudo rm -rf /Library/StartupItems/MySQLCOM
sudo rm -rf /Library/PreferencePanes/My*
rm -rf ~/Library/PreferencePanes/My*
sudo rm -rf /Library/Receipts/mysql*
sudo rm -rf /Library/Receipts/MySQL*
sudo rm -rf /var/db/receipts/com.mysql.*
```

运行上述命令之后，再看设置中的 mysql，已经看不到了，正常按照网上来说应该是卸载成功了。

然后进行 docker 安装。

```bash
docker pull mysql/mysql-server:latest

docker run --name mysql -p 3306:3306 -e MYSQL_ROOT_PASSWORD=123456 -d mysql/mysql-server
```

运行之后，通过 navicat 连接，会爆一些奇奇怪怪的错误，网上搜的解决办法一个都用不了！！

比如

> 1146 - Table 'performance_schema.session_variables' doesn't exist

> [HY000][1006] Can't create database 'testdemo' (errno: 48377920)

> 2002 - Can't connect to server on '127.0.0.1' (36)

以上错误，乱七八糟，不过最后发现 navicat 的侧边的 server version 竟然是 5.7

![mysql](/mysql.png)

应该就是没有卸载干净，后来搜索半天资料。

还需要在 bash_profile 中删掉，重启。

成功！
