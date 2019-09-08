---
title: Java方法重载
tags:
  - Java
  - 重载
  - Thinking in Java
abbrlink: 16008
date: 2019-08-08 11:37:05
---
Java方法重载
<!--more-->
## 示范重载构造器和重载的方法

```
class Tree{
	int height;
	Tree(){
		System.out.println("Planting a seedling");
		height= 0;
	}
	Tree(int initialHeight){
		height = initialHeight;
		System.out.println("Creating new Tree that is "+height+" feet tall");
	}
	void info() {
		System.out.println("Tree is "+height+"feet tall");
	}
	void info(String s) {
		System.out.println(s+":Tree is "+height+"feet tall");
	}
}
public class Overloading {
	public static void main(String[] args) {
		for(int i=0;i<5;i++) {
			Tree t = new Tree(i);
			t.info();
			t.info("overloaded method");
		}
		new Tree();
	}

}/*Output:
Creating new Tree that is 0 feet tall
Tree is 0feet tall
overloaded method:Tree is 0feet tall
Creating new Tree that is 1 feet tall
Tree is 1feet tall
overloaded method:Tree is 1feet tall
Creating new Tree that is 2 feet tall
Tree is 2feet tall
overloaded method:Tree is 2feet tall
Creating new Tree that is 3 feet tall
Tree is 3feet tall
overloaded method:Tree is 3feet tall
Creating new Tree that is 4 feet tall
Tree is 4feet tall
overloaded method:Tree is 4feet tall
Planting a seedling
*///:~
```

## 涉及基本类型的重载
```
public class PrimitiveOverloading {
	void f1(char x) {
		System.out.println("f1(char) ");
	}
	void f1(byte x) {
		System.out.println("f1(byte) ");
	}
	void f1(short x) {
		System.out.println("f1(short) ");
	}
	void f1(int x) {
		System.out.println("f1(int) ");
	}
	void f1(long x) {
		System.out.println("f1(long) ");
	}
	void f1(float x) {
		System.out.println("f1(float) ");
	}
	void f1(double x) {
		System.out.println("f1(double) ");
	}
	
	
	
	
	void f2(byte x) {
		System.out.println("f2(byte) ");
	}
	void f2(short x) {
		System.out.println("f2(short) ");
	}
	void f2(int x) {
		System.out.println("f2(int) ");
	}
	void f2(long x) {
		System.out.println("f2(long) ");
	}
	void f2(float x) {
		System.out.println("f2(float) ");
	}
	void f2(double x) {
		System.out.println("f2(double) ");
	}
	
	
	
	void f3(short x) {
		System.out.println("f3(short) ");
	}
	void f3(int x) {
		System.out.println("f3(int) ");
	}
	void f3(long x) {
		System.out.println("f3(long) ");
	}
	void f3(float x) {
		System.out.println("f3(float) ");
	}
	void f3(double x) {
		System.out.println("f3(double) ");
	}
	
	
	
	void f4(int x) {
		System.out.println("f4(int) ");
	}
	void f4(long x) {
		System.out.println("f4(long) ");
	}
	void f4(float x) {
		System.out.println("f4(float) ");
	}
	void f4(double x) {
		System.out.println("f4(double) ");
	}
	
	
	
	void f5(long x) {
		System.out.println("f5(long) ");
	}
	void f5(float x) {
		System.out.println("f5(float) ");
	}
	void f5(double x) {
		System.out.println("f5(double) ");
	}
	
	
	void f6(float x) {
		System.out.println("f6(float) ");
	}
	void f6(double x) {
		System.out.println("f6(double) ");
	}
	
	
	void f7(double x) {
		System.out.println("f7(double) ");
	}
	
	void testConstVal() {
		System.out.println("5: ");
		f1(5);f2(5);f3(5);f4(5);f5(5);f6(5);f7(5);
		System.out.println();
	}
	void testChar() {
		char x = 'x';
		System.out.println("char: ");
		f1(x);f2(x);f3(x);f4(x);f5(x);f6(x);f7(x);
		System.out.println();
	}
	void testByte() {
		byte x =0;
		System.out.println("byte: ");
		f1(x);f2(x);f3(x);f4(x);f5(x);f6(x);f7(x);
		System.out.println();
	}
	void testShort() {
		short x =0;
		System.out.println("short: ");
		f1(x);f2(x);f3(x);f4(x);f5(x);f6(x);f7(x);
		System.out.println();
	}
	void testInt() {
		int x =0;
		System.out.println("int: ");
		f1(x);f2(x);f3(x);f4(x);f5(x);f6(x);f7(x);
		System.out.println();
	}
	void testLong() {
		long x =0;
		System.out.println("long: ");
		f1(x);f2(x);f3(x);f4(x);f5(x);f6(x);f7(x);
		System.out.println();
	}
	void testFloat() {
		float x =0;
		System.out.println("float: ");
		f1(x);f2(x);f3(x);f4(x);f5(x);f6(x);f7(x);
		System.out.println();
	}
	void testDouble() {
		double x =0;
		System.out.println("double: ");
		f1(x);f2(x);f3(x);f4(x);f5(x);f6(x);f7(x);
		System.out.println();
	}
	public static void main(String[] args) {
		PrimitiveOverloading p = new PrimitiveOverloading();
		p.testConstVal();
		p.testChar();
		p.testByte();
		p.testShort();
		p.testInt();
		p.testLong();
		p.testFloat();
		p.testDouble();
	}

}/*Output:
5: f1(int) f2(int) f3(int) f4(int) f5(long) f6(float) f7(double) 
char: 
f1(char) f2(int) f3(int) f4(int) f5(long) f6(float) f7(double) 
byte: 
f1(byte) f2(byte) f3(short) f4(int) f5(long) f6(float) f7(double) 
short: 
f1(short) f2(short) f3(short) f4(int) f5(long) f6(float) f7(double) 
int: 
f1(int) f2(int) f3(int) f4(int) f5(long) f6(float) f7(double) 
long: 
f1(long) f2(long) f3(long) f4(long) f5(long) f6(float) f7(double) 
float: 
f1(float) f2(float) f3(float) f4(float) f5(float) f6(float) f7(double) 
double: 
f1(double) f2(double) f3(double) f4(double) f5(double) f6(double) f7(double) 
*///:~
```
**如果传入的数据类型（实际参数类型）小于方法中声明的形式参数类型，实际数据类型就会被提升。char型略有不同，如果无法找到恰好接受char参数的方法，就会把char直接提升至int型。**

## 如果传入的实际参数较大，就得通过类型转换来执行窄化转换。如果不这样做，编译器就会报错。

```
void testDouble() {
		double x =0;
		System.out.println("double  argument: ");
		f1(x);f2((double)x);f3((long)x);f4((int)x);f5((short)x);f6((byte)x);f7((char)x);
	}
```


