---
title: Java编程思想第四章练习
categories: Java
tags:
  - Java
  - Thinking in Java
abbrlink: 32099
date: 2019-08-07 15:56:14
---
Java编程思想第四章练习
<!--more-->
## 第四章
### 练习1：
写一个程序，打印从1到100的值。

```
public class Test{
	public static void main(String[] args) {
		for(int i=1;i<=100;i++) {
			System.out.println(i);
		}
	}
}
```

### 练习2：
写一个程序,产生25个int类型的随机数.对于每一个随机值,使用if-else语句来讲其分类为大于，小于,或等于紧随它产生的值

```
public class Test {
    public static void main(String[] args){
        int num[] =new int[25];
        for (int i=0;i<25;i++){
            num[i]=(int)(Math.random()*100);
        }
        
        for (int j=0;j<num.length-1;j++){//一共产生了25个数，需要比较24次，所以j的循环次数是num.length-1次。
            if (num[j]>num[j+1]){
                System.out.println(num[j]+"大于"+"后面的数"+num[j+1]);
            }
            else if (num[j]<num[j+1]){
                System.out.println(num[j]+"小于"+"后面的数"+num[j+1]);
            }
            else {
                System.out.println(num[j]+"等于"+"后面的数"+num[j+1]);
            }
        }
    }
}
```

>运行及结果：
>39小于后面的数70
>70大于后面的数30
>30小于后面的数61
>61大于后面的数57
>57小于后面的数76
>76小于后面的数83
>83大于后面的数13
>13大于后面的数3
>3小于后面的数38
>38小于后面的数60
>60大于后面的数57
>57小于后面的数75
>75大于后面的数12
>12小于后面的数52
>52小于后面的数62
>62小于后面的数84
>84大于后面的数51
>51大于后面的数18
>18小于后面的数59
>59小于后面的数64
>64大于后面的数41
>41小于后面的数98
>98大于后面的数54
>54大于后面的数51

### 练习4：
写一个程序,使用两个嵌套的for循环和取余操作符来探测和打印素数

```
public class Test {
    public static void main(String[] args){
    	boolean flog;
    	for(int i=2;i<=100;i++) {
    		flog=true;
    		for(int j=2;j<i;j++) {
    			if(i%j==0) {
    				flog=false;
    			}
    		}
    		if(flog==true) {
    			System.out.println(i+" ");
    		}
    	}
    }
}
```

```
2 
3 
5 
7 
11 
13 
17 
19 
23 
29 
31 
37 
41 
43 
47 
53 
59 
61 
67 
71 
73 
79 
83 
89 
97 
```

### 练习5：
重复第三章中的练习10，不要用Integer.toBinaryString()方法，而是用三元操作符和按位操作符来显示二进制0和1. 

```
emmmmmmmmmm
```

## 练习7：
修改本章练习1，通过使用break关键词（或者return关键词），使其只输出范围为1~99的值。

```
public class Test{
    public static void main(String[] args){
    	for(int i=0;i<100;i++) {
    		System.out.println(i);
    		if(i==99)
    			break; //return
    	}
    }
}
```
