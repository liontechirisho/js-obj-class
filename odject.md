# You don't know JS
## Object 對象
***
##### 兩種建立方式

1.宣告
```js
var myObj = {
    key: value
    // ...
};
```
2.建構　(要一一給予屬性)
```js
var myObj = new Object();
myObj.key = value;
```

##### 類型(同之前章節所述)
* string 簡單基本類型
* number 簡單基本類型
* boolean 簡單基本類型
* null    是自己的基本類型  但typeof null 為object
* undefined  簡單基本類型
* object-----自己是一個類型
###### 複雜基本類型:
* object 的子類型Function :可調用，可像普通物件般處理
++++++加 克服 JS 的奇怪部分的截圖
* object 的子類型Array
***
##### 內建物件/對象=== 內建的函數(可new)/有對應的方法和屬性
* String
* Number
* Boolean
* Object
* Function
* Array
* Date
* RegExp
* Error
***
**思考**  
物件 = key-value pairs  
v.s  
一個常見的錯誤論斷是“JavaScript中的一切都是物件"
***
##### 基本類型值 vs  內建物件/對象(子類型)
```js
//基本類型值
var strPrimitive = "I am a string";  
typeof strPrimitive;							// "string"
strPrimitive instanceof String;					// false
// "I am a string" 是一個基本型值，非物件

//內建物建
var strObject = new String( "I am a string" );  
typeof strObject; 								// "object"
strObject instanceof String;					// true

```
JS會強制轉型為sting物件(自己默默用toString幫你)，   
故可以使用string的屬性如length↓↓↓↓↓
```js
var strPrimitive = "I am a string";

console.log( strPrimitive.length );			// 13

console.log( strPrimitive.charAt( 3 ) );	// "m"
```
強烈推薦用字面型值操作即可，不需要特別new

##### 各子類型狀況
* String  JS會強制轉型，建議用字面形式寫
* Number JS會強制轉型，建議用字面形式寫
* Boolean JS會強制轉型，建議用字面形式寫     
--------------------------------------------------->
* null    僅有字面形式，沒有object
* undefined  僅有字面形式，沒有object
* Date    僅有object，沒有字面形式
--------------------------------------------------->
* Object  不管寫字面還是構造建立，都是object
* Function 不管寫字面還是構造建立，都是object
* Array  不管寫字面還是構造建立，都是object
* RegExp  不管寫字面還是構造建立，都是object
--------------------------------------------------->
* Error  -- 很少被手動創建，多拋出異常時自動創建

##### 訪問物件內容之方法

為了訪問myObject在位置a的值，我們需要使用。或[]操作符。兩者皆訪問相同位置
```js
var myObject = {
    a: 2
};
//稱 屬性訪問
myObject.a;        // 2

//稱 key訪問
myObject["a"];    // 2
```

如果不確定要訪問的是哪個屬性，就只能使用[裝變數]

```JS
作業三，因為不確定輸入的是哪個名稱
所以用[]取變數
//data.json
{
      "guaranteed": false,
      "date": "2018/07/19",
      "price": 67928,
      "availableVancancy": 91,
      "totalVacnacy": 451,
      "status": "截止"
  },
  {
      "certain": false,
      "date": "2017/08/26",
      "price": 909,
      "onsell": 87,
      "total": 497,
      "state": "報名"
  },
  //props
dataKeySetting: {
      // 保證出團
      guaranteed: props.options.dataKeySetting.guaranteed || "guaranteed",
      // 狀態
      status: props.options.dataKeySetting.status || "status",
      // 可賣團位
      available:
        props.options.dataKeySetting.available || "availableVancancy",
      // 團位
      total: props.options.dataKeySetting.total || "totalVacnacy",
      // 價格
      price: props.options.dataKeySetting.price || "price"
    },
//React
<div className="content">
  <span>
    可賣:{item[this.state.dataKeySetting.available]}
  </span>{" "}
  <span>團位:{item[this.state.dataKeySetting.total]}</span>
</div>

```
[  ]在ES6也可以用來計算屬姓名 ↓↓↓↓↓
```js
var prefix = "foo";

var myObject = {
    [prefix + "bar"]: "hello",
    [prefix + "baz"]: "world"
};

myObject["foobar"]; // hello
myObject["foobaz"]; // world
```
注意!      
屬性名會被存成**字串**   
如果是數字的話也會自動轉成字串
```js
var myObject = { };

myObject[true] = "foo";
myObject[3] = "bar";
myObject[myObject] = "baz";

myObject["true"];                // "foo"
myObject["3"];   －>數字被轉成字串// "bar"
myObject["[object Object]"];  －>物件被轉成字串 // "baz"
```
***
##### 屬性vs方法

