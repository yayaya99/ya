---
title: class.getName()和class.getSimpleName()的区别
categories: Java
tags:
  - Java
  - getName()
  - getSimpleName()
abbrlink: 50070
date: 2019-09-15 12:37:07
---

class.getName()和class.getSimpleName()的区别
<!--more-->

Class.getName()：以String的形式，返回Class对象的“实体”名称；

Class.getSimpleName()：获取源代码中给出的“底层类”简称。

```
public class Main {
	
	private static final String TAG1 = Main.class.getName();
	private static final String TAG2 = Main.class.getSimpleName();
	
	public static void main(String[] args) {
		System.out.println("getName ----- " + TAG1 + "\n" + "getSimpleName ----- " + TAG2);
	}
}/*Output:
getName ---- com.se7en.test.Main
getSimpleName ---- Main
*///:~
```

getName ----“实体名称” ---- com.se7en.test.Main

getSimpleName ---- “底层类简称” ---- Main


getName() 获取包名+类名;getSimpleName() 获取类名。