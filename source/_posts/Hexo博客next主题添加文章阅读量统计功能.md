---
title: Hexo博客next主题添加文章阅读量统计功能
categories: Hexo
tags:
  - next
  - Hexo
abbrlink: 57681
date: 2019-09-13 15:23:37
---
添加文章阅读量统计有很多方法，因为我已经注册了LeanCloud，所以就直接采用了LeanCloud。

<!--more-->
## 注册

[LeanCloud](https://leancloud.cn/)

## 创建应用

储存->数据->创建Class

创建名为Counter的class用来存储访问博客的数据，例如：访问次数，最新访问时间等信息。class类名必须为Counter，主要为了与next主题相兼容，否则无法接收到相关数据。为了避免后续因为权限的问题导致次数统计显示不正常，ACL权限选择无限制。

## 获取ID和Key

设置->应用Key

会得到App ID和App Key

## 修改next主题配置文件

打开_config.yml，搜索leancloud_visitors，更改为true，并添加id和key

保存文件

最后生成部署hexo博客

效果如图：

![](https://note.youdao.com/yws/api/personal/file/3562A174A28C40DC8106572FC308D989?method=download&shareKey=ddd2ef2db8a657b3869db77c3ade6ce7)


---
参考

[Hexo博客next主题添加文章阅读量统计功能](https://cuibin1991.github.io/2017/07/31/Hexo%E5%8D%9A%E5%AE%A2next%E4%B8%BB%E9%A2%98%E6%B7%BB%E5%8A%A0%E6%96%87%E7%AB%A0%E9%98%85%E8%AF%BB%E9%87%8F%E7%BB%9F%E8%AE%A1%E5%8A%9F%E8%83%BD/)