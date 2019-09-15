---
title: Java 在方法和作用域内的内部类
categories: Java
tags:
  - Java
  - 内部类
abbrlink: 4991
date: 2019-09-15 12:51:50
---

Java 在方法和作用域内的内部类
<!--more-->

10.5 在方法和作用域内的内部类

自己很难搞懂一些代码的作用，所以内部类这一章进行的很慢很慢，看的我头大

所以

先mark以下

---

在知乎上看到了这么一句话：

局部内部类是指内部类定义在方法或作用于内

- 局部内部类不能有访问说明符
- 局部内部类可以访问当前代码块内的常量以及此外围类的所有成员


---


内部类的语法覆盖了大量其他的更加难以理解的技术。例如，可以在一个方法里面或者在任意的作用域内定义内部类。这么做有两个理由：

1、实现了某个类型的接口，于是可以创建并返回对其的引用。

2、要解决一个复杂的问题，想创建一个类来辅助你的解决方案，但是又不希望这个类是公共可用的。

在后面的例子中，以用来实现：

1、一个定义在方法中的类

2、一个定义在作用域内的类，此作用域在方法的内部

3、一个实现了接口的匿名类

4、一个匿名类，它扩展了有非默认构造器的类

5、一个匿名类，它执行字段初始化

6、一个匿名类，它通过实例化初始化实现构造（匿名类不可能有构造器）

第一个例子展示了在方法的作用域（而不是在其他类的作用域内）创建了一个完整的类。这被称作局部内部类：

```
public class Parcel5{
	public Destination destination(String s) {
		class PDestination implements Destination{
			private String label;
			private PDestination(String whereTo) {
				label = whereTo;
			}
			public String readLabel() {return label;}
		}
		return new PDestination(s);
	}
	public static void main(String[] args) {
		Parcel5 p = new Parcel5();
		Destination d = p.destination("Tasmania");
	}
}
```

代码中内部类PDestination实现了Destination,???

在网上没有找到这样写的原因，个人不太懂，唉

PDestination类是destination()方法的一部分，而不是Parcel5的一部分。所以，在destination()之外不能访问PDestination。注意出现在return语句中的向上转型——返回的是Destination的引用，它是PDestination的基类。当然，在destination()中定义了内部类PDestination，并不意味着一旦dest()方法执行完毕，PDestination就不可用了。

你可以在同一个子目录下的任意类中对某个内部类使用标识符PDestination，这并不会有命名冲突。

如何在任意的作用域内嵌入一个内部类：

```
public class Parcel6{
	private void internalTracking(boolean b) {
		if(b) {
			class TrackingSlip{
				private String id;
				TrackingSlip(String s){
					id = s;
				}
				String getSlip() {return id;}
			}
			TrackingSlip ts = new TrackingSlip("slip");
			String s = ts.getSlip();
		}
		//Can't use it here! Out of scope;
		//!TrackingSlip ts = new TrackingSlip("x");
	}
	public void track() {internalTracking(true);}
	public static void main(String[] args) {
		Parcel6 p = new Parcel6();
		p.track();
	}
}
```

TrackingSlip类被嵌入在if语句的作用域内，这并不是说该类的创建是有条件的，它其实与别的类一起编译过了。然而，在定义TrackingSlip的作用域之外，它是不可用的；除此之外，它与普通的类一样。


