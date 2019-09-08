---
title: Foreach语句
tags:
  - Java
  - Foreach
abbrlink: 3213
date: 2019-08-07 14:28:57
---
Foreach语句
<!--more-->
## java SE5引入了一种新的更加简洁的for语法用于数组和容器，即foreach语法，表示不必创建int变量去对由访问项构成的序列进行计数，foreach将自动产生每一项。

```
import java.util.Random;

public class ForEachFloat{
    public static void main(String[] args){
        Random rand = new Random(47);
        float f[] = new float[10];
        for(int i = 0;i < 10;i++)
            f[i]=rand.nextFloat();
        for(float x:f)
            System.out.println(x);
    }
}
```

>运行及结果：
>0.72711575
>0.39982635
>0.5309454
>0.0534122
>0.16020656
>0.57799757
>0.18847865
>0.4170137
>0.51660204
>0.73734957


```
public class ForEachFloat{
    public static void main(String[] args){
        for(char c:"An African Swallow".toCharArray())
        	System.out.print(c+" ");	
    }
}
```

>运行及结果：
>A n   A f r i c a n   S w a l l o w 


