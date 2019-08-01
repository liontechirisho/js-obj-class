# You don't know JS
## 混合（淆）“類”的對象 class
***
## &sect; 引言
class概念並不是非常自然地映射到 JS 的物件機制上，  
許多 JavaScript 開發者為了克服這些挑戰所做的努力（mixins等）。  


1. 物件導向設計 Object-oriented programming OOP
https://zh.wikipedia.org/wiki/%E9%9D%A2%E5%90%91%E5%AF%B9%E8%B1%A1%E7%A8%8B%E5%BA%8F%E8%AE%BE%E8%AE%A1

2. CLASS 類

3. 類別的機制:“產生實體（instantiation）”, “繼承（inheritance）”與“（相對）多態(relative polymorphism）”。

4. JS 模擬類的努力




***
## &sect; 什麼是物件導向programming?

### Procedural programming
###          V.S
### Object-oriented programming (OOP)
***
![image](https://github.com/liontechirisho/js-obj-class/blob/master/img/procedural-vs-oop.jpg)

***
</br>
</br>

![image](https://github.com/liontechirisho/js-obj-class/blob/master/img/DATA%20MANAGEMENT%20IN%20PROCEDURAL%20AND%20OBJECT%20ORIENTED%20MODELS.png)
***


## &sect; OOP的三大特性: 封裝、繼承、多型

1. **資料封裝(Encapsulation)**
   資料封裝就是將資料分成私用(Private)、保護(Protected)、公用(Public)等，實踐 Information hiding 概念,   
   避免程式各個物件互相幹擾，降低程式的複雜度及維護上的困難度。  

2. **繼承(Inheritance)**  
  類=類別 ex.**載具與車子**  
  每一種不同類型的載具一次又一次地重定義“載人能力” ?  
  在 Vehicle 中把這個能力定義一次，  
  之後當我們定義 Car 時，指出它從基本的 Vehicle 定義中“繼承”（或“擴展”）。  
  次子類別的次子類別也可以繼承使用，最後即能達到資料重覆使用的目的。

3. **多型(Polymorphism)**  
   父類的method可以被子類覆蓋，
   透過實作多個繼承或介面來實現父類別，
   並使用Override或Overload來達成。



***

![image](https://github.com/liontechirisho/js-obj-class/blob/master/img/oop.png)

```
圖片來源: 小山的C#教學 https://www.youtube.com/watch?v=gpjAFBh3GJ4
```
***
## &sect; 什麼是Class?  

=> 模型/藍圖  


![image](https://github.com/liontechirisho/js-obj-class/blob/master/img/blueprints2.jpg)  
***
![image](https://github.com/liontechirisho/js-obj-class/blob/master/img/181017gn015.jpg)  
***

## &sect; 總結
### class
某些具有共同特性物件的集合
物件就是類別的實體。
### OOP
物件導向具有封裝、繼承、多型等特性，
原則上每個物件相互獨立且無關聯性
而物件導向程式設計就是依照物件的方法產生互動以完成要求。

***

## &sect; Class-based vs Prototype-based programming
* 皆為ＯＯＰ
* 主義差別在於繼承方式  

![image](https://github.com/liontechirisho/js-obj-class/blob/master/img/1_0jWIHlaV3zcjjniEOrovEQ.jpeg)  


### &para; class-based
1. 用Class **繼承** Class
2. 繼承 = 複製clone
3. Object是Class的實例
* 有哪些語言?  PHP, C++, Java, C#, and Objective-C....

```js
### class-based ###  
水果 class  
香蕉 class (extend fruit)  
製造出的每個香蕉  obj (clone banana 為class的實例)  
```

```js
延伸:https://en.wikipedia.org/wiki/Class-based_programming  
```

### &para; Prototype-based  (js)  
1. 用Object **繼承** Object (objects 會被拷貝但不包含fn, array等)  
![image](https://github.com/liontechirisho/js-obj-class/blob/master/img/js-allO%20(1).JPG)  

```js
### Prototype-based ###  
水果 object  
香蕉 object (prototype繼承)  
製造出的每個香蕉  object  
```

![image](https://github.com/liontechirisho/js-obj-class/blob/master/img/grasping_prototype_based_programming_by_stumbling_poncho_d4glx20-pre.jpg)


## &sect; 其實...JS裡面沒有典型的class  
* JS 擁有 一些 像類的語法元素（比如 new 和 instanceof）有一陣子了  
* ES6 中:有 class 關鍵字（見附錄A）。**但，是class 是一種語法糖**      
* 注意: 其他語言中遇到的 類 和在 JS 中模擬的“類”不同  
* 你可以選擇在 JavaScript 中使用或不使用類   

***

## &sect; 類的機制

### &para; 作用方式
* 由standard library提供"stack" 成為 Stackclass。  
* Stackclass 有個內部設計，儲存變數的資料DATA  
* 可以使用Public methods(類中定義好的)去存取data，使得開發者可以操作DATA  
* Stack長相
![image](https://github.com/liontechirisho/js-obj-class/blob/master/img/memory-layout-of-c-program-diagram-20170301-1024x962.png)  
   ```
瞭解更多
https://blog.gtwang.org/programming/memory-layout-of-c-program/   
```



### &para; 你不是直接在 Stack 上操作
* StackClass它本身不是一個“stack” 。
* 為了得到一個可以對之進行操作的實在的資料結構(data structure)
* **必須 產生實體 才真的有東西可以操作**

### &para; 從Class複製成為的實例
This object is a copy of all the characteristics described by the class.

**一個CLASS就是一個藍圖。**
一個類通過**拷貝clone**被產生實體為物件。

### &para; 拷貝操作圖
箭頭為拷貝方向  
![image](https://github.com/getify/You-Dont-Know-JS/blob/1ed-zh-CN/this%20%26%20object%20prototypes/fig1.png)

## &sect; 如何實例化class？
* 使用構造器（constructor）  
* 這個方法的名稱通常與類名相同  
* 此方法會初始化實例所需的所有資訊（狀態）  

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

Joe.showOff()   <---實例化Joe，可使用class制定且Joe 拷貝下來的方法
```

***

## &sect; Class Inheritance 類的繼承

對class-based 語言來說，
1. 可以定義一個類
2. 一個類可以繼承另一類(extend)
3. 第一個類被稱為“父類”，第二個類通常被稱為“子類”

###  &para; 類繼承

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
//兩個子類

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

* 兩種具體的載具：Car 和 SpeedBoat。繼承後特化。    
一輛車有4個輪子，一艘快艇有兩個引擎  
* inherited:drive() Car 可以引用它繼承的，原版 drive()。 (同時可以使用新的方法)  

## &sect; 多型

這種技術稱為“多型（polymorphism）”，  
**多型: 任何方法都可以引用位於繼承層級上更高一層的其他（同名或不同名的）方法。**

或稱“虛擬多型（virtual polymorphism）”。  
作者稱之**相對多型（relative polymorphism）** :根據你引用的實例是哪個類（class or Vehicle）而 多型（改變）。

```
BMW =  new Car();
BMW.drive()
// 啟動引擎  往前開 ----class Vehicle 定義的方法 位於繼承層級上更高一層
// 轉動輪子 4 四輪的喔 -----class Car 定義的方法
```

## &sect; 與JS的差別
class-based語言通過 super，從子類的構造器中直接訪問父類構造器。(構造器在class中)
* 在 JS 中，這是相反的 —— **class 在構造器中（Foo.prototype... 類型引用）**。  
* 父子關係僅存在於它們各自的構造器的兩個.prototype物件間
* JS的構造器本身不直接關聯
* 沒有簡單的方法從一個中相對參照另一個（參見附錄A，看看 ES6 中用 super “解決”此問題的 class）。

```
水果 object   
香蕉 obj (clone 水果 構造器 在prototype中)  
製造出的每個香蕉  obj (clone 香蕉 構造器 在prototype中)
```

## &sect; 類繼承 = 拷貝
* super: 讓你可以使用繼承的class的方法   
* 理論上: 子類 Bar可以使用super來訪問它的父類 Foo 的方法。
* 但現實上: 子類是**拷貝**一份它從父類繼承來的行為。(存在新的地方)
* 如果子類“覆蓋”一個它繼承的方法，原版的方法和覆蓋版的方法實際上都是存在的，所以它們都是可以訪問的。  

**不要讓多型把你搞糊塗**  
Ｘ：子類是連結到父類上的(不是在父類存方法的地方得到方法)  
Ｏ：子類得到一份它需要從父類繼承的東西的拷貝   
(把父類方法存到新地方，舊地方還是有東西)

所以...**類繼承=拷貝**  

## &sect; 多重繼承（Multiple Inheritance）
###  &para; classed-based 可以多重繼承
* 好處:多個功能  
* 壞處:可能衝突且複雜  
==> 產生鑽石問題

### &para; 鑽石問題
* 祖父: A:drive()
* 父類: B:drive()  C:drive()  
* 子類: D:B? or C?

![image](https://github.com/getify/You-Dont-Know-JS/blob/1ed-zh-CN/this%20%26%20object%20prototypes/fig2.png)

## &sect; 比較JS  
JS不提供多重繼承機制

***
## &sect; 混合（Mixin）
### &para; [JS]- 原型鍊繼承
* 剛提到: 類繼承是拷貝  
* 在JS中，當你“繼承”或是“產生實體”時，JS **不會 自動地 執行拷貝行為**。  
* 因為: JavaScript 沒有“類”可以拿來產生實體，只有Obj。  
* Obj也不會被拷貝到另一個Obj中，而是**連結在一起**（詳見第五章）。  
* ＪＳ的方法: 模擬沒有類的拷貝行為 => mixins（混合）。  

## &sect; 兩種“mixin”：明確/隱含

### &para; 明確的 Mixin（Explicit Mixins）  
* 建造一個工具來手動拷貝  
* 通常稱為extend，這裡叫它 mixin(..)。  

```JS
// 大幅簡化的手動工具 `mixin(..)` 示例：  取代類的自動拷貝功能
function mixin( Vehicle, Car) {
    for (var key in Vehicle) {
        // 僅拷貝不存在的屬性
        if (!(key in Car)) {
           Car[key] =Vehicle[key];
        }
    }   //如果在 targetObj（在我們的例子中是 Car）中沒有名稱與之匹配的屬性，它就進行拷貝
    return Car;
}
```
```JS
//  創建一個範本Vehicle (模擬類 但其實是obj)
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
* 父類(obj)中的函數沒有被複製，而是函數的**位址**被複製。  
* 因為子car 父vehicle都有drive()  
O : Vehicle.drive.call( this )      
X : 若寫成 Vehicle.drive()  (沒有綁定在car上呼叫) 則引用後無法使用car環境中執行    

```
[JS]Vehicle.drive.call( this )。作者將之稱為“顯式假想多態（explicit pseudo-polymorphism）”。

[Class-based]inherited:drive()。作者稱之為“相對多態（relative polymorphism）”
```


* JavaScript 沒有能力實現相對多態（ES6 之前，見附錄A）。
因為 Car 和 Vehicle 都有一個名為 drive() 的函數，為了在它們之間區別調用，  
* 必須使用**絕對（不是相對）引用**。
明確地用名稱指出 Vehicle 物件，然後在它上面調用 drive() 函數。  

這裏只是為了演示需要，
**應當盡可能地避免使用顯式假想多態（Vehicle.drive.call( this )）**

***

## &sect; 混合拷貝（Mixing Copies）

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

* 建立時還沒給car的內容(“mixin”這個名稱來自於解釋這個方法：Car 混入 Vehicle 的內容 )
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
***
**不論哪種方法，我們都明確地將 Vehicle 中的非重疊內容拷貝到 Car 中。**  
**在 Car 上添加屬性，它不會影響到 Vehicle，反之亦然。**  
***

### &para; BUT!! 拷貝完成後還能互相“影響”對方
比如它們共用一個共通物件（比如陣列）的引用。  
拷貝的是位置不是值的就會受到影響

## &sect; 結論：
1. 將一個屬性定義兩次相比 V.S 將屬性從一個物件拷貝到另一個物件?  
=>並不會產生多少 實際的 好處。
2. JS “多重繼承”的行為可以被模擬出來，但不易維護，不會更複雜才考慮用。
3. 第六章中，將揭示更簡單的方法。

***
## &sect; 寄生繼承（Parasitic Inheritance）
明確的 mixin 模式的一個變種  
在某種意義上是明確的，而在某種意義上是隱含的  
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
## &sect; 隱含的 Mixin（Implicit Mixins）
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

將 Something 的行為“混入”了 Another。  
**應當儘量避免使用這種結構，以保持代碼乾淨而且易於維護。**
***
## &sect; 結論
* 類意味著拷貝。  
* 傳統的類產生實體，就發生了類向實例拷貝。
* 當類被繼承時，也發生父類的行為向子類的拷貝。  
* 多型（在繼承鏈的不同層級上擁有同名的不同函數）不是子類回到父類方法，而是拷貝的結果。   
* JavaScript **不會** 自動地 （像類那樣）在物件間創建拷貝。  
* mixin 模式常用於在 某種程度上 類比類的拷貝行為，但是這通常導致像顯式假想多態那樣（OtherObj.methodName.call(this, ...)）難看而且脆弱的語法，這樣的語法又常導致更難懂和更難維護的代碼。  
* 明確的 mixin 和類 拷貝 不同，因為物件（和函數！）僅僅是引用被複製，不是物件/函數自身被複製    
* 一般來講，在 JS 中模擬類可能埋下更多的坑。  
