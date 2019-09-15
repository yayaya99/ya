---
title: Java 链接到外部类
categories: Java
tags:
  - Java
abbrlink: 58949
date: 2019-09-15 12:49:07
---

Java 链接到外部类
<!--more-->

当生成一个内部类的对象时，此对象与制造它的外围对象之间就有了一种联系，所以它能访问其外围对象的所有成员，而不需要任何特殊条件。

内部类还拥有其外围类的所有元素的访问权。
```
interface Selector{
	boolean end();Object current();void next();
}
public class Sequence{
	private Object[] items;
	private int next = 0;
	public Sequence(int size) {items = new Object[size];}
	public void add(Object x) {
		if(next < items.length)
			items[next++] = x;
	}
	private class SequenceSelector implements Selector{
		private int i = 0;
		public boolean end() {return i == items.length;}
		public Object current() {return items[i];}
		public void next() {
			if(i < items.length)
				i++;
		}
	}
	public Selector selector() {
		return new SequenceSelector();
	}
	public static void main(String[] args) {
		Sequence sequence = new Sequence(10);
		for(int i = 0;i<10;i++) {sequence.add(Integer.toString(i));}  //1
		Selector selector = sequence.selector();
		while(!selector.end()) {
			System.out.print(selector.current()+" ");
			selector.next();
		}
	}
}
```

程序中在1处的调用是这样写的，sequence.add(Integer.toString(i)，add函数为：public void add(Object x)。这里我有个疑问，如果写成sequence.add(1)结果是一样的，那么那样写是是那么意思呢？

依照疑问下面引入了网友的回答：

1、sequence.add(Interger.toString(1))表示s里面加入的是个string值，内容是1
sequence.add(1)表示s里面加入的是个int数字1
因为public void add(Object x)中参数是Object所以string和int都能传入

2、Interger.toString(1) 是把数字用字符串的形式表示出来
Object x 是所有java支持的对象
sequence.add(1),,因为不管1是数字还是字符,都是java支持的对象所以直接add也可以