每次你訪問一個物件的屬性都是一個屬性訪問，無論你得到什麼類型的值。  
如果你恰好從屬性訪問中得到一個函數，**不會魔法般地變成方法** 。
一個從屬性訪問得來的函數沒有任何特殊性

可能最安全的結論是，在JavaScript中，“函數”和“方法”是可以互換使用的。  

ME: 我不知道他為啥要特別講這個...
***
##### 不要亂玩Array的屬性
數組也是物件，所以雖然每個索引都是正整數，你可以在數組上添加屬性：  
添加非數字屬性（不論是使用. 還是[]操作符語法）不會改變數組的長度所報告的值。  
如果你試圖在一個數組上添加屬性，但是屬性名看起來像一個數字，那麼最終它會成為一個數字索引（也就是改變了數組的內容）：
```js
var myArray = [ "foo", 42, "bar" ];

myArray["3"] = "baz";  //屬性名看起來像一個數字

myArray.length;    // 4  //最終改變了數組的內容

myArray[3];        // "baz"
```
***
##### 複製物件 是一個大工程
```js
function anotherFunction() { /*..*/ }
var anotherArray = [];
var anotherObject = {
    c: true
};
var myObject = {
    a: 2,  //只有值是copy一個一樣的存到新的位置  若為物件則僅拷貝到地址(引用)
    b: anotherObject,    // 引用，不是拷貝!
    c: anotherArray,    // 又一个引用!
    d: anotherFunction
};
anotherArray.push( anotherObject, myObject );
```
1.淺拷貝
僅copy 數值和物件位址
可使用ES6  Object.assign(..)
```js
var newObj = Object.assign( {}, myObject );
newObj.a;                        // 2
newObj.b === anotherObject;        // true
newObj.c === anotherArray;        // true
newObj.d === anotherFunction;    // true
```
→想要不只拷貝物件位置?

2.深拷貝
物件拷貝-轉字串再轉回物件
```js
let noRepeat = JSON.parse(JSON.stringify(orderDay));
```
不適用 function 等json不支援的內容

***
##### 屬性描述符（Property Descriptors）

為何有這個東西？  
ES5之前，JavaScript語言沒有給出直接的方法，讓你的代碼可以考察或描述屬性性質間的區別，比如屬性是否為只讀(不可複寫)。   
在ES5改進了，    
所有的屬性都用屬性描述符（Property Descriptors）來描述。
```js
var myObject = {
    a: 2
};

Object.getOwnPropertyDescriptor( myObject, "a" );
// {
//    value: 2,
//    writable: true,
//    enumerable: true,
//    configurable: true
// }
```
a有值2外，它還包含另外三個性質：writable，enumerable，和configurable

可以用Object.defineProperty（..）來添加新屬性，或使用期望的性質來修改既存的屬性（如果它是configurable的！）
```js
var myObject = {};
Object.defineProperty( myObject, "a", {
    value: 2,
    writable: true,
    configurable: true,
    enumerable: true
} );

myObject.a; // 2
```

#### 三個性質說明
###### 1. 可寫性（Writable）
writable控制著你改變屬性值的能力。   
writable: false 表示不可再賦值   
再賦值結果↓↓↓↓↓↓   
嚴格模式：TypeError    
非嚴格模式：維持原值    
###### 2.可配置性（可配置的）
是否可以使用defineProperty（..）工具，修改它的描述符定義。   
configurable設置為false是一個單向操作，不可撤銷！
```js
var myObject = {
    a: 2
};
Object.defineProperty( myObject, "a", {
    value: 4,
    writable: true,
    configurable: false,    // 不可配置！
    enumerable: true
} );

myObject.a;                    // 4
myObject.a = 5;                //value可以被重新給
myObject.a;                    // 5

Object.defineProperty( myObject, "a", {    //但這個方法就不能用了
    value: 6,
    writable: true,
    configurable: true,
    enumerable: true
} ); // TypeError
```
configurable:false
阻止的另外一個事情是使用刪除操作符移除既存屬性的能力。
```js
var myObject = {
    a: 2
};

myObject.a;                // 2
delete myObject.a;
myObject.a;                // undefined   被成功刪掉了

Object.defineProperty( myObject, "a", {
    value: 2,
    writable: true,
    configurable: false,
    enumerable: true
} );
myObject.a;                // 2
delete myObject.a;
myObject.a;                // 2
```
###### 3.可枚舉性（Enumerable）

