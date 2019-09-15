---
title: java接口中方法的默认访问修饰符为public
categories: Java
tags:
  - Java
  - 默认修饰符
abbrlink: 43208
date: 2019-09-15 12:42:55
---

java接口中方法的默认访问修饰符为public
<!--more-->

接口，比抽象类还要抽象的类:

1、接口中的方法会被隐式的指定为  public abstract （只能是 public abstract，其他修饰符都会报错）。

2、接口中的变量会被隐式的指定为  public static final   变量（并且只能是 public，用 private 修饰会报编译错误。）

3、接口中的方法是不能在接口中实现的，只能由实现接口的类来实现接口中的方法。


注：

接口是隐式抽象的，当声明一个接口的时候，不必使用 abstract 关键字。

接口中每一个方法也是隐式抽象的，声明时同样不需要 abstract 关键字。

接口中的方法都是公有的( public ) ！！！ 不是 default 啦