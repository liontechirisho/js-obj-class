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


![image](https://github.com/liontechirisho/js-obj-class/blob/master/img/blueprints2.jpg)  

![image](https://github.com/liontechirisho/js-obj-class/blob/master/img/181017gn015.jpg)  



![image](https://github.com/liontechirisho/js-obj-class/blob/master/img/oop.png)

```
圖片來源: 小山的C#教學https://www.youtube.com/watch?v=gpjAFBh3GJ4
```

### OOP的三大特性: 封裝、繼承、多型

1. **資料封裝(Encapsulation)**
```
表示一个单词或短语的一系列字符通常称为“string（字符串）”。
这些字符就是数据。
你总是想对数据 做事情， 所以可以 向 数据实施的行为
（计算它的长度，在末尾添加数据，检索，等等）
都被设计成为 String 类的方法。
```
   **任何给定的字符串都是这个类的一个实例**

   資料封裝就是將資料分成私用(Private)、保護(Protected)、公用(Public)等，實踐 Information hiding 概念, 避免程式各個物件互相干擾，降低程式的複雜度及維護上的困難度。

2. **繼承(Inheritance)**
  ##### 類=類別
  **載具與車子**
  每一种不同类型的载具一次又一次地重定义“载人能力”这个基本性质可能没有道理。
  反而，我们在 Vehicle 中把这个能力定义一次，之后当我们定义 Car 时，
  我们简单地指出它从基本的 Vehicle 定义中“继承”（或“扩展”）。
  有繼承的關係後，父類別 (Super class) 中的資料 (Data) 或方法 (Method) 在次子類(Subclass)就可以繼承使用，次子類別的次子類別也可以繼承使用，最後即能達到資料重覆使用的目的。

3. **多型(Polymorphism)**  
   于父类的泛化行为可以被子类覆盖，从而使它更加具体。实际上，相对多态允许我们在覆盖行为中引用基础行为。
   多型(Polymorphism) 代表能夠在執行階段，物件能夠依照不同情況變換資料型態，換句話說，多型是指一個物件參考可以在不同環境下，扮演不同角色的特性，指向不同的物件實體，可 透過實作多個繼承或介面來實現父類別，並使用Override或Overload來達成。



***

### 物件導向?
### procedural programming VS Object-oriented programming (OOP)

![image](https://github.com/liontechirisho/js-obj-class/blob/master/img/procedural-vs-oop.jpg)



![image](https://github.com/liontechirisho/js-obj-class/blob/master/img/DATA%20MANAGEMENT%20IN%20PROCEDURAL%20AND%20OBJECT%20ORIENTED%20MODELS.png)


有些语言（比如 Java）不给你选择，所以这根本没什么 选择性 —— 一切都是类。
其他语言如 C/C++ 或 PHP 同时给你过程式和面向类的语法，在使用哪种风格合适或混合风格上，留给开发者更多选择。

### 總結: CLASS 的定義
而類別則較具抽象的概念，也就是某些具有共同特性物件的集合
換句話說，物件就是類別的實體。
物件導向具有封裝、繼承、多型等特性，原則上 每個物件相互獨立且無關聯性
而物件導向程式設計就是依照物件的方法產生互 動以完成要求。

***

### Class-based vs Prototype-based programming
皆是ＯＯＰ的一種

![image](https://github.com/liontechirisho/js-obj-class/blob/master/img/1_0jWIHlaV3zcjjniEOrovEQ.jpeg)  

##### class-based
1. 用Class 作為**繼承**載體
2. Object是Class的實例
* 有哪些語言?  PHP, C++, Java, C#, and Objective-C....

```
延伸:https://en.wikipedia.org/wiki/Class-based_programming
```

#####
Prototype-based  (js 原型鍊運作方式)

![image](https://github.com/liontechirisho/js-obj-class/blob/master/img/grasping_prototype_based_programming_by_stumbling_poncho_d4glx20-pre.jpg)
1. 用Object 作為**繼承**載體 (objects 會被拷貝跟extend)

```
### class-based ###
水果 class
香蕉 class (extend fruit)
製造出的每個香蕉  obj (class的實例)
```

```
### Prototype-based ###
水果 object
香蕉 obj (clone fruit)
製造出的每個香蕉  obj (clone banana)
```




```
Prototype-based programming is a style of object-oriented programming in which behaviour reuse (known as inheritance) is performed via a process of reusing **existing objects** via delegation that serve as prototypes. This model can also be known as prototypal, prototype-oriented, classless, or instance-based programming. Delegation is the language feature that supports prototype-based programming.

Prototype-based programming uses generalized objects,   
which can then be cloned and extended.    
Using fruit as an example,   
a "fruit" object would represent the properties and functionality of fruit in general.   
A "banana" object would be cloned from the "fruit" object and general properties specific to bananas would be appended.   
Each individual "banana" object would be cloned from the generic "banana" object.   
Compare to the class-based paradigm, where a "fruit" class would be extended by a "banana" class.

The first prototype-oriented programming language was Self,
```

```
You must instantiate the Stack class
before you have a concrete data structure thing to operate against.
先實例化出一個物件
才有DATA給你操作
沒有存在class 的methods給你訪問DATA
```
### 其實...JS裡面沒有類
* JS 拥有 一些 像类的语法元素（比如 new 和 instanceof）有一阵子了，  
* ES6 中，还有一些追加的东西，比如 class 关键字（见附录A）。   
* **ES6裡面class 是一種語法糖**    
* 在其他语言中遇到的 类 和在 JS 中模拟的“类”不同  
* 你可以选择在 JavaScript 中使用或不使用類  

### 類機制

##### * 作用方式
* 由standard library提供"stack" (data structure)
* 成為 Stackclass。  
* Stackclass 有個內部設計，儲存變數的資料DATA  
* 可以使用Public methods(類中定義好的)去存取data，使得開發者可以操作DATA  
* Stack長相
![image](https://github.com/liontechirisho/js-obj-class/blob/master/img/memory-layout-of-c-program-diagram-20170301-1024x962.png)  

<a src="https://blog.gtwang.org/programming/memory-layout-of-c-program/">了解更多</a>

 ```
 原文:
 "standard library" provides a "stack" data structure (push, pop, etc.) as a Stackclass.
This class would have an internal set of variables that stores the data,
and it would have a set of publicly accessible behaviors ("methods") provided by the class,
which gives your code the ability to interact with the (hidden) data (adding & removing data, etc.).
```

##### 你不是直接在 Stack 上操作
* StackClass它本身不是一个“stack” 。
* 为了得到一个可以对之进行操作的实在的数据结构(data structure)
* **必须 实例化 这个 StackClass**

##### 物件就是Class的複製
This object is a copy of all the characteristics described by the class.

**一个CLASS就是一个蓝图。**
但實例做出來你才能住或吃(操作)。

一个类通过**拷贝**被实例化为物件。
```
class-based
水果 class
香蕉 class (extend fruit)
製造出的每個香蕉  obj (class的實例)
```

拷貝操作圖

![image](https://github.com/getify/You-Dont-Know-JS/blob/1ed-zh-CN/this%20%26%20object%20prototypes/fig1.png)

### 如何實例化？
* 使用构造器（constructor）  
* 这个方法的名称通常与类名相同  
* 此方法會初始化实例所需的所有信息（状态）  

```
class CoolGuy {
    specialTrick = nothing


    CoolGuy( trick ) {   //我是和class同名的構造器
        specialTrick = trick
    }


    showOff() {
        output( "Here's my trick: ", specialTrick )
    }
}
```

```
Joe = new CoolGuy( "jumping rope" )   <--- using class constructor:

Joe.showOff()   <---實例化Joe，可使用class制定且他clone下來的方法
```

***

### Class Inheritance 類的繼承

對class-based 語言來說，
1. 可以定義一個類
2. 一個類可以繼承另一類(extend)
3. 第一个类被称为“父类”，第二个类通常被称为“子类”

#####  類繼承

```
//父類 載具
class Vehicle {
	engines = 1

	ignition() {
		output( "啟動引擎" )
	}

	drive() {
		ignition()
		output( "往前開" )
	}
}
```
兩個子類

```
class Car inherits Vehicle {                       <----繼承Vehicle
	wheels = 4

	drive() {<----以同名覆蓋父類的方法
		inherited:drive()  // inherited = super  拷貝父類的方法過來
		output( "轉動輪子", wheels, " 四輪的喔!" )
	}
}

class SpeedBoat inherits Vehicle {                 <----繼承Vehicle
	engines = 2

	ignition() {
		output( "啟動引擎", engines, "是我獨門的引擎數！" )
	}

	pilot() {
		inherited:drive()  // inherited = super  拷貝父類的方法過來
		output( "看我輕功水上飄!" )
	}
}
```

* 两种具体的载具：Car 和 SpeedBoat。继承後特化。    
一辆车有4个轮子，一艘快艇有两个引擎  
* inherited:drive() Car 可以引用它继承的，原版 drive()。 (同時可以使用新的方法)  

##### 多型

这种技术称为“多型（polymorphism）”，  
**多型: 任何方法都可以引用位于继承层级上更高一层的其他（同名或不同名的）方法。**

或“虚拟多型（virtual polymorphism）”。  
作者稱之**相对多态（relative polymorphism）**  

drive() 方法的定义，根据你引用的实例是哪个类（class or Vehicle）而 多态（改变）。
```
BMW =  new Car();
BMW.drive()
// 啟動引擎  往前開 ----class Vehicle 定義的方法 位於继承层级上更高一层
// 轉動輪子 4 四輪的喔 -----class Car 定義的方法
```

##### 與JS的差別
class-based語言通过 super，从子类的构造器中直接访问父类构造器。(构造器在class中)
* 在 JS 中，这是相反的 —— **class 在構造器中（Foo.prototype... 类型引用）**。  
* 父子关系仅存在于它们各自的构造器的两个.prototype物件间，
* JS的构造器本身不直接关联
* 没有简单的方法从一个中相对引用另一个（参见附录A，看看 ES6 中用 super “解决”此问题的 class）。

```
水果 object   
香蕉 obj (clone 水果 構造器 在prototype中)  
製造出的每個香蕉  obj (clone 香蕉 構造器 在prototype中)
```

### 類繼承是拷貝
* super: 讓你可以使用繼承的class的方法   
* 理論上: 子类 Bar可以使用super来访问它的父类 Foo 的方法。
* 但现实中: 子类是**拷貝**一份它从父类继承来的行为。(存在新的地方)
* 如果子类“覆盖”一个它继承的方法，原版的方法和覆盖版的方法实际上都是存在的，所以它们都是可以访问的。  

不要让多态把你搞糊涂，
Ｘ：子类是链接到父类上的(不是在父類存方法的地方得到方法)
Ｏ：子类得到一份它需要从父类继承的东西的拷贝 (把父類方法存到新地方，舊地方還是有東西)

所以...**类继承意味着拷贝**  

### 多重继承（Multiple Inheritance）
classed-based 可能發生的問題  
* 好處:多個功能  
* 壞處:可能衝突且複雜  

### 鑽石問題 ###
* 祖父: A:drive()
* 父類: B:drive()  C:drive()  
* 子類: D  B? or C?

![image](https://github.com/getify/You-Dont-Know-JS/blob/1ed-zh-CN/this%20%26%20object%20prototypes/fig2.png)

### 比較JS  
JS不提供多重继承機制

***
### 混合（Mixin）
##### JS- 原型練繼承
* 剛提到: 類繼承是拷貝  
* 在JS中，当你“继承”或是“实例化”时，JS **不会 自动地 执行拷贝行为**。  
* 因為: JavaScript 没有“类”可以拿来实例化，只有对Obj。  
* Obj也不会被拷贝到另一个Obj中，而是**链接在一起**（详见第五章）。  
* ＪＳ的方法: 模拟沒有类的拷贝行为 => mixins（混合）。  

### 两种“mixin”：明确的（explicit） 和 隐含的（implicit）

##### 明确的 Mixin（Explicit Mixins）  
建造一个工具来手动拷贝  
通常稱為extend，这里叫它 mixin(..)。  

```JS
// 大幅简化的手動工具 `mixin(..)` 示例：  取代類的自動拷貝功能
function mixin( Vehicle, Car) {
    for (var key in Vehicle) {
        // 仅拷贝不存在的属性
        if (!(key in Car)) {
           Car[key] =Vehicle[key];
        }
    }   //如果在 targetObj（在我们的例子中是 Car）中没有名称与之匹配的属性，它就进行拷贝
    return Car;
}
```
```JS
//  創建一個模板Vehicle (類 但其實是obj)
var Vehicle = {
    engines: 1,  // 子類Car 將 copy  value

    ignition: function() {          //子類Car 將 copy  reference  
        console.log( "啟動引擎" );
    },


    drive: function() {
        this.ignition();
        console.log( "往前開" );
    }
};


var Car = mixin( Vehicle, {
    wheels: 4,
    drive: function() {        // 同名故覆蓋vehicle drive()
        Vehicle.drive.call( this );  // 引用父類的drive    
        console.log( "轉動輪子 " + this.wheels + " 四輪的喔" );  覆
    }
} );
```
* 父類(obj)中的函数没有被复制，而是指向函数的**引用**被复制。  
* 因為子car 父vehicle都有drive()
O : Vehicle.drive.call( this )    
X : 若寫成 Vehicle.drive()  (沒有綁定在car上呼叫) 則引用後無法使用car環境中執行    

```
[Class-based]inherited:drive()。作者称之为“相对多态（relative polymorphism）”

[JS]Vehicle.drive.call( this )。作者将之称为“显式假想多态（explicit pseudo-polymorphism）”。
```


* JavaScript 没有能力实现相对多态（ES6 之前，见附录A）。
因为 Car 和 Vehicle 都有一个名为 drive() 的函数，为了在它们之间区别调用，  
* 必须使用**绝对（不是相对）引用**。
明确地用名称指出 Vehicle 对象，然后在它上面调用 drive() 函数。  

這裏只是為了演示需要，
**应当尽可能地避免使用显式假想多态（Vehicle.drive.call( this )）**

***

### 混合拷贝（Mixing Copies）

* 建立時就給car的內容

```
var Car = mixin( Vehicle, {
    wheels: 4,
    drive: function() {        // 同名故覆蓋vehicle drive()
        Vehicle.drive.call( this );  // 引用父類的drive
        console.log( "轉動輪子 " + this.wheels + " 四輪的喔" );  覆
    }
} );
```

* 建立時還沒給car的內容(“mixin”这个名称来自于解释這個方法：Car 混入 Vehicle 的内容 )
```
// 首先，创建一个空对象
// 将 Vehicle 的内容拷贝进去
var Car = mixin( Vehicle, { } );
```
```
// 现在拷贝 Car 的具体内容
mixin( {
	wheels: 4,

	drive: function() {
		// ...
	}
}, Car );
```
***
**不论哪种方法，我们都明确地将 Vehicle 中的非重叠内容拷贝到 Car 中。**  
**在 Car 上添加属性，它不会影响到 Vehicle，反之亦然。**  
***

##### BUT 拷贝完成后还能互相“影响”对方
比如它们共享一个共通对象（比如数组）的引用。  
拷貝的是位置不是值的就會受到影響

##### 結論：
1. 将一个属性定义两次相比 VS 将属性从一个对象拷贝到另一个对象?
并不会产生多少 实际的 好处
2. JS “多重继承”的行为可以被模擬出來，但不易維護，不會用不要用。
3. 在第六章中，我们将试着提取一种更简单的方法来实现我们期望的结果，同时免去这些周折。

***
### 寄生继承（Parasitic Inheritance）
明确的 mixin 模式的一个变种  
在某种意义上是明确的而在某种意义上是隐含的  
```
// “传统的 JS 类” `Vehicle`
function Vehicle() {
    this.engines = 1;
}
Vehicle.prototype.ignition = function() {
    console.log( "Turning on my engine." );
};
Vehicle.prototype.drive = function() {
    this.ignition();
    console.log( "Steering and moving forward!" );
};


// “寄生类” `Car`
function Car() {
    // 首先, `car` 是一个 `Vehicle`
    var car = new Vehicle();


    // 现在, 我们修改 `car` 使它特化
    car.wheels = 4;


    // 保存一个 `Vehicle::drive()` 的引用
    var vehDrive = car.drive;


    // 覆盖 `Vehicle::drive()`
    car.drive = function() {
        vehDrive.call( this );  //不直接用爸爸的位置，而是先把位置存在另個地方(vehDrive)
        console.log( "Rolling on all " + this.wheels + " wheels!" );
    };

    return car;
}

var myCar = new Car();   
//因為有return 就算不用new也會返回實例

myCar.drive();
// Turning on my engine.
// Steering and moving forward!
// Rolling on all 4 wheels!
```
***
### 隐含的 Mixin（Implicit Mixins）
```
var Something = {
    cool: function() {
        this.greeting = "Hello World";
        this.count = this.count ? this.count + 1 : 1;
    }
};


Something.cool();
Something.greeting; // "Hello World"
Something.count; // 1


var Another = {
    cool: function() {
        // 隐式地将 `Something` 混入 `Another`
        Something.cool.call( this );  this===Another
    }
};


Another.cool();
Another.greeting; // "Hello World"
Another.count; // 1 (不会和 `Something` 共享状态)

```

将 Something 的行为“混入”了 Another。
**应当尽量避免使用这种结构 以保持代码干净而且易于维护。**

### 結論
* 类意味着拷贝。  
* 当一个传统的类被实例化时，就发生了类的行为向实例中拷贝。
* 当类被继承时，也发生父类的行为向子类的拷贝。  
* 多态（在继承链的不同层级上拥有同名的不同函数）看起来是子类回到父类的相对引用链接，但是仍是拷贝行为的结果。   
* JavaScript 不会自动地 （像类那样）在对象间创建拷贝。  
* mixin 模式常用于在 某种程度上 模拟类的拷贝行为，但是这通常导致像显式假想多态那样（OtherObj.methodName.call(this, ...)）难看而且脆弱的语法，这样的语法又常导致更难懂和更难维护的代码。  
* 明确的 mixin 和类 拷贝 又不完全相同，因为物件（和函数！）仅仅是引用被复制，不是对象/函数自身被复制    
* 一般来讲，在 JS 中模拟类通常会比解决当前 真正 的问题埋下更多的坑。  
