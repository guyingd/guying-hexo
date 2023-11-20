---
title: 跟随狂神学Java-03，基础语法
date: 2022/6/14 22:01:11
tags:
  - 狂神
  - Java
  - JavaSE
categories:
  - [跟随狂神学Java]
  - [Java]
cover: https://resource.joker2yue.cn/blog/images/coverImg/JavaSE/04.jpg
copyright: true
copyright_author: joker2yue
copyright_author_href: https://github.com/Joker2Yue
copyright_url: https://github.com/Joker2Yue/Joker2Yue-Blog
keywords:
  - Java
  - 注释
  - 标识符
  - 强类型语言
  - 数据类型
  - 进制
  - 输出
  - 逻辑运算
  - 位运算
  - 短路逻辑运算
  - 三元运算符
ai: 
  - 这篇文章是"跟随狂神学Java"系列的第三天内容，主要介绍了Java的基础语法。文章首先讨论了注释的使用方式，包括单行注释、多行注释和JavaDoc文档注释。接着，文章解释了标识符的概念，强调Java中的标识符是大小写敏感的。然后，文章提到Java是强类型语言，要求变量必须先定义后使用。文章还介绍了不同的数据类型，包括整数类型和字符串类型，并提到了进制表示法。此外，文章展示了一般的输出方法和逻辑运算，包括逻辑运算符的使用和位运算。最后，文章介绍了短路逻辑运算和三元运算符的概念。通过简单的示例和清晰的文字，文章帮助读者建立了对Java基础语法的初步了解。
  - 这篇文章介绍了Java的基础语法，包括注释、标识符、数据类型、进制、输出、逻辑运算、位运算、短路逻辑运算、三元运算符等内容，以帮助初学者建立Java编程的基本概念。
  - 这篇文章介绍了Java的基础语法要点，包括注释、标识符、数据类型、进制、输出、逻辑运算、位运算、短路逻辑运算和三元运算符。文章以简明的示例和文字说明帮助读者理解这些基础概念。
---
# 跟随狂神学Java
> 作者：[joker2yue](https://github.com/Joker2Yue)
> 链接：https://github.com/Joker2Yue/Joker2Yue-Blog
> 来源：Github
> 著作权归原作者所有。商业转载请联系原作者获得授权，非商业转载请注明出处。
##### 第三天：基础语法

> 好戏开场了！

---

## 学习内容

#### 注释

~~~java
//单行注释

/*多行
  注释*/

//JavaDoc文档注释
/**
 * @description HelloWorld
 * @author		Joker_Yue
 */
~~~



#### 标识符

Java 所有的组成部分都需要名字。类名、变量名以及方法名都被称为标识符

标识符是大小写敏感的



#### Java是强类型语言

要求变量的使用都必须严格符合规定，所有的变量都必须先定义后才能使用



#### 数据类型

![在这里插入图片描述](./跟随狂神学Java-3/d77a4a2a703e4348b89373d6d9666061.png)



> 注意：String不是关键字，是类

int : 		-2<sup>31</sup>-1 ~ 2<sup>31</sup>

byte: 	  -2<sup>7</sup>-1 ~ 2<sup>7</sup>

==最好完全避免使用浮点数进行比较==



#### 进制

> 二进制：0b 
>
> 十进制
>
> 八进制：0
>
> 十六进制： 0x

~~~java
int i=10;	//十进制
int j=010;	//八进制
int k=0x10;	//十六进制
~~~



#### 一般输出

~~~java
System.out.println();                //输出整行
System.out.print();                  //普通输出
System.out.print("我今年"+18+"岁了");  //组合输出
~~~






#### 逻辑运算
~~~java
System.out.println(true | false);   //会输出true
System.out.println(20>10);      	//会输出true
System.out.println(true ^ false);   //会输出true(两个要不一样）
~~~

~~~java
/*
A   = 0011 1100
B   = 0000 1101

A&B = 0000 1100		//并，两者为1才为1
A|B = 0011 1101		//或，一者为1就为1
A^B = 0011 0001		//异或，两者不同即为1
~B  = 1111 0010		//取反，零变一，一变零
*/
~~~

~~~java
//	0 ： 0000 0000
//	1 ： 0000 0001
//	2 ： 0000 0010
//	3 ： 0000 0011
//  4 ： 0000 0100
//	8 ： 0000 1000
//  16：	0001 0000

System.out.println(2<<3);	//会输出16
~~~



#### 短路逻辑运算
&&和||    有几率不会判断右边的东西



#### 三元运算符

~~~java
面试成功?明天上班:回家种田;		//三元运算符
~~~

