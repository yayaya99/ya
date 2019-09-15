---
title: Java继承与初始化
categories: Java
tags:
  - Java
  - 继承初始化
abbrlink: 61610
date: 2019-09-15 12:16:39
---
转自 https://blog.csdn.net/fengjianbang/article/details/50938569

<!--more-->

在Java中，每一个类的编译代码都存在于它自己的独立文件中。该文件只有在需要时才会被加载，一般是在类初次使用时加载，这通常是指创建类的第一个对象或者第一次访问类中的静态方法或者静态块。

当JVM要加载一个类A时，如果发现这个类有父类B，那么JVM首先加载其父类B，如果这个父类B还有其自身的父类C，那么首先加载类C，一次类推。这个过程是必须要进行的，即使我们有没有创建类A的对象。看下面这段代码，执行之后的输出结果为，在这段代码中，main函数中并没有任何语句，但是却产生了输出，这是因为在执行这段代码的时候，第一件事是试图访问B.main函数（由于main函数是属于类B的一个静态函数，根据上述内容，这时候需要加载类B的编译代码），于是加载器启动，并找出类B的编译代码（在名为B.class的文件中），在加载的过程中，发现它继承与类A，于是转而先加载类A。在类的加载过程中，加载器会对类的static 变量进行初始化，加载类中的静态块。

```
package testOOP;
class A{
	static{
		System.out.println("this is father's static");
	}
	A(){
		System.out.println("this is father");
	}
	
}
public class B extends A{
	static{
		System.out.println("this is child's static");
	}
	B(){
		System.out.println("this is child");
	}
	public static void main(String [] args){
		
	}
}
```

在上述的代码中，如果main函数中有明确创建B对象的语句，并且类A，和类B都有自己的成员变量和非静态初始化块时，类A，类B的初始化顺序是怎么样的呢？我们首先看一下这段代码，运行后的输出为。根据输出我们可以看出，在创建类B的对象时，首先会加载父类A，然后加载类B，加载完这两个类之后，开始进行初始化操作：首先执行父类的非静态块的初始化操作，然后执行父类的构造方法，再执行子类的非静态块初始化操作，最后执行子类的构造方法。

```
package testOOP;
class A{
	static{
		System.out.println("this is father's static");
	}
	{
		System.out.println("这是父类的非静态初始化块");
	}
	A(){
		System.out.println("this is father");
	}
	
}
public class B extends A{
	static{
		System.out.println("this is child's static");
	}
	{
		System.out.println("这是子类的非静态初始化块");
	}
	B(){
		System.out.println("this is child");
	}
	public static void main(String [] args){
		new B();
	}
}
```

由上述分析内容可以知道，当需要创建一个类A的对象时，其执行顺序是：1、加载父类，2、加载类A，3、执行父类的非静态初始化块，4、执行父类的构造方法，5、执行子类的非静态初始化块，6、执行子类的构造方法。