控制著一個屬性是否能在特定的物件的屬性枚舉操作中出現，比如for..in循環。   
設置為false將會阻止它出現在這樣的枚舉中，即使它依然完全是可以訪問的。   
所有一般默認設置是可枚舉的
***
##### 不可變性（不變性）
有時我們希望將屬性或對象（有意或無意地）設置為不可改變的，ES5用幾種不同的微妙方式，加入了對此功能的支持。    
**BUT所有方法都是"淺"不可變**，也就是數組內部資料鎖不到（似淺拷貝）    
它們僅影響對象和它的直屬屬性的性質，物件的內容任然保持可變。
```js
myImmutableObject.foo; // [1,2,3]
myImmutableObject.foo.push( 4 );
myImmutableObject.foo; // [1,2,3,4]
```
注意：在JS程序中創建完全不可動搖的對像是不那麼常見的。
作為一個普通的設計模式，如果你發現自己想要封印（封印）或凍結（freeze），那麼你可能想要退一步來重新考慮你的程序設計

###### 1.物件常量(Object Constant)
**防止值被修改**  
const 常量（不能被改變，不可修改它的描述符定義）
```js
var myObject = {};

Object.defineProperty( myObject, "FAVORITE_NUMBER", {
	value: 42,
	writable: false,
	configurable: false
} );
```
###### 2.防止擴展(Prevent Extensions)
**防止被添加新的屬性**   
可以使用Object.preventExtensions（..）
```js
var myObject = {
	a: 2
};

Object.preventExtensions( myObject );

myObject.b = 3;  //b為新屬性
myObject.b; // undefined  
→非strict mode 直接失敗
→ strict mode 跳 TypeError
```
###### 3.封印(Seal)
**使用Object.seal(..)  創建一個“封印”的Object**   
**1.不可增加新屬性  2.不可重新配置屬性**   
=Object.preventExtensions(..) + configurable:false
值可以變
```
[複習一下]
configurable:false
值可變/描述符不可變(false後就不可逆)|| delete失效
```
###### 4.凍結(Freeze)
**Object.freeze(..) 創建一個“凍結”的Object**
=封印+值也不可變(writable:false)

***
### 屬性訪問不是你以為的那麼簡單
##### 內建的[[Get]]操作--取得既存屬性

屬性訪問可以用.跟[ ]
```js
var myObject = {
	a: 2
};
myObject.a; // 2
```

以為是.，但其實背後是由[[Get]] 操作(有些像 [[Get]]() 函数调用)
1.檢查obj
2.尋找屬性名
3.返回值
若沒有找到
4.遍历 [[Prototype]]  查找原型練(第五章)
5.還是都沒有返回 undefined
```js
var myObject = {
	a: 2
};

myObject.b; // undefined
```

```js
var myObject = {
	a: undefined  //存一個undefined
};

myObject.a; // undefined   

myObject.b; // undefined
```
a.b好像得到一樣的但其實不一樣(但看不出來..)   
处理引用 myObject.a，处理 myObject.b 的操作要多做一些潜在的“工作”。
##### 內建的[[Put]]操作--設定既存屬性或新增屬性值
1. 有setters 優先使用setters
这个属性是访问器描述符吗（见下一节"Getters 与 Setters"）？如果是，而且是 setter，就调用 setter。
2. writable:false 則不可更改值，故不可使用put
这个属性是 設為writable:false?若是→非strict mode 直接失敗//
→ strict mode 跳 TypeError
3. 否则，像平常一样设置既存属性的值。

##### Getters 与 Setters
ES5 引入了一个方法来覆盖这些默认操作的一部分，但不是在对象级别而是针对每个属性
Getter 调用一个隐藏函数来**取得**值的属性
Setter 调用一个隐藏函数来**设置**值的属性。
**属性不必非要包含值 —— 它们也可以是带有 getter/setter 的“访问器属性”**
若一属性定义为拥有 getter 或 setter 或两者兼备，那么它就成为“访问器描述符”:
访问器描述符: value 和 writable，被取代成 JS 将会考虑属性的 set 和 get 性质（还有 configurable 和 enumerable）。


```js
var myObject = {
	// 为 `a` 定义一个 getter
	get a() {
		return 2;
	}
};

Object.defineProperty(
	myObject,	// 目标对象
	"b",		// 属性名   myObject中的b屬性
	{			// 描述符
		// 为 `b` 定义 getter
		get: function(){ return this.a * 2 },

		// 确保 `b` 作为对象属性出现
		enumerable: true  //可枚舉性
	}
);

myObject.a; // 2

myObject.b; // 4
```

