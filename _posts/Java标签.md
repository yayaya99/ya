---
title: Java标签
categories: Java
tags:
  - Java
  - 标签
abbrlink: 53890
date: 2019-08-07 18:56:44
---
Java标签
<!--more-->
## Java标签,博文内容剽窃于Thinking in Java第四版四章4.7  (●'◡'●)

```
label1:
outer-iteration{
    inner-iteration{
        //...
        break; //(1)
        //...
        continue; //(2)
        //...
        continue label1; //(3)
        //...
        break label1; //(4)
    }
}
```


在（1）中，break中断内部迭代。
在（2）中，continue使执行点移回内部迭代的起始值。
在（3）中，continue label1同时中断内部迭代以及外部迭代，直接转到label1处；随后，它实际上是继续迭代过程，但却从外部迭代开始。
在（4）中，break label1也会中断所有迭代，并回到label1处，但并不重新进入迭代。也就是说，它实际是完全中止了两个迭代。

```
public class Test{
    public static void main(String[] args){
    	int i=0;
    	outer:
    		for(;true;) {
    			inner:
    				for(;i<10;i++) {
    					System.out.println("i= "+i);
    					if(i==2) {
    						System.out.println("continue");
    						continue;
    					}
    					if(i==3) {
    						System.out.println("break");
    						i++;    //由于break跳过了递增表达式，所以这里添加了递增运算
    						break;
    					}
    					if(i==7) {
    						System.out.println("continue outer");
    						i++;    //添加了递增运算
    						continue outer;
    					}
    					if(i==8) {
    						System.out.println("break outer");
    						break outer;
    					}
    					for(int k=0;k<5;k++) {
    						if(k==3) {
    							System.out.println("continue inner");
    							continue inner;
    						}
    					}
    				}
    		}
    }
}
```

>Output:
>i= 0
>continue inner
>i= 1
>continue inner
>i= 2
>continue
>i= 3
>break
>i= 4
>continue inner
>i= 5
>continue inner
>i= 6
>continue inner
>i= 7
>continue outer
>i= 8
>break outer

***break和continue本身只能中断最内层的循环***

## 带标签的break以及continue语句在while循环中的用法：

```
public class Test{
    public static void main(String[] args){
    	int i=0;
    	outer:
    		while(true) {
    			System.out.println("Outer while loop");
    			while(true) {
    				i++;
    				System.out.println("i= "+i);
    				if(i==1) {
    					System.out.println("continue");
    					continue;
    				}
    				if(i==3) {
						System.out.println("continue outer");
						continue outer;
					}
    				if(i==5) {
						System.out.println("break");
						break;
					}
    				if(i==7) {
						System.out.println("break outer");
						break outer;
					}
    			}
    		}
    }
}
```

>Output:
>Outer while loop
>i= 1
>continue
>i= 2
>i= 3
>continue outer
>Outer while loop
>i= 4
>i= 5
>break
>Outer while loop
>i= 6
>i= 7
>break outer

同样的规则亦适用于while:
1、一般的continue会退出最内层循环开头（顶部），并继续执行。
2、带标签的continue会到达标签的位置，并重新进入紧接在那个标签后面的循环。
3、一般的break会中断并跳出当前循环。
4、带标签的break会中断并跳出标签所指的循环。

## 在Java里需要使用标签的唯一理由就是因为有循环嵌套存在，而且想从多层嵌套中break或continue。

