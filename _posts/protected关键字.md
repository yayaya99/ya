---
title: protected关键字
categories: Java
tags:
  - Java
  - protected
abbrlink: 36588
date: 2019-09-15 12:28:58
---

如果希望超类中的某些方法允许被子类访问，或者允许子类的方法访问超类的某个域，为此需要将这些方法或域设置为protected。
<!--more-->

下面是编程思想中的一段代码

```
class Villain{
	private String name;
	protected void set(String nm) {name = nm;}
	public Villain(String name) {this.name=name;}
	public String toString() {
		return "I'm a Villain and my name is "+name;
	}
}
public class Orc extends Villain{
	private int orcNumber;
	public Orc(String name,int orcNumber) {
		super(name);
		this.orcNumber = orcNumber;
	}
	public void change(String name,int orcNumber) {
		set(name);
		this.orcNumber = orcNumber;
	}
	public String toString() {
		return "Orc "+orcNumber+": "+super.toString();
	}
	public static void main(String[] args) {
		Orc orc  = new Orc("Limburger",12);
		System.out.println(orc);
		orc.change("Bob",19);
		System.out.println(orc);
	}
}/*Output:
Orc 12: I'm a Villain and my name is Limburger
Orc 19: I'm a Villain and my name is Bob
*///:~
```

change()可以访问set(),这是因为它是protected。

但是我换成public后依然可以运行，不懂为什么要用protected。

-----------------------------------分割线----------------------------------------------------------------------------------------------------------------------------------
