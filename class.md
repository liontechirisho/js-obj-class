# You don't know JS
## 混合（淆）“类”的对象 class
***
### 引言
class概念并不是非常自然地映射到 JS 的对象机制上，许多 JavaScript 开发者为了克服这些挑战所做的努力（mixins等）。
(Me: 畢竟是後來的語言要吸引大家使用)

1. 物件導向設計
<a src='https://zh.wikipedia.org/wiki/%E9%9D%A2%E5%90%91%E5%AF%B9%E8%B1%A1%E7%A8%8B%E5%BA%8F%E8%AE%BE%E8%AE%A1'>
Object-oriented programming OOP
</a>

2. CLASS 類別

3. 類別的機制:“实例化（instantiation）”, “继承（inheritance）”与“（相对）多态(relative polymorphism）”。


### Class 類理論

强调数据和操作它的行为之间有固有的联系

什麼是物件=> 模型/藍圖
(圖)

OOP的三大特性: 封裝、繼承、多型
1. 資料封裝(Encapsulation)
```
表示一个单词或短语的一系列字符通常称为“string（字符串）”。
这些字符就是数据。
你总是想对数据 做事情， 所以可以 向 数据实施的行为
（计算它的长度，在末尾添加数据，检索，等等）
都被设计成为 String 类的方法。
```
   **任何给定的字符串都是这个类的一个实例**

   資料封裝就是將資料分成私用(Private)、保護(Protected)、公用(Public)等，實踐 Information hiding 概念, 避免程式各個物件互相干擾，降低程式的複雜度及維護上的困難度。

2. 繼承(Inheritance)
  ##### 類=類別
  **載具與車子**
  每一种不同类型的载具一次又一次地重定义“载人能力”这个基本性质可能没有道理。
  反而，我们在 Vehicle 中把这个能力定义一次，之后当我们定义 Car 时，
  我们简单地指出它从基本的 Vehicle 定义中“继承”（或“扩展”）。
  有繼承的關係後，父類別 (Super class) 中的資料 (Data) 或方法 (Method) 在次子類(Subclass)就可以繼承使用，次子類別的次子類別也可以繼承使用，最後即能達到資料重覆使用的目的。

3. 多型(Polymorphism)
   于父类的泛化行为可以被子类覆盖，从而使它更加具体。实际上，相对多态允许我们在覆盖行为中引用基础行为。
   多型(Polymorphism) 代表能夠在執行階段，物件能夠依照不同情況變換資料型態，換句話說，多型是指一個物件參考可以在不同環境下，扮演不同角色的特性，指向不同的物件實體，可 透過實作多個繼承或介面來實現父類別，並使用Override或Overload來達成。

小山圖
<img src="https://www.evernote.com/shard/s493/res/c002ca1c-6ec3-4b08-9046-0d00224d1426">

![](https://drive.google.com/file/d/1V9ukA1l90Dd_FAubxclL8x1gMOZEWWty/view?usp=sharing)

https://www.youtube.com/watch?v=gpjAFBh3GJ4

### 物件導向的編程

procedural programming
VS oop
(圖)

有些语言（比如 Java）不给你选择，所以这根本没什么 选择性 —— 一切都是类。
其他语言如 C/C++ 或 PHP 同时给你过程式和面向类的语法，在使用哪种风格合适或混合风格上，留给开发者更多选择。

### 總結: 類的定義
而類別則較具抽象的概念，也就是某些具有共同特性物件的集合
換句話說，物件就是類別的實體。
物件導向具有封裝、繼承、多型等特性，原則上 每個物件相互獨立且無關聯性
而物件導向程式設計就是依照物件的方法產生互 動以完成要求。

### Class-based vs Prototype-based programming
##### class-based

* 哪些?Others include PHP, C++, Java, C#, and Objective-C.
* 作用方式
有standard library提供"stack" data structure  成為  Stackclass.
Stackclass 有個內部設計，儲存變數的資料DATA
可以使用Public methods(類中定義好的)去存取data
使得開發者可以操作DATA

Stack長相
(圖)
了解更多
https://blog.gtwang.org/programming/memory-layout-of-c-program/

 ```
 原文:
 "standard library" provides a "stack" data structure (push, pop, etc.) as a Stackclass.
This class would have an internal set of variables that stores the data,
and it would have a set of publicly accessible behaviors ("methods") provided by the class,
which gives your code the ability to interact with the (hidden) data (adding & removing data, etc.).
```

##### js 原型鍊運作方式
Prototype-based programming
先實例化出一個物件
才有DATA給你操作
沒有存在class 的methods給你訪問DATA
<a src="https://www.deviantart.com/stumbling-poncho/art/Grasping-Prototype-Based-Programming-269761176">看漫畫學JS</a>

```
You must instantiate the Stack class
before you have a concrete data structure thing to operate against.
http://www.kwongwah.com.my/wp-content/uploads/2018/10/181017gn015.jpg
```
### js裡面沒有類
