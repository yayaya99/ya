---
title: 空白fianl
categories: Java
tags:
  - Java
  - fianl
abbrlink: 61669
date: 2019-09-15 12:12:59
---
Java允许生成“空白fianl”，所谓空白fianl是指被声明为fianl但又未给定初值的域。编译器会确保空白fianl在使用前必须被初始化。
<!--more-->

```
class Poppet{
	private int i;
	Poppet(int ii){i=ii;}
}
public class BlankFianl{
	private final int i=0;
	private final int j;
	private final Poppet p;
	
	public BlankFianl() {
		j = 1;
		p = new Poppet(1);
	}
	public BlankFianl(int x) {
		j = x;
		p = new Poppet(x);
	}
	public String toString() {
		return "i,j,p:"+i+j+p;
		
	}
	public static void main(String[] args) {
		new BlankFianl();
		new BlankFianl(47);
	}
}
```

必须在域的定义处或者每个构造器中用表达式对final进行赋值，这正是final域在使用前总是被初始化的原因所在。

## 练习19 ：
创建一个含有指向某对象的空白final引用类。在所有构造器内部都执行空白final的初始化操作。说明Java确保final在使用前必须初始化，且一旦被初始化即无法改变