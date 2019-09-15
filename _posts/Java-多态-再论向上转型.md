---
title: Java_多态_再论向上转型
categories: Java
tags:
  - Java
  - 多态
  - 向上转型
abbrlink: 19885
date: 2019-09-15 12:18:58
---
Java_多态_再论向上转型
<!--more-->
```
enum Note{
	MIDDLE_C,C_SHARP,B_FLAT;
}
class Instrument{
	public void play(Note n) {
		System.out.println("Instrument.play()");
	}
}

class Wind extends Instrument{
	public void play(Note n) {
		System.out.println("Wind.play() "+n);
	}
}

public class Music{
	static void tune(Instrument i) {
		i.play(Note.MIDDLE_C);
		
	}
	public static void main(String[] args) {
		Wind flute = new Wind();
		tune(flute);
	}
}/*Output:
Wind.play() MIDDLE_C
*///:~
```

Music.tune()方法接受一个Instrument引用，同时也接受任何导出自Instrumnet的类。在main()方法中，当一个Wind引用传递到tune()方法时，就会出现这种情况，而不需要任何类型转换。这样做是允许的-因为Wind从Instrument继承而来，所以Instrument的接口必定存在于Wind中。

但为什么不让tune()方法直接接受一个Wind引用作为自己的参数呢。如果那样做，就需要为系统内Instrument的每种类型都编写新的tune()方法。

按照这种假设，再加入Stringed（弦乐）和Brass（管乐）两种Instrument(乐器)。

```
enum Note{
	MIDDLE_C,C_SHARP,B_FLAT;
}
class Instrument{
	public void play(Note n) {
		System.out.println("Instrument.play()");
	}
}
class Wind extends Instrument{
	public void play(Note n) {
		System.out.println("Wind.play() "+n);
	}
}
class Stringed extends Instrument{
	public void play(Note n) {
		System.out.println("Stringes.play() "+n);
	}
}
class Brass extends Instrument{
	public void play(Note n) {
		System.out.println("Brass.play() "+n);
	}
}

public class Music2{
	public static void tune(Wind i) {
		i.play(Note.MIDDLE_C);
	}
	public static void tune(Stringed i) {
		i.play(Note.MIDDLE_C);
	}
	public static void tune(Brass i) {
		i.play(Note.MIDDLE_C);
	}
	public static void main(String[] args) {
		Wind flute = new Wind();
		Stringed violin = new Stringed();
		Brass frenchHorn = new Brass();
		tune(flute);
		tune(violin);
		tune(frenchHorn);
	}
}/*Output:
Wind.play() MIDDLE_C
Stringes.play() MIDDLE_C
Brass.play() MIDDLE_C
*///:~
```

虽然行得通，但必须为添加的每一个新Instrument类编写特定类型的方法。如果想添加类似tune()的新方法，或者添加自Instrument导出的新类，仍需要做大量工作。