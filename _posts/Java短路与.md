---
title: Java短路与
categories: Java
tags:
  - Java
  - Java编程思想
abbrlink: 56535
date: 2019-08-04 12:12:01
---
Java短路与
<!--more-->
## Java中使用逻辑操作符时遇到的短路现象
```
// &&短路与

public class ShortCircuit{
	static boolean test1(int val) {
		System.out.println("test("+val+")");
		System.out.println("result: "+(val<1));
		return val<1;
	}
	static boolean test2(int val) {
		System.out.println("test("+val+")");
		System.out.println("result: "+(val<2));
		return val<2;
	}
	static boolean test3(int val) {
		System.out.println("test("+val+")");
		System.out.println("result: "+(val<3));
		return val<3;
	}
	
	public static void main(String[] args) {
		boolean b=test1(0)&&test2(2)&&test3(2);
		System.out.println("expression is "+b);
	}
}
```



>运行及结果：
>test(0)
>result: true
>test(2)
>result: false
>expression is false

可以发现test1与test2比较后直接输出，不会对test3进行比较，这就是&和&&的不同之处。