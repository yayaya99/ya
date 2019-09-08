---
title: Mysql数据备份与还原
categories: Mysql备份还原
tags:
  - Mysql
abbrlink: 15374
date: 2019-07-21 13:22:26
---
Mysql数据备份与还原
<!--more-->
- ## 数据备份
1.整库备份
	利用mysqldump进行sql备份
	语法：mysqldump.exe -hPup 数据库名字 > 备份路径
	
	mysqldump.exe -hlocalhost -P3306 -uroot -proot mydatabase C:/server/mydatabase.sql
	
2.单表备份 
	语法：mysqldump.exe -hPup 数据库名字 表名 > 备份路径
	
	mysqldump -uroot -proot mydatabase my_int > c:/server/int.sql
	

3.多表备份 
	语法：mysqldump.exe -hPup 数据库名字 表名 表名 .. > 备份路径
	
	mysqldump -uroot -proot mydatabase my_student my_int > c:/server/student_int.sq
	

- ## 数据还原
1.利用mysql.exe客户端 
 	在cmd中直接对数据还原
 	语法：mysql -hPup 数据库 < 文件路径
	
	mysql -uroot -proot mydatabse < c:/server/mydatabase.sql
	

2.利用sql指令
 	登录mysql客户端并进入对应数据库
	语法：source 文件路径（注意后面会有； 因为这里是在mysql中输入的sql指令）
	
	source c:/server/int.sql;
	

3.复制粘贴
