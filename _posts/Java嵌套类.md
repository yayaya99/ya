---
title: Java嵌套类
categories: Java
tags:
  - Java
  - 嵌套类
abbrlink: 57599
date: 2019-09-15 12:57:59
---

Java嵌套类
<!--more-->


如果不需要内部类对象与其外围类对象之间有联系，那么可以将内部类声明为static。这通常称为其**嵌套类**。想要理解static应用于内部类时的含义，就必须记住，普通的内部类对象隐式地保存了一个引用，指向创建它地外围类对象。然而，当内部类是static的时，就不是这样了。嵌套类意味着：

1、要创建嵌套类的对象，并不需要外围类的对象。

2、不能从嵌套类的对象中访问非静态的外围类对象。

嵌套类与普通的内部类还有一个区别。普通内部类的字段与方法，只能放在类的外部层次上，所以普通的内部类不能有static数据和static字段，也不能包含嵌套类。但是嵌套类可以包含所有这些东西：

```
public class Parcel11{
	private static class ParcelContents implements Contents{
		private int i = 11;
		@Override
		public int value() {return i;}
	}
	protected static class ParcelDestination implements Destination{
		private String label;
		private ParcelDestination(String whereTo) {
			label = whereTo;
		}
		@Override
		public String readLabel() {
			return label;
		}
		public static void f() {}
		static int x = 10;
		static class AnotherLevel{
			public static void f() {}
			static int x = 10;
		}
	}
	public static Destination destination(String s) {
		return new ParcelDestination(s);
	}
	public static Contents contents() {
		return new ParcelContents();
	}
	public static void main(String[] args) {
		Contents c = contents();
		Destination d = destination("Tasmania");
	}
}
```

在main()中，没有任何Parcel11的对象是必需的；而是使用选取static成员的普通语法来调用方法——这些方法返回对Contents和Destination的引用。

就像你在本章前面看到的那样，在一个普通的（非static）内部类中，通过一个特殊的this引用可以链接到其外围类对象。嵌套类就没有这个特殊的this的引用，这使得它类似于一个static方法。