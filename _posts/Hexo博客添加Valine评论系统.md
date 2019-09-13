---
title: Hexo博客添加Valine评论系统
categories: Hexo
tags:
  - Hexo
  - next
abbrlink: 62918
date: 2019-09-12 20:44:40
---
[Valine](https://valine.js.org) 诞生于2017年8月7日，是一款基于LeanCloud的快速、简洁且高效的无后端评论系统。

理论上支持但不限于静态博客，目前已有Hexo、Jekyll、Typecho、Hugo、Ghost 等博客程序在使用Valine。

<!--more-->
## 注册Leancloud

[Leancloud官网](https://leancloud.cn/dashboard/applist.html#/apps)

## 创建应用

创建应用，名字随便，然后进入**设置**->**应用Key**

会获得**App ID**和**App Key**

![](https://note.youdao.com/yws/api/personal/file/4681CD86787442E3ABDF8E4253EBB7F7?method=download&shareKey=4a29feba787b06c9bad81b82cba3e0e5)

## 设置安全域名

**设置**->**安全中心**->**Web 安全域名**

添加域名

![](https://note.youdao.com/yws/api/personal/file/24F9AB5A35F246EEA9D1AC9E3B001B5E?method=download&shareKey=d1421b849fce2fe3ad04db77a829a274)

## 配置主题文件

打开next主题配置文件，找到Valine

![](https://note.youdao.com/yws/api/personal/file/3218D186890A414690199CBE24AFF54B?method=download&shareKey=f67add0d27a1f16a2c63b6a57b6bb5f2)

添加**App ID**和**App Key**

## 保存

> hexo clean && hexo g && hexo d

然后刷刷刷

![](https://note.youdao.com/yws/api/personal/file/6ACDF3D45A04486BAFFA1582C666F63C?method=download&shareKey=2015c0c92caaa4c71bddeb3e470a9e89)

添加成功

---

**参考**

[为你的Hexo加上评论系统-Valine](https://blog.csdn.net/blue_zy/article/details/79071414)