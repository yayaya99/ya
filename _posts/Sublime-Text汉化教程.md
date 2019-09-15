---
title: Sublime Text汉化教程
categories: Sublime Test
tags:
  - 汉化
  - Sublime Test
abbrlink: 19963
date: 2019-09-13 19:59:40
---
发现一款Sublime Text编辑器，界面非常简洁，官方简介“A sophisticated text editor for
code, markup and prose”

<!--more-->
应用界面：

![](https://note.youdao.com/yws/api/personal/file/D63DC3CDC8184E21AC0CC529AF3B0CB7?method=download&shareKey=0466c46ccdb5640c82c78d492c858b66)

## 安装

[Sublime Text](http://www.sublimetext.com/)官网点击DOWNLOAD下载

## 汉化

英文界面用着不习惯那就汉化，另外Sublime Text也支持很多语言

### 打开Sublime Text的控制台（Ctrl+~）

![](https://note.youdao.com/yws/api/personal/file/DECDD38064CB43D382A931789CB46459?method=download&shareKey=48c07dedbfc24163536553843b3fe86e)

### 粘贴代码到控制台

进入[Package Control官方网站](https://packagecontrol.io/installation)

打开后，将适用于您的Sublime Text版本的Python代码粘贴到控制台中。

![](https://note.youdao.com/yws/api/personal/file/F3A3BCAFD6944276AB58FBC5B4E162A9?method=download&shareKey=a3aa69e5a8989458ddd9178faf64e14f)

可以直接粘贴下面的代码：

> SUBLIME TEST 3

```
import urllib.request,os,hashlib; h = '6f4c264a24d933ce70df5dedcf1dcaee' + 'ebe013ee18cced0ef93d5f746d80ef60'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)
```

> SUBLIME TEST 2

```
import urllib2,os,hashlib; h = '6f4c264a24d933ce70df5dedcf1dcaee' + 'ebe013ee18cced0ef93d5f746d80ef60'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); os.makedirs( ipp ) if not os.path.exists(ipp) else None; urllib2.install_opener( urllib2.build_opener( urllib2.ProxyHandler()) ); by = urllib2.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); open( os.path.join( ipp, pf), 'wb' ).write(by) if dh == h else None; print('Error validating download (got %s instead of %s), please try manual install' % (dh, h) if dh != h else 'Please restart Sublime Text to finish installation')
```

粘贴后回车

### 选择语言

![](https://note.youdao.com/yws/api/personal/file/17E635F75A414E85BE61A8689C1E0045?method=download&shareKey=1f2ebac7ba81d16f0070533dc2c28ca4)

![](https://note.youdao.com/yws/api/personal/file/4FB00C2308514C3397179B4E178A8EA5?method=download&shareKey=572dceb1b7fc6eecec872fa4426aa008)

![](https://note.youdao.com/yws/api/personal/file/128B2F2D5B21447F88BFD73978E8AAE2?method=download&shareKey=86be3e3a7b90dea49a76664b3c53b6c8)

![](https://note.youdao.com/yws/api/personal/file/9CAEE92A14604CD6932B45BBE4C782E3?method=download&shareKey=b10febac4b4c005a12bad64bfbac34fb)

稍微等一会就会出现中文界面

## 切换语言

![](https://note.youdao.com/yws/api/personal/file/7DF89CE11F4345099D7C39EE0087B3AE?method=download&shareKey=e6cd06046dbfa2c0e7f2d2f3a1fd764f)

Help->Language


---
参考

[Sublime text如何汉化](https://jingyan.baidu.com/article/90bc8fc8b38eabf653640c93.html)
