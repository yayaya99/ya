---
title: Java匿名内部类实现工厂化生产
categories: Java
tags:
  - Java
  - 匿名内部类
abbrlink: 15770
date: 2019-09-15 12:56:42
---

Java匿名内部类实现工厂化生产
<!--more-->

```
interface Service{
	void method1();
	void method2();
}
interface ServiceFactory{
	Service getService();
}
class Implementation1 implements Service{
	private Implementation1(){}  //构造器私有，禁止new
	public void method1() {System.out.println("Implementation1 method1");}
	public void method2() {System.out.println("Implementation1 method2");}
	public static ServiceFactory factory = new ServiceFactory() {
		@Override
		public Service getService() {
			return new Implementation1();
		}
	};
}
class Implementation2 implements Service{
	private Implementation2(){}
	public void method1() {System.out.println("Implementation2 method1");}
	public void method2() {System.out.println("Implementation2 method2");}
	public static ServiceFactory factory = new ServiceFactory() {
		@Override
		public Service getService() {
			return new Implementation2();
		}
	};
}
public class Factories{
	public static void serviceConsumer(ServiceFactory fact) {
		Service s = fact.getService();
		s.method1();
		s.method2();
	}
	public static void main(String[] args) {
		serviceConsumer(Implementation1.factory);
		serviceConsumer(Implementation2.factory);
	}
}/*Output:
Implementation1 method1
Implementation1 method2
Implementation2 method1
Implementation2 method2
*///:~
```

```
interface Game{boolean move();}
interface GameFactory{Game getGame();}
class Checkers implements Game{
	private Checkers() {}
	private int moves = 0;
	private static final int MOVES = 3;
	@Override
	public boolean move() {
		System.out.println("Checkers move "+moves);
		return ++moves!=MOVES;
	}
	public static GameFactory factory  = new GameFactory() {
		@Override
		public Game getGame() {
			// TODO 自动生成的方法存根
			return new Checkers();
		}
	};
}
class Chess implements Game{
	private Chess() {}
	private int moves = 0;
	private static final int MOVES =4;
	@Override
	public boolean move() {
		System.out.println("Chess mpve "+moves);
		return ++moves!=MOVES;
	}
	public static GameFactory factory = new GameFactory() {
		@Override
		public Game getGame() {
			// TODO 自动生成的方法存根
			return new Chess();
		}
	};
}
public class Games{
	public static void playGame(GameFactory factory) {
		Game s = factory.getGame();
		while(s.move())
			;
	}
	public static void main(String[] args) {
		playGame(Checkers.factory);
		playGame(Chess.factory);
	}
}/*Output:
Checkers move 0
Checkers move 1
Checkers move 2
Chess mpve 0
Chess mpve 1
Chess mpve 2
Chess mpve 3
*///:~
```

