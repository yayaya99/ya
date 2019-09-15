---
title: 在云服务器下部署Java Web项目
categories: Java Web
tags:
  - Java Web
abbrlink: 53782
date: 2019-09-12 12:18:45
---
在服务器下手动部署Java Web项目

<!--more-->

## 在云服务下部署Java的三种方法
- Java镜像部署
- 一键安装包部署
- **手动部署**

## 手动部署的准备

Java jdk:[Java jdk官方](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)（下载“jdk-序号-linux-x64.tar.gz”版本）

Tomcat：[Tomcat官方下载链接](http://tomcat.apache.org/download-80.cgi)（点击首页左侧Tomcat 8，下载“tar.gz (pgp, md5, sha1)”）

## 安装jdk

1、打开Xshell和Xftp，用Xftp在云服务器创建文件夹

![](https://upload-images.jianshu.io/upload_images/6089846-9c0ab37c7f566143.png?imageMogr2/auto-orient/strip|imageView2/2/w/1200/format/webp)

2、将jdk安装包和tomcat安装包复制粘贴到云服务器对应的文件夹下

3、在Xshell输入指令，解压jdk安装包到指定文件夹

> #tar-zxvf jdk-版本编号-linux-x64.tar.gz-C/usr/java/jdk/

![](https://upload-images.jianshu.io/upload_images/6089846-60aea858d317c8ae.png?imageMogr2/auto-orient/strip|imageView2/2/w/681/format/webp)

4、解压完毕后jdk文件夹里会有对应文件，开始配置环境变量

> #vi /etc/profile
> export JAVA_HOME=/usr/java/jdk/jdk版本编号_121
> export JRE_HOME=/usr/java/jdk/jdk版本编号_121/jre
> export CLASSPATH=.:$JAVA_HOME/lib$:JRE_HOME/lib:$CLASSPATH
> export PATH=$JAVA_HOME/bin:$JRE_HOME/bin/$JAVA_HOME:$PATH

![](https://upload-images.jianshu.io/upload_images/6089846-1b2e66251be5b64a.png?imageMogr2/auto-orient/strip|imageView2/2/w/519/format/webp)

5、编辑完内容后，按下Esc键，并输入“:wq”，然后回车可以保存退出

6、保存完毕后输入下面指令

> #source /etc/profile

7、验证是否成功

> #java -version

![](https://upload-images.jianshu.io/upload_images/6089846-9d6b1ed45549eb66.png?imageMogr2/auto-orient/strip|imageView2/2/w/666/format/webp)

## 安装Tomcat

1、解压tomcat，解压指令如下：

> #tar -xvf apache-tomcat-版本编号.tar.gz -C /usr/java/tomcat/

![](https://upload-images.jianshu.io/upload_images/6089846-5ca276a70bb29aa4.png?imageMogr2/auto-orient/strip|imageView2/2/w/852/format/webp)

2、进入解压文件夹下的bin文件夹，指令如下：

> #cd/usr/java/tomcat/apache-tomcat-版本编号/bin/

![](https://upload-images.jianshu.io/upload_images/6089846-41050295e6db549c.png?imageMogr2/auto-orient/strip|imageView2/2/w/725/format/webp)

3、编辑setclasspath.sh 脚本，指令如下：

> #vi setclasspath.sh

4、添写如下内容：

> export JAVA_HOME=/usr/java/jdk/jdk版本编号
> export JRE_HOME=/usr/java/jdk/jdk版本编号/jre

5、保存编辑内容，按下Esc键，并输入“:wq”，然后回车可以保存退出。

6、启动tomcat，指令如下：

>  #./startup.sh

![](https://upload-images.jianshu.io/upload_images/6089846-66ccc6c4134336b0.png?imageMogr2/auto-orient/strip|imageView2/2/w/854/format/webp)

7、jdk和tomcat都弄好了，接下来可以用浏览器访问我的云服务器吗？

当然可以！你可以从浏览器访问，输入http://云服务器的ip:8080就能访问啦！

![](https://upload-images.jianshu.io/upload_images/6089846-adacb39c1796acf1.png?imageMogr2/auto-orient/strip|imageView2/2/w/1200/format/webp)

## 部署项目

将项目上传到 Tomcat文件夹下的 Webapps 文件夹里就行。上传好了后，浏览器访问即可。例如：http://云服务器ip地址:8080/index/one.html等。

![](https://upload-images.jianshu.io/upload_images/6089846-1919ee11f2bba7a7.png?imageMogr2/auto-orient/strip|imageView2/2/w/922/format/webp)

### 怎么通过我的域名访问我的网站呢

解析域名
域名直接访问


---

参考

[阿里云ECS建网站（建站）超详细全套完整图文教程！菜鸟必看！](https://www.jianshu.com/p/2604e53a7f6a?from=singlemessage)

