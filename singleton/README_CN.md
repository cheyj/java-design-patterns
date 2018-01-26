---
layout: pattern
title: Singleton
folder: singleton
permalink: /patterns/singleton/
categories: Creational
tags:
 - Java
 - Gang Of Four
 - Difficulty-Beginner
---

## Intent
Ensure a class only has one instance, and provide a global point of
access to it.  
确保一个类只有一个实例，并提供一个全局的访问点。


## Explanation
Real world example

> There can only be one ivory tower where the wizards study their magic. The same enchanted ivory tower is always used by the wizards. Ivory tower here is singleton.
> 那里只能有一座象征着巫师学习魔法的象牙塔。巫师总是使用同样的象牙塔。这里的象牙塔是单例的。
  
In plain words

> Ensures that only one object of a particular class is ever created.
> 确保只创建一个特定类的一个对象。

Wikipedia says

> In software engineering, the singleton pattern is a software design pattern that restricts the instantiation of a class to one object. This is useful when exactly one object is needed to coordinate actions across the system.
> 在软件工程中，单例模式是一种软件设计模式，它将一个类的实例化限制为一个对象。当需要恰好一个对象来协调系统中的操作时，这是非常有用的。

**Programmatic Example**

Joshua Bloch, Effective Java 2nd Edition p.18

> A single-element enum type is the best way to implement a singleton
> 枚举是单例模式的最好方式

```
public enum EnumIvoryTower {
  INSTANCE;
}
```

Then in order to use

```
EnumIvoryTower enumIvoryTower1 = EnumIvoryTower.INSTANCE;
EnumIvoryTower enumIvoryTower2 = EnumIvoryTower.INSTANCE;
assertEquals(enumIvoryTower1, enumIvoryTower2); // true
```

## Applicability
Use the Singleton pattern when

* there must be exactly one instance of a class, and it must be accessible to clients from a well-known access point
* when the sole instance should be extensible by subclassing, and clients should be able to use an extended instance without modifying their code

## Typical Use Case

* the logging class
* managing a connection to a database
* file manager

## 经典用例
* 日志记录类
* 管理数据库连接
* 文件管理器

## Real world examples

* [java.lang.Runtime#getRuntime()](http://docs.oracle.com/javase/8/docs/api/java/lang/Runtime.html#getRuntime%28%29)
* [java.awt.Desktop#getDesktop()](http://docs.oracle.com/javase/8/docs/api/java/awt/Desktop.html#getDesktop--)
* [java.lang.System#getSecurityManager()](http://docs.oracle.com/javase/8/docs/api/java/lang/System.html#getSecurityManager--)


## Consequences

* Violates Single Responsibility Principle (SRP) by controlling their own creation and lifecycle.
* Encourages using a global shared instance which prevents an object and resources used by this object from being deallocated.     
* Creates tightly coupled code. The clients of the Singleton become difficult to test.
* Makes it almost impossible to subclass a Singleton.

## Credits

* [Design Patterns: Elements of Reusable Object-Oriented Software](http://www.amazon.com/Design-Patterns-Elements-Reusable-Object-Oriented/dp/0201633612)
* [Effective Java (2nd Edition)](http://www.amazon.com/Effective-Java-Edition-Joshua-Bloch/dp/0321356683)
