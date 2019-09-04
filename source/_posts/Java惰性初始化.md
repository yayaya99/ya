---
title: Java惰性初始化
tags:
  - Java
  - 初始化
abbrlink: 43118
date: 2019-08-19 17:17:41
---
在书中第七章中提到了引用的初始化，编译器并不是简单地为每一个引用都创建默认对象，减少不必要的负担

1、在定义对象的地方。这意味着它们总是能够在构造器被调用之前被初始化。
2、在类的构造器中。
3、就在正要使用这些对象之前，这种方式称为惰性初始化。在生成对象不值得及不必每次都生成对象的情况下，这种方式可以减少额外的负担。
4、使用实例初始化。

惰性初始化的目的是延迟对象的初始化，直到程序真正使用它，同时确保它只初始化一次。

/*
惰性初始化：当需要一个实例的时候才初始化一个对象。
新建两个简单的类，第二个类中包含第一个类的一个引用，当
需要第一个类的对象是调用Lazy()方法即可获得第一个类的对象。
*/

```
class First{
	 First(){
		 System.out.print("First()");
	 }
}
public class Lazy{
	 First f;
	 public void print(){
		 if(f==null)
			 f = new First();
	 }
	 public static void main(String[] args){
		 Lazy z = new Lazy();
		 z.print();
	 }
}/*Output:
First()
*///:~
```
