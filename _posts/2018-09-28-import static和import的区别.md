﻿---
layout:     post
title:      import static和import的区别
subtitle:   the difference between import static and import
date:       2018-09-28
author:     BY
header-img: img/post-bg-universe.jpg
catalog: true
tags:
    - Blog
---


## 前言

现在Java 11已经发布了，可是Java 1.5引入的特性都没见过。真是有点out了。

## 正文

### 问题来源

在看quartz示例代码的时候看到import static，瞬间觉得自己是不是不会用Java了。

#### import static

import static静态导入是JDK1.5中的新特性。一般我们导入一个类都用 import com.....ClassName;而静态导入是这样：import static com.....ClassName.*;这里的多了个static，还有就是类名ClassName后面多了个 .* ，意思是导入这个类里的静态方法。当然，也可以只导入某个静态方法，只要把 .* 换成静态方法名就行了。然后在这个类中，就可以直接用方法名调用静态方法，而不必用ClassName.方法名 的方式来调用。   
这种方法的好处就是可以简化一些操作，例如打印操作System.out.println(...);就可以将其写入一个静态方法print(...)，在使用时直接print(...)就可以了。   
但是这种方法建议在有很多重复调用的时候使用，如果仅有一到两次调用，不如直接写来的方便  

#### 对比列子

在Java 5中，import语句得到了增强，以便提供甚至更加强大的减少击键次数功能，虽然一些人争议说这是以可读性为代价的。这种新的特性成为静态导入。

当你想使用static成员时，可以使用静态导入（在API中的类和你自己的类上，都可以使用该特性）。下面是静态导入前后的代码实例：

在静态导入之前：
```
public class TestStatic { 
    public static void main(String[] args) { 
        System.out.println(Integer.MAX_VALUE); 
        System.out.println(Integer.toHexString(42)); 
    } 
}
```
在静态导入之后：
```
import static java.lang.System.out; 
import static java.lang.Integer.*; 
 
public class TestStaticImport { 
    public static void main(String[] args) { 
        out.println(MAX_VALUE); 
        out.println(toHexString(42)); 
    } 
}
```
两个类都产生相同的输出：
```
2147483647 
2a
```
#### 例子发生的故事

让我们看一下使用静态导入特性的代码中将发生什么：  
1、虽然该特性通常称为“静态导入”，但语法必须是import static，后面跟你想导入的static成员的完全限定名称，或者通配符。在本例中，我们在System类的out对象上进行静态导入。  
2、在本例中，我们可能想使用java.lang.Integer类的几个static成员。该静态导入语句使用通配符来表达“我想在此类中的所有静态成员上进行静态导入”。  
3、现在我们终于看到静态导入特性的好处！我们不必在System.out.println中键入System。太好了！另外，我们不必在Integer.MAX_VALUE中键入Integer。因此，在这行代码中，我们能够将快捷方式用于静态方法和一个常量。  
4、最后，我们进行更多的快捷操作，这次针对Integer类的方法。  
关于该特性，我们已经有点儿讽刺意味儿了，但不仅我们是这样的。我们不认为节省少量的击键次数会让代码难于阅读一点，但许多开发人员要求将它添加到语言中。  

#### 注意：

你必须说import static， 不能说static import。  
提防含糊不清的命名static成员。例如，如果你对Integer类和Long类执行了静态导入，引用MAX_VALUE将导致一个编译器错误，因为Integer和Long都有一个MAX_VALUE常量，并且Java不会知道你在引用哪个MAX_VALUE。  
你可以在static对象引用、常量（记住，它们是static 或final）和static方法上进行静态导入。  

#### 总结

 借助J2SE 1.5里提供的Static Import机制，可以用一种更简单的方式，来访问类和接口的静态成员。不过，使用这一机制并不是没有代价的，在使用不当的时候可能给维护工作带来一定的困扰。因此，在具体使用之前，还要作一些两方面的权衡。

## 结语
查漏补缺。
