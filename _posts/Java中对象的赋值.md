---
title: Java中对象的赋值
categories: Java
tags:
  - Java
  - 赋值
abbrlink: 41314
date: 2019-08-03 17:46:26
---
记录以下学习Java对象赋值中出现的问题
<!--more-->

在java中赋值使用操作符“=”。意思是“取右边的值，把它赋值给左边”。右值可以是任何常数、变量或者表达式（只要能生成一个值）。但左边必须是一个明确的、已命名的变量。
但是不能把任何东西赋值给一个常数，常数不能作为左值（比如不能4=a;）。
基本数据类型的赋值是直接将一个地方的内容复制到了另一个地方。例如，a=b,b的内容复制给a。接着又修改了a，而b并不会受a修改的影响。
	
但在为对象赋值的时候，情况却不一样。
对一个对象进行操作时，我们真正操作的是对对象的引用。



```
class Tank{
	int level;
}
public class Test{
	public static void main(String[] arg) {
		Tank t1 = new Tank();
		Tank t2 = new Tank();
		t1.level = 9;
		t2.level = 47;
		System.out.println("1: t1.level: " + t1.level + ",t2.level: " + t2.level);
		t1 = t2;
		System.out.println("2: t1.level: " + t1.level + ",t2.level: " + t2.level);
		t1.level = 27;
		System.out.println("3: t1.level: " + t1.level + ",t2.level: " + t2.level);
	
	}
}/*Output:
1: t1.level: 9,t2.level: 47
2: t1.level: 47,t2.level: 47
3: t1.level: 27,t2.level: 27
*///:~
```

每个Tank类对象的level域都赋予了一个不同的值，然后，将t2赋给t1。
我们可能会期望t1和t2总是相互独立的。
但由于赋值操作的是一个对象的引用，t1和t2包含的引用相同,所以修改t1的同时也改变了t2。
这种特殊现象称为”别名现象“。
	
>避免方式：
>t1.level = t2.level;
	
---
	
## 方法调用中的别名问题
	
```
class Tank{		
	char c;
}

public class Test{
	static void f(Tank y) {
		y.c = 'z';
	}
	public static void main(String[] arg) {
		Tank t = new Tank();
		t.c = 'a';
		System.out.println("1: t.c: " + t.c);
		f(t);
		System.out.println("2: t.c: " + t.c);
	}
}
```
	
>运行及结果：
>1: t.c: a
>2: t.c: z

	