證明b沒有實際的值，但可以利用getter 的設置
讓我們訪問這個屬性時仍然可以取得一個值

```js
var myObject = {
	// 为 `a` 定义 getter
	get a() {
		return 2;
	}
};

myObject.a = 3;  賦值是沒有用的!

myObject.a; // 2
```
有setter才可賦值
```js
var myObject = {
	// 为 `a` 定义 getter
	get a() {
		return this._a_;
	},

	// 为 `a` 定义 setter
	set a(val) {
		this._a_ = val * 2;
	}
};

myObject.a = 2;   //傳到set a(val)

myObject.a; // 4
```
***
##### 存在性（Existence）

思考剛剛的問題:   
如何辨別屬性不存在的undefined v.s 存著undefined 值的屬性?   

=>查詢一個物件是否擁有該屬性名(而不存取值)   
* **屬性名是否存在**   
>兩個方法   
> * in  - 連[[prototype]]一起查
> * hasOwnProperty - 只查該物件    

```js
var myObject = {
	a: 2
};

("a" in myObject);				// true
("b" in myObject);				// false

myObject.hasOwnProperty( "a" );	// true
myObject.hasOwnProperty( "b" );	// false
```

* **屬性是否可遍歷**
> * .propertyIsEnumerable(..) - 屬性名是否存該物件中    
> * Object.keys(..)  - 返回一个所有可枚举属性的数组       
> * Object.getOwnPropertyNames(..) - 返回一个 所有 属性的数组，不论能不能枚举。   
>Object.keys(..)   
Object.getOwnPropertyNames(..)   
兩者都只能查該物件不查原型鍊，要做的話要自己寫迴圈查每一層的keys    


```js
var myObject = { };

Object.defineProperty(
	myObject,
	"a",
	// 使 `a` 可枚举，如一般情况
	{ enumerable: true, value: 2 }
);

Object.defineProperty(
	myObject,
	"b",
	// 使 `b` 不可枚举
	{ enumerable: false, value: 3 }
);

myObject.propertyIsEnumerable( "a" ); // true
myObject.propertyIsEnumerable( "b" ); // false

Object.keys( myObject ); // ["a"]
Object.getOwnPropertyNames( myObject ); // ["a", "b"]
```
### 迭代（Iteration）
***
可以使用 ES6 的 for..of 语法，在数据结构（数组，对象等）中迭代 值，for..of它寻找一个内建或自定义的 @@iterator 对象，这个对象由一个 next() 方法组成，通过这个 next() 方法每次迭代一个数据。  
```js
var myArray = [ 1, 2, 3 ];

for (var v of myArray) {
	console.log( v );
}
// 1
// 2
// 3
```

Array 拥有内建的 @@iterator    
@@iterator 本身 不是迭代器对象， 而是一个返回迭代器对象的 方法
```js
var myArray = [ 1, 2, 3 ];
var it = myArray[Symbol.iterator]();

it.next(); // { value:1, done:false }
it.next(); // { value:2, done:false }
it.next(); // { value:3, done:false }
it.next(); // { done:true }
```
迭代器的 next() 调用的返回值是一个 { value: .. , done: .. } 形式的对象，其中 value 是当前迭代的值，而 done 是一个 boolean

其他沒有內建@@iterator者，還是可以自己定義next( )
```js
var myObject = {
	a: 2,
	b: 3
};

Object.defineProperty( myObject, Symbol.iterator, {
	enumerable: false,           //Symbol.iterator 計算型屬性名
	writable: false,
	configurable: true,
	value: function() {
		var o = this;
		var idx = 0;
		var ks = Object.keys( o );
		return {
			next: function() {
				return {
					value: o[ks[idx++]],
					done: (idx > ks.length)
				};
			}
		};
	}
} );

// 手动迭代 `myObject`
var it = myObject[Symbol.iterator]();
it.next(); // { value:2, done:false }
it.next(); // { value:3, done:false }
it.next(); // { value:undefined, done:true }

// 用 `for..of` 迭代 `myObject`
for (var v of myObject) {
	console.log( v );
}
// 2
// 3
```

迭代对象属性的顺序是**不确定**的，而且可能会因 JS 引擎的不同而不同。对于需要跨平台环境保持一致的问题，**不要依赖** 观察到的顺序，因为这个顺序是不可靠的。