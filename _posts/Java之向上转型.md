---
title: Java之向上转型
categories: Java
tags:
  - Java
  - 向上转型
abbrlink: 35786
date: 2019-09-15 12:09:37
---

Java之向上转型

<!--more-->
由于继承可以确保基类中所有的方法在导出类中也同样有效，所以能够向基类发送的所有信息同样也可以向导出类发送。Instrument类具有一个play()方法，那么Wind类也同样具备。可以说Windui对象也是一种类型的Instrument。

```
class Instrument{
	public void play() {}
	static void tune(Instrument i) {
		i.play();
	}
}
public class Wind extends Instrument{
	public static void main(String[] args) {
		Wind flute = new Wind();
		Instrument.tune(flute);
	}
}
```

在例中，tune()方法可以接受Instrument引用。但在Wind.main()中，传递给tune()方法的是一个Wind引用。在tune()中，程序代码可以对Instrument和它所有的导出类起作用，这种将Wind引用转换为Instrument引用的动作，我们称之为向上转型。

## 父类类型的变量来引用一个子类类型的对象。

```
interface Animal{
	void shout();
}
class Cat implements Animal{
	public void shout() {
		System.out.println("喵喵");
	}
}
public class Test{
	public static void main(String[] args) {
		Animal animal = new Cat();
		animalShout(animal);
	}
	public static void animalShout(Animal an) {
		an.shout();
	}
}
```

> Animal animal = new Cat() //将Cat对象当作Animal类型来使用
