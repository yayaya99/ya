---
title: Github个人博客：绑定二级域名
categories: Hexo
tags:
  - Hexo
abbrlink: 44778
date: 2019-09-15 13:00:55
---

Github个人博客：绑定二级域名
<!--more-->

## 购买域名，实名认证

购买的阿里云的域名，绑定博客可以不需要备案的。


## CNAME设置

在blog/source目录下，新建名为CNAME的文件，没有后缀，添加blog.hongxigua.xyz

也可以直接编辑github中的文件


## 设置GitHub Pages

进入博客的管理设置

向下拉会出现GitHub Pages设置的选项

Custom domain添加：

> blog.hongxigua.xyz


## 域名解析

在域名后选择解析

出现解析设置

添加记录：

> 记录类型: CNAME- 将域名指向另外一个域名
> 主机记录： blog
> 解析路线：可默认
> 记录值：yayaya99.github.io
> TTL：10

(选择A时主机记录为www，记录值为ip地址，可通过pign博客的二级域名看到)

确定保存



