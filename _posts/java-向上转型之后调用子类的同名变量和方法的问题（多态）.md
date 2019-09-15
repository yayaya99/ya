---
title: java 向上转型之后调用子类的同名变量和方法的问题（多态）
categories: Java
tags:
  - Java
  - 向上转型
  - 多态
abbrlink: 23364
date: 2019-09-15 12:21:57
---

在学习向上转型时遇到的一些疑问
<!--more-->

```
class A{
	int i=0;
	void f1() {
		System.out.println("A.f1()");
		f2();
	}
	public void f2() {
		System.out.println("A.f2()");
	}
}
class B extends A{
	int i=1;
	public void f2() {
		System.out.println("B.f2()");
	}
}
```

```
public class Test{
	public static void main(String[] args) {
		A a = new B(); //(1)
		a.f1(); //(2)
	}
}/*Output:
A.f1()
B.f2()
*///:~
```

在（1）处为向上转型（a实际上指向的是一个子类对象），之后调用了a.f1();,以为会打印A.f1();A.f2();,但结果却不是。

个人理解：B继承了A，也就是B有了A的方法，a.f1()是调用B里的f1()，然后f1()又调用了B里f2()。

```
public class Test{
	public static void main(String[] args) {
		A a = new B(); //（1）
		System.out.println(a.i);
	}
}
```

然后又出现疑问，为什么（1）后输出的i值为0

突然脑子短路。。


---------------------------------分割线-------------------------------------------------------------------------------------------------------------------------------- 


在网上查看了好多类似的问题，发现某位兄台整理的比较好，就厚颜无耻的引用过来了。

https://blog.csdn.net/kavensu/article/details/8079460

```
class Father {
	String name = "父";
	void f(){System.out.print("父类");}
}

class Son extends Father{
	String name = "儿子";
	void f() {
		System.out.print("儿子");
	}
	void f2() {
	}
}
public class Test{
	public static void main(String[] args) {
		Father s = new Son();
		System.out.println(s.name); //1
		s.f(); //2
		s.f2();	//3
	}
}
```

疑问：不是说类型是由new决定的而不是由声明决定的吗？即Father s=new Son()此时s的具体类型是什么？若是Father 那上面的2就应该输出“父类”而不是“儿子”？
若是Son类那就应该能调用f2()呀？另外还有name疑问，s.name怎么会是"父"呢？

分析：

Father s = new Son();

表示定义了一个Father类型的引用，指向新建的Son类型的对象。由于Son是继承自它的父类Father，所以Father类型的引用是可以指向Son类型的对象的。那么这样有什么意义？因为子类是对父类的一个改进和扩充，所以一般子类在功能上较父类更强大，属性较父类更独特。

定义一个父类类型的引用之指向一个子类的对象既可以使用子类强大的功能，又可以抽取父类的共性。

所以，父类类型的引用可以调用父类中定义的所有属性和方法，而对于子类中定义而父类中没有的方法，它是无可奈何的； 因此s.name调用父类的属性! f2方法父类没有，出错！

同时，父类中的一个方法只有在在父类中定义而在子类中没有重写的情况下，才可以被父类类型的引用调用；

对于父类中定义的方法，如果子类中重写了该方法，那么父类类型的引用将会调用子类中的这个方法，这就是动态连接。因此s.f()调用子类的方法!

对于多态，可以总结它为：

　　一、使用父类类型的引用指向子类的对象；
　　
　　二、该引用只能调用父类中定义的方法和变量；
　　
　　三、如果子类中重写了父类中的一个方法，那么在调用这个方法的时候，将会调用子类中的这个方法；（动态连接、动态调用）
　　
　　四、变量不能被重写（覆盖），”重写“的概念只针对方法，如果在子类中”重写“了父类中的变量，那么在编译时会报错。
