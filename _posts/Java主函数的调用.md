---
title: Java主函数的调用
categories: Java
tags:
  - Java
abbrlink: 48045
date: 2019-08-10 16:28:07
---
Java主函数的调用
<!--more-->
一个java文件里可以存在多个class，但是只能有一个public class

你可以创建一个String对象数组，将其传递给另一个main（）方法，以提供参数，用来替换传递给该main（）方法的命令行参数。

```
public class DynamicArray{
	public static void main(String[] args) {
		Other.main(new String[] {"fiddle","de","dum"});
	}
}
class Other{
	public static void main(String[] args) {
		for(String s:args) {
			System.out.println(s+" ");
		}
	}
}/*Output:
fiddle 
de 
dum 
*///:~
```