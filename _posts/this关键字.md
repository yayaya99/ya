---
title: this关键字
categories: Java
tags:
  - Java
  - this
abbrlink: 22373
date: 2019-08-09 08:24:21
---
编程思想第五章5.4中,这一段代码看着有点懵逼，记下来
<!--more--> 

```
class Person{
	void eat(Apple apple) {
		Apple peeled =apple.getPeeled();
		System.out.println("Yummy");
	}
}
class Peeler{
	static Apple peel(Apple apple) {
		return apple;
	}
}
class Apple{
	Apple getPeeled() {
		return Peeler.peel(this);
	}
}

public class Leaf {
	public static void main(String[] args) {
		new Person().eat(new Apple());
	}
}
```

***Apple需要调用Peeler.peel（）方法，它是一个外部的工具方法，将执行由于某种原因而必须放在Apple外部的操作。为了将自身传递给外部方法，Apple必须使用this关键字。***

## 在构造器中调用构造器

```
public class Flower{
	int petalCount = 0;
	String s="initial value";
	Flower(int petals){
		petalCount = petals;
		System.out.println("Constructor w/ int arg only,petalCount= "+petalCount);
	}
	Flower(String ss){
		System.out.println("Constructor w/ String arg only,s= "+ss);
		s=ss;
	}
	Flower(String s,int petals){
		this(petals);
		//this(s); //Can't call two!
		this.s=s;
		System.out.println("String & int args");
	}
	Flower(){
		this("hi",47);
		System.out.println("default constructor (no args)");
	}
	void printPetalCount() {
		//this(11); //Not inside non-constructor!
		System.out.println("petalCount = "+petalCount+" s= "+s);
	}
	public static void main(String[] args) {
		Flower x = new Flower();
		x.printPetalCount();
	}
}/*Output:
Constructor w/ int arg only,petalCount= 47
String & int args
default constructor (no args)
petalCount = 47 s= hi
*///:~
```

***this调用构造器不能调用两个。***
***构造器调用必须置于起始值。***
***调用构造器只能在构造器中调用***
