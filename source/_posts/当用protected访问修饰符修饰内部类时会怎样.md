---
title: 当用protected访问修饰符修饰内部类时会怎样
categories: Java
tags:
  - Java
  - protected
abbrlink: 20356
date: 2019-09-15 12:50:50
---

在第十章的练习6中，遇到了这个问题。

在查找问题时，发现了下面这篇博文，内容通俗易懂，看过之后很受启发，但我文笔不好，所以直接引用过来学习。

哈哈我好无耻。。

转自 https://blog.csdn.net/clarkdu/article/details/334925
<!--more-->


```
// in SuperClass.java
package com.duwei.SuperClass;
        
class SuperClass {
        protected class InnerClass{  // 错误根源
                                
        }
}

// in SubClass.java
package com.duwei.SubClass

import com.duwei.SuperClass.*;

class SubClass extends SuperClass {
        public void func() {
                InnerClass ic = new InnerClass();  // 导致错误
        }
}
```

对protected访问修饰符理解的还不是很深刻的朋友会觉得这没什么程序很正常. 程序行为都很合乎情理. 其实不然, 程序在编译的时候会报错, 错误信息为InnerClass() has protected access in com.duwei.SuperClass.InnerClass.

这是为什么? 我的SuperClass类里的内部类InnerClass已经被定义为protected了, 而且Java保证了被protected所修饰的东西都可以在其子类中使用呀!!! 但, 请再仔细看看错误信息的内容, 原来并不是InnerClass类有什么问题, 而是InnerClass类中的InnerClass()方法出现了问题, InnerClass()这不是InnerClass类的构造函数吗!!! 看来问题找到一半了, 我们在学习Java的时候都知道, 如果一个类没定义任何形式的构造函数时, Java编译器会自动为类加上一个, 但问题就在这, 很多人不会重视这个自动被加上的构造函数的访问级别为何! 不过在此提到了可能大家也就都想起来了, 事实上这个被自动加上的构造函数的访问级别与类相同! 我们在回到刚才的问题上, 这时我们会发现原来InnerClass类在定义时并没有写构造函数, 编译时被自动加入的构造函数访问级别与类相同, 也就是protected. 这时我想大家应该明白为什么程序会出问题了吧!!!

原来在SubClass类中的func()方法里实例化InnerClass类时出了问题, 当然单从InnerClass的访问级别为protected来讲这样做没什么问题, 但实例化就得调用构造函数, 也就是在调用了InnerClass类的构造函数时, 由于这个被编译器自动加上的构造函数沿袭了InnerClass类的访问级别为protected, 所以这个构造函数只能在InnerClass的子类中或者同一个包中被调用, 而此时只是简单的实例化InnerClass类而并不存在什么子类而且又是在另一个包中, 再说Java只允许在同一个类中的内部类继承另一个内部类, 而且这种操作的允许范围仅此而以, 所以问题的终于要水落石出了, 由于InnerClass类的构造函数只允许其子类调用而不允许其它形式的调用, 所以此时对于InnerClass类来讲无法调用其构造函数来实例化对象. 至此问题找到了. 解决问题的方法也很简单, 只要在InnerClass类中定义一个public访问级别的构造函数就可以了.

由此我们可以看出, 有时候程序的某些特征是深藏不露, 如果你不去那样想是很难发现它的.

本文链接：https://blog.csdn.net/clarkdu/article/details/334925