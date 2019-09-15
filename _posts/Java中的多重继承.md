---
title: Java中的多重继承
categories: Java
tags:
  - Java
  - 多继承
abbrlink: 59292
date: 2019-09-15 12:38:48
---

Java中的多重继承
<!--more-->

```
interface CanFight{
	void fight();
}
interface CanSwim{
	void swim();
}
interface CanFly{
	void fly();
}
class ActionCharacter{
	public void fight() {}
}
class Hero extends ActionCharacter implements CanFight,CanSwim,CanFly{
	public void swim() {}
	public void fly() {}
}
public class Adventure{
	public static void t(CanFight x) {x.fight();}
	public static void u(CanSwim x) {x.swim();}
	public static void v(CanFly x) {x.fly();}
	public static void w(ActionCharacter x) {x.fight();}
	public static void main(String[] args) {
		Hero h = new Hero();
		t(h);
		u(h);
		v(h);
		w(h);
	}
}
```