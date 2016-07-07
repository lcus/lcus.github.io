---
layout: post
title: "NSObject的load和initialize"
date: 2016-06-27 11:15:16 +0800
comments: true
categories: 
---
`Objective-C`中的基类中`NSObject`中有两个方法`load`和`initialize`,看了很多资料 来对这两个方法做一下整理。

###+load
**+load** 方法是当类或者分类加载的时候调用的，实现这个方法可以让我们在类加载的时候执行一下行为，一般方法混淆（**Method Swizzling**）都在这里进行；如果子类没有实现**+load**方法 不会去调用父类的**+load**方法，当一个类和它的分类都实现了**+load**方法，这个两个方法都会被调用;

###+initialize

**+initialize** 方法是类或者它的子类收到第一条消息时候被调用的，**+initialize**方法是以一种懒加载的方式被调用的，如果始终没有一个类或者它的子类发消息，那么这个类的**+initialize**方法永远不会调用，这样有效的节省了资源。如果一个子类没有实现**+initialize**方法，它的父类的实现方法还是被调用执行，所以有时候想要保证**+initialize**方法执行一次 我们需要在内部判断一下类的类型。

###验证


