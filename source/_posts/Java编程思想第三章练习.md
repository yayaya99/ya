---
title: Java编程思想第三章练习
tags:
  - Java
  - Thinking in Java
abbrlink: 26010
date: 2019-08-04 09:35:12
---
## 第三章

### 练习5：
创建一个名为Dogde类，它包含两个String域：name和scruffy（它的叫声为“Ruff!”）,另一个名为scruffy（它的叫声为“Wurf！”）。然后显示它们的名字和叫声。
练习6：
创建一个新的Dog索引，并对其赋值为spot对象。测试用==和equals()方法比较所有引用的结果。
 
 
```
class Dog{
	String name;
	String says;
	
	void shows() {
		System.out.println("name: "+name+" Says: "+says);
	}
}
public class Test{
	public static void main(String[] args) {
		Dog spot = new Dog();
		spot.name="Spot";
		spot.says="Ruff!";
		Dog scruffy = new Dog();
		scruffy.name="Sruffy";
		scruffy.says="Wufrf!";
		
		spot.shows();
		scruffy.shows();
		
		Dog newDog = new Dog();
		newDog = spot;
		System.out.println(newDog==spot);
		System.out.println(newDog.equals(spot));
		
	}
}
```
>运行及结果：
>name: Spot Says: Ruff!
>name: Sruffy Says: Wufrf!
>true
>true

<!--more-->

### 练习7：
编写一个程序，模拟扔硬币的结果。

```
import java.util.Random;

class Coin{
	static void test() {
		Random r = new Random();
		System.out.println(r.nextInt(2) == 1?"正面":"反面");
	}
}
public class Test{
	public static void main(String[] args) {
		Coin.test();
	}
}

```

### 练习8：
展示用16进制和8进制记数法（字面值）来操作long值（赋值），用Long.toBinaryString()来显示其结果。

```
public class Test{
	public static void main(String[] args) {
		long l1=0xC2B;
		long l2=0777;
		System.out.println(Long.toBinaryString(l1));
		System.out.println(Long.toBinaryString(l2));
		
	}
}
```

### 练习9：
分别显示用float和double指数计数法所能表示的最大和最小的数字

```
public class Test{
	public static void main(String[] args) {
		
		float floatmax = Float.MAX_VALUE;
		float floatmin = Float.MIN_VALUE;
		double doublemax = Double.MAX_VALUE;
		double doublemin = Double.MIN_VALUE;
		
		System.out.println("floatmax = " + floatmax);
		System.out.println("floatmin = " + floatmin);
		System.out.println("doublemax = " + doublemax);
		System.out.println("doublemin = " + doublemin);
	}
}
```

>运行及结果：
>floatmax = 3.4028235E38
>floatmin = 1.4E-45
>doublemax = 1.7976931348623157E308
>doublemin = 4.9E-324

### 练习10：
编写一个具有两个常量值的程序,一个具有交替的二进制位1和0,其中最低有效位为0,另一个也具有交替的二进制位1和0,其中最低有效位为1.取这两个值,用按位操作符以所有可能的方式结合运算它们,然后用Integer.toBinaryString()显示

```
public class Test{
	public static void main(String[] args) {
		int a = 0xaaaaaaaa;
		int b = 0x55555555;
		
		System.out.println("  a: "+Integer.toBinaryString(a));
		System.out.println("  b: "+Integer.toBinaryString(b));
		System.out.println(" ~a: "+Integer.toBinaryString(~a));
		System.out.println(" ~b: "+Integer.toBinaryString(~b));
		System.out.println("a&a: "+Integer.toBinaryString(a&a));
		System.out.println("a|a: "+Integer.toBinaryString(a|a));
		System.out.println("a^a: "+Integer.toBinaryString(a^a));
		System.out.println("a&b: "+Integer.toBinaryString(a&b));
		System.out.println("a|b: "+Integer.toBinaryString(a|b));
		System.out.println("a^b: "+Integer.toBinaryString(a^b));
		
	}
}
```

>运行及结果：
>  a: 10101010101010101010101010101010
>  b: 1010101010101010101010101010101
> ~a: 1010101010101010101010101010101
> ~b: 10101010101010101010101010101010
>a&a: 10101010101010101010101010101010
>a|a: 10101010101010101010101010101010
>a^a: 0
>a&b: 0
>a|b: 11111111111111111111111111111111
>a^b: 11111111111111111111111111111111


### 练习11：
以一个最高有效位为1的二进制数开始,用有符号右移操作符对其进行右移,直至所有的二进制位都被移出为止,每移一位都显示二进制字符串效果.
练习12：
以一个所有位都为1的二进制数字开始,先左移它,然后用无符号右移操作符对其进行右移,直至所有二进制位都移出为止,每移一位都要显示二进制字符串效果.

```
public class Test {
	public static void main(String[] args) {
		int number = 0xaaaaa;
		while(number != 0) {
			number >>= 1;
			System.out.println(Integer.toBinaryString(number));
		}
		
		System.out.println("====================");
		
		int number2 = 0xff;
		number2 <<= 1;
		
		while(number2 != 0) {
			number2 >>>= 1;
			System.out.println(Integer.toBinaryString(number2));
		}
	}
}

```

```
运行及结果：
1010101010101010101
101010101010101010
10101010101010101
1010101010101010
101010101010101
10101010101010
1010101010101
101010101010
10101010101
1010101010
101010101
10101010
1010101
101010
10101
1010
101
10
1
0
====================
11111111
1111111
111111
11111
1111
111
11
1
0
```

### 练习13：
编写一个方法,它以二进制形式显示char类型的值.使用多个不同的字符来展示它.

```
class TestChar{
	static void Conversion(char c) {
		System.out.println(Integer.toBinaryString((int)c));
	}
}
public class Test {
	public static void main(String[] args) {
		TestChar.Conversion('a');
		TestChar.Conversion('b');
		TestChar.Conversion('c');
		TestChar.Conversion('$');
	}
}

```

>运行及结果：
>1100001
>1100010
>1100011
>100100

