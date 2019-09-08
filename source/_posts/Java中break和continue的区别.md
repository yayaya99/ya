---
title: Java中break和continue的区别
tags:
  - Java
  - break
  - continue
abbrlink: 59837
date: 2019-08-07 15:39:50
---
Java中break和continue的区别
<!--more-->
## 在任何迭代语句的主体部分，都可用break和continue控制循环的流程

## break
1、break用于强行退出循环。
2、退出后不执行循环中剩余的语句
## continue
1、停止执行当前的迭代
2、退回循环起始处，开始下一次迭代



```
public class Test{
    public static void main(String[] args){
    	for(int i=0;i<=5;i++) {
    		if(i==3) {
    			break;
    		}
    		System.out.println(i);
    	}
    	
    	System.out.println("===============");
    	for(int i=0;i<=5;i++) {
    		if(i==3) {
    			continue;
    		}
    		System.out.println(i);
    	}
    }
}
```

>运行及结果：
>0
>1
>2
>分隔符
>0
>1
>2
>4
>5
