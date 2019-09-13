---
title: WordPress建站
categories: WordPress
tags:
  - WordPress搭建
  - WordPress优化
abbrlink: 29529
date: 2019-09-11 22:34:03
---
最近想让博客绑定域名，逛了阿里云，脑子一热又买了服务器，学生认证也挺优惠的，趁机会学习以下建站。因为个人没有基础，所以就从网上搜集教程，结合了多篇文章进行学习。

教程讲解了WordPress建站流程，从服务器配置、域名解析、宝塔面板、Wordpress建站、网站优化等操作讲解建站方法。

<!--more-->
转自 https://blog.csdn.net/aliyunguide/article/details/86664703
## 前期准备

- 域名：实名认证
- 服务器：内存512M以上Linux服务器，推荐使用1G内存、Centos7系统。国内服务器需要备案才可以用
- 其他：Wordpress主题、插件等，免费或者付费都可以，免费的可以查看我们推荐的[WordPress](https://themeforwp.net/archives/wordpress-blog-theme/)免费主题，付费的可以到Themeforest挑选


## 服务器LNMP环境搭建

想要运行Wordpress网站程序，必须要有对应的软件，也就是服务器环境，比如我们常说的LNMP就是 Linux + Nginx + Mysql + PHP 环境，最常见的网站程序，Wordpress程序就是结合这些语言开发出来的。

其实环境里面安装LNMP是众所周知的，这里我要说的是软件的版本，服务器不同于虚拟主机，我们可以自主控制各种程序的参数和版本，这将让网站的配置非常灵活。为了wordpress兼容和性能，关于软件版本的选择有一个很好的标准就是wordpress官方推荐环境，官方的建议是PHP7.2版本及以上，Mysql5.6版本及以上，还有就是https，安装软件的的原则就是版本越接近推荐的越好

接下来就让我们从使用服务器命令开始，搭建Wordpress网站的LNMP环境

### 安装Xshell

由于Windows是不能直接连接到Linux服务器的，需要一个SSH的软件，推荐使用Xshell作为远程连接软件，它对于个人和学校是免费使用的，可以在Xshell官网直接下载。

### 连接到服务器

安装好了Xshell软件之后，就可以开始连接到服务器了，提前准备好服务器的IP、账号、密码

打开Xshell软件，选择文件 – 新建，添加一个连接

图1-1为连接成功

![图1-1](https://note.youdao.com/yws/api/personal/file/WEB3c7e5bb2f3eb0b7dcf39547db3389e49?method=download&shareKey=498e383173ce4768c290d70dfe93255f)

### 安装宝塔面板

接下来我们在服务器安装宝塔面板，输入下面的命令并执行(最新宝塔面板需要在centos7系统用，其他系统的命令[查看这里](https://www.bt.cn/bbs/thread-1186-1-1.html))

> yum install -y wget && wget -O install.sh http://download.bt.cn/install/install_6.0.sh && bash install.sh

安装中途会脚本询问是否将网站安装在www目录，直接选择y，然后确认即可，大概会需要几分钟的时间

安装成功后会出现图1-2的信息

![图1-2](https://themeforwp.net/wp-content/uploads/2018/06/20180613225752.jpg)

最后得到了宝塔面板的登陆信息，将这些保存下来

宝塔面板为了提升安全，已将面板路径在之前的8888端口增加了随机入口，所以最好将登录信息长期保存，以后面板的管理都需要用到这些信息

### 安装网站环境

使用刚刚获得到的信息，访问你的ip:8888，登陆宝塔面板，比如刚刚我的就是访问 http://45.76.48.16:8888，账号密码也就是刚刚安装完显示的

(注意：如果使用的是阿里云之类的云服务器提前开放安全端口)

首次登陆宝塔面板后台，会弹出一键安装环境，在这里我们需要耐心设置一遍

仔细看下图中的设置，安装环境主要有3个点
- 选择LNMP环境，节省资源
- 调整Mysql和PHP版本
- 安装方式选择为编译安装

![](https://themeforwp.net/wp-content/uploads/2018/06/20180614070705.jpg)

最好是按照上图的配置安装，可能有朋友会问为什么不选择 PHP7.2，这里主要是考虑到各种主题和插件的最大兼容，如果选择PHP7.2的话可能会有一些奇怪的问题，当然如果后期主题和插件都兼容了也可以切换到7.2。还有一点就是如果服务器为512M内存要选择Mysql5.5，不然压力会很大

![](https://themeforwp.net/wp-content/uploads/2018/06/20180614071911.jpg)

LNMP环境编译安装过程大概为半小时左右，视服务器性能而定

## 搭建Wordpress网站

当服务器LNMP环境安装完成之后，我们就可以开始着手搭建Wordpress网站了，这里就是建站的主要步骤，用过虚拟主机的朋友应当非常熟悉

### 新建站点

选择网站 – 添加站点，首先填入自己的域名，一般是 domain.com 和 www.domain.com 两种格式都要绑定，并创建FTP和数据库

![](https://themeforwp.net/wp-content/uploads/2018/06/20180614125432.jpg)

创建完成后会在网站列表中显示，这里面的密码记不记无所谓，可以随时查看，后期还要通过这里进行网站管理

![](https://themeforwp.net/wp-content/uploads/2018/06/20180614125517.jpg)

### 域名解析

服务器已经绑定了域名，接下来就是添加解析了，其实就是添加2条A记录，非常简单，这里我用的是腾讯云域名，其他的服务商可能稍微有些不同

登陆控制台，选择域名注册 – 找到自己的域名 – 解析

和服务器绑定一致，域名也是添加2条记录，一个是www对应 www.domain.com，另一个是@，对应domain.com，全部解析到服务器的ip地址

解析完成后访问域名，如果显示 恭喜, 站点创建成功，就证明解析完成，可以进入下一步的网站搭建了，如果还不能访问，稍等几分钟再尝试

注意，有些国外域名解析的话生效较慢，需要等待一天左右时间

### 下载Wordpress安装包

因为需要到wordpress官网下载程序，就采用的是宝塔的远程下载功能，先教大家如何使用

我们进入宝塔后台 – 文件，可以看到这就是服务器的文件系统，默认的/www目录就是所有网站的目录，可以看到刚刚我们创建的网站 wpwp.xyz，我们点击就能就入网站里面

![](https://themeforwp.net/wp-content/uploads/2018/06/20180614133227.jpg)

可以看到网站下还很空，可以先把2个没用的 index.html 和 404.html 删除

![](https://themeforwp.net/wp-content/uploads/2018/06/20180614133423-800x333.jpg)

在文件的上方，我们可以看到在上传的右边有一个远程下载的按钮，点击会弹出一个对话框

这里我们就填入wordpress最新版的下载地址，确定之后就会下载到当前的目录

有的朋友可能不知道如何获取下载地址，打开[wordpress中文下载](https://cn.wordpress.org/download/)，在下载按钮上右键 – 复制链接地址

![](https://themeforwp.net/wp-content/uploads/2018/06/20180614134204.jpg)

![](https://themeforwp.net/wp-content/uploads/2018/06/20180614133907.jpg)

等待一会下载完成后，点击一下刷新按钮，就能看到Wordpress程序的压缩包

![](https://themeforwp.net/wp-content/uploads/2018/06/20180614134338.jpg)

选择右键 – 解压，直接确定

![](https://themeforwp.net/wp-content/uploads/2018/06/20180614134711.jpg)

解压完成后网站根目录会多出一个wordpress的文件夹

但这样不能直接使用的，我们还要继续将wordpress文件夹内的所有文件移动到网站的根目录

选中所有文件，然后剪切，然后到网站根目录粘贴所有

![](https://themeforwp.net/wp-content/uploads/2018/06/20180614134952.jpg)

最后的目录结构如下图就行了

![](https://themeforwp.net/wp-content/uploads/2018/06/20180614135525.jpg)

### WordPress安装

环境和程序都就绪了，接下来就可以开始安装Wordpress网站了

访问 www.domain.com(自己购买的域名)，进入程序安装界面，第一步选择 现在就开始

![](https://themeforwp.net/wp-content/uploads/2018/06/20180614150844-800x444.jpg)
