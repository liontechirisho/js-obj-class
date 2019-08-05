# You don't know JS

## 混合（淆）“類”的對象 class

---

### 引言

class 概念並不是非常自然地映射到 JS 的物件機制上，許多 JavaScript 開發者為了克服這些挑戰所做的努力（mixins 等）。
(Me: 畢竟是後來的語言要吸引大家使用)

1. 物件導向設計
   <a src='https://zh.wikipedia.org/wiki/%E9%9D%A2%E5%90%91%E5%AF%B9%E8%B1%A1%E7%A8%8B%E5%BA%8F%E8%AE%BE%E8%AE%A1'>
   Object-oriented programming OOP
   </a>

2. CLASS 類別

3. 類別的機制:“產生實體（instantiation）”, “繼承（inheritance）”與“（相對）多態(relative polymorphism）”。

### Class 類理論

強調資料和操作它的行為之間有固有的聯繫

什麼是物件=> 模型/藍圖

![image](https://github.com/liontechirisho/js-obj-class/blob/master/img/blueprints2.jpg)

![image](https://github.com/liontechirisho/js-obj-class/blob/master/img/181017gn015.jpg)

小山

![image](https://github.com/liontechirisho/js-obj-class/blob/master/img/oop.png)

https://www.youtube.com/watch?v=gpjAFBh3GJ4

### OOP 的三大特性: 封裝、繼承、多型

1. **資料封裝(Encapsulation)**

```
表示一個單詞或短語的一系列字元通常稱為“string（字串）”。
這些字元就是資料。
你總是想對資料 做事情， 所以可以 向 資料實施的行為
（計算它的長度，在末尾添加資料，檢索，等等）
都被設計成為 String 類的方法。
```

**任何給定的字串都是這個類的一個實例**

資料封裝就是將資料分成私用(Private)、保護(Protected)、公用(Public)等，實踐 Information hiding 概念, 避免程式各個物件互相幹擾，降低程式的複雜度及維護上的困難度。

2. **繼承(Inheritance)**

##### 類=類別

**載具與車子**
每一種不同類型的載具一次又一次地重定義“載人能力”這個基本性質可能沒有道理。
反而，我們在 Vehicle 中把這個能力定義一次，之後當我們定義 Car 時，
我們簡單地指出它從基本的 Vehicle 定義中“繼承”（或“擴展”）。
有繼承的關係後，父類別 (Super class) 中的資料 (Data) 或方法 (Method) 在次子類(Subclass)就可以繼承使用，次子類別的次子類別也可以繼承使用，最後即能達到資料重覆使用的目的。

3. **多型(Polymorphism)**  
   于父類的泛化行為可以被子類覆蓋，從而使它更加具體。實際上，相對多態允許我們在覆蓋行為中引用基礎行為。
   多型(Polymorphism) 代表能夠在執行階段，物件能夠依照不同情況變換資料型態，換句話說，多型是指一個物件參考可以在不同環境下，扮演不同角色的特性，指向不同的物件實體，可 透過實作多個繼承或介面來實現父類別，並使用 Override 或 Overload 來達成。

### 物件導向的編程

##### procedural programming VS OOP

![image](https://github.com/liontechirisho/js-obj-class/blob/master/img/DATA%20MANAGEMENT%20IN%20PROCEDURAL%20AND%20OBJECT%20ORIENTED%20MODELS.png)

![image](https://github.com/liontechirisho/js-obj-class/blob/master/img/procedural-vs-oop.jpg)

有些語言（比如 Java）不給你選擇，所以這根本沒什麼 選擇性 —— 一切都是類。
其他語言如 C/C++ 或 PHP 同時給你過程式和面向類的語法，在使用哪種風格合適或混合風格上，留給開發者更多選擇。

### 總結: 類的定義

而類別則較具抽象的概念，也就是某些具有共同特性物件的集合
換句話說，物件就是類別的實體。
物件導向具有封裝、繼承、多型等特性，原則上 每個物件相互獨立且無關聯性
而物件導向程式設計就是依照物件的方法產生互 動以完成要求。

### Class-based vs Prototype-based programming

皆為 OOP

![image](https://github.com/liontechirisho/js-obj-class/blob/master/img/1_0jWIHlaV3zcjjniEOrovEQ.jpeg)

##### class-based

Class-based programming, or more commonly class-orientation,  
is a style of Object-oriented programming (OOP)  
in which inheritance occurs via defining classes of objects, instead of inheritance occurring via the objects alone (compare prototype-based programming).

- 哪些?Others include PHP, C++, Java, C#, and Objective-C.

The most popular and developed model of OOP is a class-based model, instead of an object-based model.
The structure and behavior of an object are defined by a class,  
which is a definition, or blueprint, of all objects of a specific type.
An object must be explicitly created based on a class
and an object thus created is considered to be an instance of that class.
An object is similar to a structure, with the addition of method pointers, member access control,
and an implicit data member which locates instances of the class (i.e., objects of the class) in the class hierarchy (essential for runtime inheritance features).
https://en.wikipedia.org/wiki/Class-based_programming
皆是ＯＯＰ的一種
繼承 by class
object 是 class 的實例

##### Prototype-based (js 原型鍊運作方式)

![image](https://github.com/liontechirisho/js-obj-class/blob/master/img/grasping_prototype_based_programming_by_stumbling_poncho_d4glx20-pre.jpg)

Prototype-based programming is a style of object-oriented programming in which behaviour reuse (known as inheritance) is performed via a process of reusing **existing objects** via delegation that serve as prototypes. This model can also be known as prototypal, prototype-oriented, classless, or instance-based programming. Delegation is the language feature that supports prototype-based programming.
繼承一個 object
Prototype-based programming uses generalized objects,  
which can then be cloned and extended.  
Using fruit as an example,  
a "fruit" object would represent the properties and functionality of fruit in general.  
A "banana" object would be cloned from the "fruit" object and general properties specific to bananas would be appended.  
Each individual "banana" object would be cloned from the generic "banana" object.  
Compare to the class-based paradigm, where a "fruit" class would be extended by a "banana" class.
objects 會被拷貝跟 extend
水果 object
香蕉 obj (clone fruit)
製造出的每個香蕉 obj (clone banana)

class-based
水果 class
香蕉 class (extend fruit)
製造出的每個香蕉 obj (class 的實例)

The first prototype-oriented programming language was Self,

```
You must instantiate the Stack class
before you have a concrete data structure thing to operate against.
先實例化出一個物件
才有DATA給你操作
沒有存在class 的methods給你訪問DATA
```

### js 裡面沒有類

JS 擁有 一些 像類的語法元素（比如 new 和 instanceof）有一陣子了，而且在最近的 ES6 中，還有一些追加的東西，比如 class 關鍵字（見附錄 A）。

但這意味著 JavaScript 實際上 擁有 類嗎？簡單明瞭：沒有。
ES6 裡面確實有 class 但是一種語法糖  
實際上遲早要面對：你在其他語言中遇到的 類 和你在 JS 中模擬的“類”不同。

類是軟體設計中的一種可選模式， 你可以選擇在 JavaScript 中使用或不使用它

### 類機制

##### \* 作用方式

有 standard library 提供"stack" data structure 成為 Stackclass.
Stackclass 有個內部設計，儲存變數的資料 DATA
可以使用 Public methods(類中定義好的)去存取 data
使得開發者可以操作 DATA

Stack 長相
![image](https://github.com/liontechirisho/js-obj-class/blob/master/img/memory-layout-of-c-program-diagram-20170301-1024x962.png)

<a src="https://blog.gtwang.org/programming/memory-layout-of-c-program/">瞭解更多</a>

```
原文:
"standard library" provides a "stack" data structure (push, pop, etc.) as a Stackclass.
This class would have an internal set of variables that stores the data,
and it would have a set of publicly accessible behaviors ("methods") provided by the class,
which gives your code the ability to interact with the (hidden) data (adding & removing data, etc.).
```

##### 你不是直接在 Stack 上操作（StackClass)

它本身不是一個“stack”(data structure)。
為了得到一個可以對之進行操作的實在的資料結構，你必須 產生實體 這個 StackClass。

This object is a copy of all the characteristics described by the class.

**一個類就是一個藍圖。**
做出來你才能住或吃

一個類通過拷貝操作被產生實體為物件。

```
class-based
水果 class
香蕉 class (extend fruit)
製造出的每個香蕉  obj (class的實例)
```

拷貝操作圖

![image](https://github.com/getify/You-Dont-Know-JS/blob/1ed-zh-CN/this%20%26%20object%20prototypes/fig1.png)

### 如何實例化？

類的實例由類的一種特殊方法構建，這個方法的名稱通常與類名相同，稱為 “構造器（constructor）”。這個方法的具體工作，就是初始化實例所需的所有資訊（狀態）。

```
class CoolGuy {
    specialTrick = nothing

    CoolGuy( trick ) {   //我是構造器
        specialTrick = trick
    }

    showOff() {
        output( "Here's my trick: ", specialTrick )
    }
}
```

using class constructor:

```
Joe = new CoolGuy( "jumping rope" )

Joe.showOff()
```

### Class Inheritance 類繼承

面向類的語言中，你不僅可以定義一個能夠初始化它自己的類，你還可以定義另外一個類 繼承 自第一個類。  
第二個類通常被稱為“子類”，而第一個類被稱為“父類”。

##### 類繼承

```
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

class Car inherits Vehicle {
    wheels = 4

    drive() {
        inherited:drive()  // inherited = super  拷貝爸爸的方法過來
        output( "轉動輪子", wheels, " 四輪的喔!" )
    }
}

class SpeedBoat inherits Vehicle {
    engines = 2

    ignition() {
        output( "啟動引擎", engines, "是我獨門的引擎數！" )
    }

    pilot() {
        inherited:drive()  // inherited = super  拷貝爸爸的方法過來
        output( "看我輕功水上飄!" )
    }
}
```

兩種具體的載具：Car 和 SpeedBoat。它們都繼承 Vehicle 的泛化性質，  
但之後它們都對這些性質進行了恰當的特化。  
一輛車有 4 個輪子，一艘快艇有兩個引擎，意味著它需要在打火時需要特別注意要啟動兩個引擎

Car 定義了自己的 drive() 方法，它覆蓋了從 Vehicle 繼承來的同名方法。
但是，Car 的 drive() 方法調用了 inherited:drive()，  
這表示 Car 可以引用它繼承的，原版 drive()。 (同時可以使用新的方法)
SpeedBoat 的 pilot() 方法也引用了它繼承的 drive() 拷貝。

##### 多型

這種技術稱為“多型（polymorphism）”，或“虛擬多型（virtual polymorphism）”。  
對我們當前的情況更具體一些，我們稱之為“相對多態（relative polymorphism）”。
任何方法都可以引用位於繼承層級上更高一層的其他（同名或不同名的）方法。
obj Car can use class car's drive and Vehicle's drive

```
BMW =  new Car();
BMW.drive()
// 啟動引擎  往前開 ----class Vehicle 定義的方法 class car拷貝來的
// 轉動輪子 4 四輪的喔 -----class Car 定義的方法

```

ignition() 方法的定義，根據你引用的實例是哪個類（繼承層級）而 多態（改變）。

傳統面向類語言通過 super 給你的能力，是從子類的構造器中直接訪問父類構造器
然而在 JS 中，這是相反的 —— 實際上認為**“類”屬於構造器（Foo.prototype... 類型引用）更恰當**。  
因為在 JS 中，父子關係僅存在於它們各自的構造器的兩個.prototype 對象間，
構造器本身不直接關聯，而且沒有簡單的方法從一個中相對參照另一個（參見附錄 A，看看 ES6 中用 super “解決”此問題的 class）。

```
水果 object
香蕉 obj (clone 水果 構造器 在prototype中)
製造出的每個香蕉  obj (clone 香蕉 構造器 在prototype中)
```

### 多型帶來的盲點

類是繼承而來的，對這些類本身（不是由它們創建的物件！）有一個方法可以 相對地 引用它們繼承的物件，這個相對參照通常稱為 super。

從概念上講，看起來子類 Bar 可以使用相對多態引用（也就是 super）來訪問它的父類 Foo 的行為。  
然而在現實中，子類不過是被給與了一份它從父類繼承來的行為的拷貝而已。  
如果子類“覆蓋”一個它繼承的方法，原版的方法和覆蓋版的方法實際上都是存在的，所以它們都是可以訪問的。

不要讓多態把你搞糊塗，
Ｘ：子類是連結到父類上的
Ｏ：子類得到一份它需要從父類繼承的東西的拷貝
**類繼承意味著拷貝**

### 多重繼承（Multiple Inheritance）

classed-based 可能發生的問題

- 好處:多個功能
- 壞處:可能衝突且複雜

### 鑽石問題

- 子類“D”繼承自兩個父類（“B”和“C”），它們兩個又繼承自共通的父類“A”。
  如果“A”提供了方法 drive()，而“B”和“C”都覆蓋（多態地）了這個方法，
  那麼當“D”引用 drive() 時，它應當使用那個版本呢（B:drive() 還是 C:drive()）？

![image](https://github.com/getify/You-Dont-Know-JS/blob/1ed-zh-CN/this%20%26%20object%20prototypes/fig2.png)

我們在這裡將它們提出來，只是便於我們可以將它和 JavaScript 機制的工作方式比較。  
JavaScript 更簡單：它不為“多重繼承”提供原生機制。=> JS 不提供多重繼承 機制

---

### 混合（Mixin）

##### JS- 原型練繼承

當你“繼承”或是“產生實體”時，JavaScript 的物件機制**不會 自動地 執行拷貝行為**。  
很簡單，在 JavaScript 中沒有“類”可以拿來產生實體，只有物件。  
而且物件也不會被拷貝到另一個物件中，而是**連結在一起**（詳見第五章）。

其他語言中觀察到的類的行為意味著拷貝，  
ＪＳ用來類比 沒有類的拷貝行為：mixins（混合）。  
我們會看到兩種“mixin”：明確的（explicit） 和 隱含的（implicit）。

##### 明確的 Mixin（Explicit Mixins）

因為 JavaScript 不會自動地將行為從 Vehicle 拷貝到 Car，我們可以建造一個工具來手動拷貝。  
通常被稱為 extend，但為了便於說明，我們在這裡叫它 mixin(..)。

```JS
// 大幅簡化的手動工具 `mixin(..)` 示例：  取代類的自動拷貝功能
function mixin( Vehicle, Car) {
    for (var key in Vehicle) {
        // 僅拷貝不存在的屬性
        if (!(key in Car)) {
           Car[key] =Vehicle[key];
        }
    }

            //如果在 targetObj（在我們的例子中是 Car）中沒有名稱與之匹配的屬性，它就進行拷貝
    return Car;
}

//  創建一個範本Vehicle (類 但其實是obj)
var Vehicle = {
    engines: 1,  copy  value

    ignition: function() {   copy  reference
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

父類中的函數實際上沒有被複製，而是指向函數的 引用 被複製了。

所以，Car 現在有一個稱為 ignition 的屬性，它是一個 ignition() 函數**引用的拷貝**；而且它還有一個稱為 engines 的屬性，持有從 Vehicle 拷貝來的值 1

因為子 car 父 vehicle 都有 drive()，所以調用的時候要明確指出 Vehicle.drive.call( this )  
若寫成 Vehicle.drive() (沒有綁定在 car 上呼叫) 則引用後無法使用 car 環境中執行

```
Vehicle.drive.call( this )。我將之稱為“顯式假想多態（explicit pseudo-polymorphism）”。
inherited:drive()。我們稱之為“相對多態（relative polymorphism）”
```

JavaScript 沒有能力實現相對多態（ES6 之前，見附錄 A）。
因為 Car 和 Vehicle 都有一個名為 drive() 的函數，為了在它們之間區別調用，  
我們必須使用**絕對（不是相對）引用**。
明確地用名稱指出 Vehicle 物件，然後在它上面調用 drive() 函數。

這裏只是為了演示需要，
應當盡可能地避免使用顯式假想多態（Vehicle.drive.call( this )）

### 混合拷貝（Mixing Copies）

- 建立時就給 car 的內容

```
var Car = mixin( Vehicle, {
    wheels: 4,
    drive: function() {        // 同名故覆蓋vehicle drive()
        Vehicle.drive.call( this );  // 引用父類的drive
        console.log( "轉動輪子 " + this.wheels + " 四輪的喔" );  覆
    }
} );
```

- 建立時還沒給 car 的內容(“mixin”這個名稱來自於解釋這個方法：Car 混入 Vehicle 的內容 )

```
// 首先，創建一個空物件
// 將 Vehicle 的內容拷貝進去
var Car = mixin( Vehicle, { } );
```

```
// 現在拷貝 Car 的具體內容
mixin( {
    wheels: 4,

    drive: function() {
        // ...
    }
}, Car );
```

不論哪種方法，我們都明確地將 Vehicle 中的非重疊內容拷貝到 Car 中。  
在 Car 上添加屬性，它不會影響到 Vehicle，反之亦然。

BUT 拷貝完成後還能互相“影響”對方，比如它們共用一個共通物件（比如陣列）的引用。例如碰到直接複製引用的函式  
因為 JavaScript 函數不能真正意義上地（以標準，可靠的方式）被複製，  
所以你最終得到的是同一個函數的 被複製的引用。  
舉例來說，如果你在一個共用的函數物件（比如 ignition()）上添加屬性來修改它，
Vehicle 和 Car 都會通過這個共用的引用而受“影響”。

##### 結論：

將一個屬性定義兩次相比 VS 將屬性從一個物件拷貝到另一個物件並不會產生多少 實際的 好處  
如果你明確地將兩個或更多物件混入你的目標物件，你可以 某種程度上模擬 “多重繼承”的行為  
要小心的是，僅在明確的 mixin 能夠實際提高代碼可讀性時使用它，而如果你發現它使代碼變得更很難追溯，或在物件間建立了不必要或笨重的依賴性時，要避免使用這種模式。  
如果正確使用 mixin 使你的問題變得比以前 困難，那麼你可能應當停止使用 mixin。  
在第六章中，我們將試著提取一種更簡單的方法來實現我們期望的結果，同時免去這些周折。

### 寄生繼承（Parasitic Inheritance）

明確的 mixin 模式的一個變種，在某種意義上是明確的而在某種意義上是隱含的，稱為“寄生繼承（Parasitic Inheritance）”

```
// “傳統的 JS 類” `Vehicle`
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

// “寄生類” `Car`
function Car() {
    // 首先, `car` 是一個 `Vehicle`
    var car = new Vehicle();

    // 現在, 我們修改 `car` 使它特化
    car.wheels = 4;

    // 保存一個 `Vehicle::drive()` 的引用
    var vehDrive = car.drive;

    // 覆蓋 `Vehicle::drive()`
    car.drive = function() {
        vehDrive.call( this );
        console.log( "Rolling on all " + this.wheels + " wheels!" );
    };

    return car;
}
//我們一開始從“父類”（物件）Vehicle 製造了一個定義的拷貝，之後將我們的“子類”（物件）定義混入其中（按照需要保留父類的引用），最後將組合好的物件 car 作為子類實例傳遞出去。

var myCar = new Car();
//當我們調用 new Car() 時，一個新物件被創建並被 Car 的 this 所引用，但我們沒有使用這個物件，而是返回我們自己的 car 物件，因此，Car() 可以不用 new 關鍵字調用 :var myCar = Car();  myCar也會獲得一個Car()返回的實例

myCar.drive();
// Turning on my engine.
// Steering and moving forward!
// Rolling on all 4 wheels!
```

### 隱含的 Mixin（Implicit Mixins）

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
        // 隱式地將 `Something` 混入 `Another`
        Something.cool.call( this );  this===Another
    }
};

Another.cool();
Another.greeting; // "Hello World"
Another.count; // 1 (不會和 `Something` 共用狀態)

```

實質上“借用”了 Something.cool() 函數並在 Another 環境下 執行，說我們將 Something 的行為“混入”了 Another。
應當儘量避免使用這種結構 以保持代碼乾淨而且易於維護。

### 結論

類意味著拷貝。  
當一個傳統的類被產生實體時，就發生了類的行為向實例中拷貝。當類被繼承時，也發生父類的行為向子類的拷貝。  
多態（在繼承鏈的不同層級上擁有同名的不同函數）也許看起來意味著一個從子類回到父類的相對參照連結，但是它仍然只是拷貝行為的結果。  
JavaScript 不會自動地 （像類那樣）在物件間創建拷貝。  
mixin 模式常用於在 某種程度上 類比類的拷貝行為，但是這通常導致像顯式假想多態那樣（OtherObj.methodName.call(this, ...)）難看而且脆弱的語法，這樣的語法又常導致更難懂和更難維護的代碼。  
明確的 mixin 和類 拷貝 又不完全相同，因為物件（和函數！）僅僅是引用被複製，不是物件/函數自身被複製  
一般來講，在 JS 中模擬類通常會比解決當前 真正 的問題埋下更多的坑。
