---
title: Java toString() 方法
categories: Java
tags:
  - Java
  - toString()
abbrlink: 60799
date: 2019-09-15 12:47:46
---

Java toString() 方法
<!--more-->

toString()方法用于返回以一个字符串表示的Number对象值。

如果方法使用了原生的数据类型作为参数，返回原生数据类型的String对象值。

如果方法有两个参数，返回用第二个参数指定基数表示的第一个参数的字符串表示形式。

## 语法

以String类为例，该方法有以下几种格式语法：

>String toString()
>static String toString(int i)

参数

- i--转换的整数

返回值

- toString():返回表示Integer值的String对象
- toString(int i):返回表示指定int的String对象

实例：

```
public class Test{
	public static void main(String[] args) {
		Integer x = 5;
		System.out.println(x.toString());
		System.out.println(Integer.toString(12));
	}
}/*Output:
5
12
*///:~
```
---------------------------------------------------------------------分割线------------------------------------------------------------------------------------------- 

以下引自 https://blog.csdn.net/u013309870/article/details/72158054

## Integer类的toString的基本用法

```
public class IntegerDemo{
	public static void main(String[] args) {
		Integer OUT_MAX_VALUE = new Integer(Integer.MAX_VALUE);
		Integer MAX_VALUE = new Integer(Integer.MAX_VALUE);
		Integer MIN_VALUE = new Integer(Integer.MIN_VALUE);
		Integer NOR_VALUE = new Integer(-128);
		Integer OUT_MIN_VALUE = new Integer(Integer.MIN_VALUE);
		
		System.out.println("max_val "+MAX_VALUE.toString());
		System.out.println("max_val :"+MAX_VALUE);
        System.out.println("-------------------------");
        System.out.println("out_max :"+OUT_MAX_VALUE.toString());
        System.out.println("out_min :"+OUT_MIN_VALUE.toString());
        System.out.println("-------------------------");        
        System.out.println("min_val :"+MIN_VALUE.toString());
        System.out.println("min_val :"+MIN_VALUE);
        System.out.println("-------------------------");
        System.out.println("nor_val :"+NOR_VALUE.toString());
        System.out.println("nor_val :"+NOR_VALUE);
	}
}/*Output:
max_val 2147483647
max_val :2147483647
-------------------------
out_max :2147483647
out_min :-2147483648
-------------------------
min_val :-2147483648
min_val :-2147483648
-------------------------
nor_val :-128
nor_val :-128
*///:~
```

由上面可知直接输出Integer的值和调用Integer类的toString方法是一样的，其实直接打印一个对象的时候就是调用了该对象的toString方法。调用toString方法的时候其实输出的是Integer的value值，toString方法就是把int类型的value值转化为string类型输出。注意一下几点：

1、Integer的value值从 Integer.MIN_VALUE 到 Integer.MAX_VALUE 如果超出了这个范围就会得到一些奇怪的结果。

2、在Integer.MAX_VALUE基础上加1输出的结果是个负值。

3、在Integer.MIN_VALUE基础上加1输出的结果是个正值。

## Integer类的toString的源码分析

```
public String toString() {
    return toString(value);
}

//------------------------------

public static String toString(int i) {
    if (i == Integer.MIN_VALUE)
        return "-2147483648";
     //如果是最小值直接返回其字符串因为Integer.MIN_VALUE=-2147483648 ，这样可以节省下面计算时间
     //①
    int size = (i < 0) ? stringSize(-i) + 1 : stringSize(i);
    //获取整数值的长度10进制
    char[] buf = new char[size];
    //②
    getChars(i, size, buf);
    //得到整数中的每一个字符
    //③
    return new String(buf, true);
    //返回字符串值
}
```

上面的代码做几点说明： 
1、如果Integer的value值正好是 Integer.MIN_VALUE 直接返回 “-2147483648” 节省时间。 
2、得到integer值的十进制的长度，如果负数先求出绝对值的长度，然后再长度加1，因为负数的符号位占一位。 
3、得到integer的value值的每一个字符。 
4、得到的字符新建字符串返回。 

...

先记到这里把，我脑子不够用了。。