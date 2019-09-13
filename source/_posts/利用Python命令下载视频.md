---
title: 利用Python命令下载视频
categories: Python
tags:
  - Python
abbrlink: 16968
date: 2019-09-12 19:39:23
---
Python是一种跨平台的计算机程序设计语言。是一种面向对象的动态类型语言，最初被设计用于编写自动化脚本(shell)，随着版本的不断更新和语言新功能的添加，越来越多被用于独立的、大型项目的开发。

<!--more-->

1、电脑需要安装[Python3](https://www.python.org)

2、window+r 打开cmd输入python来检查环境：

> python

3、输入下面的代码回车：

> pip3 install you-get 

安装you-get，它是python3的一个下载工具

4、下载视频时可以选择文件路径

> you-get -o F:\k 文件地址  

默认下载到C盘

5、下载视频选择清晰度

> you-get -i 文件地址

![](https://note.youdao.com/yws/api/personal/file/5D074E03E1A14F468FFFE7717370B64E?method=download&shareKey=af6f177fd5891cd1abe66e7436f3f007)

显示下载时会有多种：超清、高清、标清

然后我们下载想要下载的视频样式，比如下载高清的，高清的是：-format=mp4sd

那么我们在cmd中输入：

> you-get --format=mp4sd 视频地址


---

网站视频下载基本上都支持

**下载国外视频需要科学上网**

