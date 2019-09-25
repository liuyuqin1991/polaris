## JavaScript规定了几种语言类型

> 7种，根据堆栈储存方式的不同分为简单类型（下面前6种）和复杂类型（object）

* undefined 
* null
* boolean
* number
* string
* symbol
* object

![](https://github.com/liuyuqin1991/polaris/blob/master/frontend/note/note-images/javascript-type.png)

## JavaScript对象的底层数据结构是什么

> 有3中类型的数据结构：

* 栈和队列：类数组的结构，它们只是在插入和删除数据上有所不同
* 链表、树和图： 拥有节点的结构，并且节点有对其他节点的指针
* 哈希表依赖哈希函数保存和定位数据

## Symbol类型在实际开发中的应用

* 代替常量
* 防止变量重复

## JavaScript中的变量在内存中的具体存储形式

> JavaScript中的变量分为基本类型和引用类型，变量的储存方式取决于类型

* 基本类型：以键值对的方式储存在栈内存中
* 复杂类型：会在堆内存中开辟一块空间，储存这个对象的值，并同时在栈内存中储存变量和指向对象的指针，因为JavaScript不允许直接访问堆内存中的位置

## 基本类型的装箱与拆箱

* 装箱：直接使用基本类型调用方法（隐式装箱），new一个基本类型对象调用方法（显式装箱）
```
number 隐式装箱
var num = 1234;
num.toFixed(2) // '1234.00'

number 显式装箱
var num = new Number(1234)
num.toFiexed(2)
```

* 拆箱：把引用类型的值当做基本类型的值来使用

## null和undefined的区别

* null：表示空对象指针，将null赋值给变量，就表示该变量指向空对象；意料之中
* undefined：表示未定义，声明一个变量但不初始化，那么它的值就是undefined；意料之外

## javascript 数据类型判断

* typeof
* instanceof
* Object.prototype.toString.call

## 

