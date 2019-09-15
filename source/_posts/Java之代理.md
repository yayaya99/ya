---
title: Java之代理
categories: Java
tags:
  - Java
  - 代理
abbrlink: 34810
date: 2019-09-15 12:07:18
---
Java并没有提供对它的直接支持。这是继承与组合之间的中庸之道，因为我们将一个成员对象置于所要构造的类中（就像组合），但与此同时我们在新类中暴露了该对象的所有方法（就像继承）。例如，太空船需要一个控制模块：

<!--more-->
```
public class SpaceShipCotrols{
	void up(int velocity) {}
	void down(int velocity) {}
	void left(int velocity) {}
	void right(int velocity) {}
	void forward(int velocity) {}
	void back(int velocity) {}
	void turBoost(int velocity) {}
}
```

构造太空船的一种方式是使用继承：

```
public class SpaceShip extends SpaceShipCotrols{
	private String name;
	public SpaceShip(String name) {this.name=name;}
	public String toString() {return name;}
	public static void main(String[] args) {
		SpaceShip protector = new SpaceShip("NSEA Protector");
		protector.forward(100);
	}
}
```

然而，SpaceShip并非真正的SpaceShipControls类型，即便你可以“告诉”SpaceShip向前运动（forward()）。更准确地讲，SpaceShip包含SpaceShipControls，与此同时，SpaceShipControls的所有方法在SpaceShip中都暴露了出来。代理解决了此难题：

```
public class SpaceShipDelegation{
	private String name;
	private SpaceShipControls controls = new SpaceShipControls();
	public SpaceShipDelegation(String name) {
		this.name = name;
	}
	public void back(int velocity) {
		controls.back(velocity);
	}
	public void down(int velocity) {
		controls.down(velocity);
	}
	public void forward(int velocity) {
		controls.forward(velocity);
	}
	public void left(int velocity) {
		controls.left(velocity);
	}
	public void right(int velocity) {
		controls.right(velocity);
	}
	public void turBoost(int velocity) {
		controls.turBoost(velocity);
	}
	public void up(int velocity) {
		controls.up(velocity);
	}
	public static void main(String[] args) {
		SpaceShipDelegation protector = new SpaceShipDelegation("NSEA Protector");
		protector.forward(100);
	}
}
```

可以看到，上面的方法是如何传递给了底层的controls对象，而其接口由此也就与使用继承得到的接口相同了。