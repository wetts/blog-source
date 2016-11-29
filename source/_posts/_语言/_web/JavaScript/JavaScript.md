# JavaScript #

---
## 目录 ##
##### 1. [如何在HTML中使用JavaScript](#1)
##### 2. [JavaScript中的注释](#2)
##### 3. [JavaScript中的变量](#3)
##### 4. [JavaScript中的数据类型](#4)
###### &nbsp;4.1 [Undefined和null](#4.1)
##### 5. [JavaScript中的函数](#5)
##### 6. [JavaScript中的比较符](#6)
##### 7. [JavaScript typeof](#7)
##### 8. [JavaScript 数据类型](#8)
##### 9. [JavaScript 类型转换](#9)
##### 10. [javascript:void(0) 含义](#10)
##### *附录：[注意事项](#ps)*
---

## <span id="1">在HTML中如何使用JS</span>
#### 1. 直接在代码中使用
> 在标签 &lt;script&gt;***JavaScript脚本***&lt;/script&gt; 中直接写

#### 2.外部JavaScript脚本
> &lt;script src=&quot;myScript.js&quot;&gt;&lt;/script&gt;

**提示：外部脚本不能包含 &lt;script&gt; 标签。**

---

## <span id="2">JavaScript中的注释</span>
#### 1. 单行注释
> 直接使用//进行单行注释

#### 2. 多行注释
> /* 注释内容 */

---

## <span id="3">JavaScript中的变量</span>
#### 1. 使用var关键字定义变量
> 该种方式可以定义全局变量也可以定义局部变量，这取决于定义变量的位置。在函数体中使用var关键字定义的变量为局部变量；在函数体外使用var关键字定义的变量为全局变量。
>> var flag = true; 

#### 2. 不使用var关键字定义变量
> 使用该方式定义的变量为全局变量，与位置无关
>> flag = true;

**提示：如果重新声明 JavaScript 变量，该变量的值不会丢失**
> 在以下两条语句执行后，变量 carname 的值依然是 "Volvo"：
>> var carname="Volvo";
var carname;

---

## <span id="4">JavaScript中的数据类型</span>
#### 1. 如何定义数组
>> var cars=new Array();
cars[0]="Audi";
cars[1]="BMW";
cars[2]="Volvo";

> 或者（condensed array）
>> var cars=new Array("Audi","BMW","Volvo");

> 或者（literal array）
>> var cars=["Audi","BMW","Volvo"];

#### 2. 如何定义对象
> var person={firstname:"Bill", lastname:"Gates", id:5566};

#### 3. 访问对象的属性和方法
> 访问对象属性的语法如下：
>> *objectName.propertyName*

> 方法对象方法的语法如下：
>> *objectName.methodName()*

---

## <span id="4.1">Undefined和null</span>
Undefined这个值表示变量不含有值。当声明的变量还未被初始化时，变量的默认值为undefined。
Undefined表示"缺少值"，就是此处应该有一个值，但是还没有定义。
> 1. 变量被声明了，但没有赋值时，就等于undefined。
2. 调用函数时，应该提供的参数没有提供，该参数等于undefined。
3. 对象没有赋值的属性，该属性的值为undefined。
4. 函数没有返回值时，默认返回undefined。

null用来表示尚未存在的对象，常用来表示函数企图返回一个不存在的对象。
> 1. 作为函数的参数，表示该函数的参数不是对象。
2. 作为对象原型链的终点。

---

## <span id="5">JavaScript中的函数</span>
#### 1. 定义函数
> funtion functionName(argument1, argument2 ...) {}

#### 2. 函数表达式
JavaScript 函数可以通过一个表达式定义。  
函数表达式可以存储在变量中：
> var x = function (a, b) {return a * b};  
> var z = x(4, 3);

以上函数实际上是一个 匿名函数 (函数没有名称)。  
函数存储在变量中，不需要函数名称，通常通过变量名来调用。

#### 3. Function() 构造函数
函数同样可以通过内置的 JavaScript 函数构造器（Function()）定义。
> var myFunction = new Function("a", "b", "return a * b");  
> var x = myFunction(4, 3);

#### 4. 自调用函数
函数表达式可以 "自调用"。  
自调用表达式会自动调用。  
如果表达式后面紧跟 () ，则会自动调用。  
不能自调用声明的函数。  
通过添加括号，来说明它是一个函数表达式：
> (function () {  
> var x = "Hello!!";      // 我将调用自己  
> })();

#### 5. JavaScript 函数参数
如果函数在调用时缺少参数，参数会默认设置为： undefined  

> ####Arguments 对象
> JavaScript 函数有个内置的对象 arguments 对象.
> argument 对象包含了函数调用的参数数组。
>> x = findMax(1, 123, 500, 115, 44, 88);  
>> function findMax() {   
>> var i, max = 0;  
>> for (i = 0; i < arguments.length; i++) {  
>> if (arguments[i] > max) {  
>> max = arguments[i];  
>> }}  
>> return max;}

##### 通过值传递参数  
在函数中调用的参数是函数的参数。  
如果函数修改参数的值，将不会修改参数的初始值（在函数外定义）。  
函数参数的改变不会影响函数外部的变量（局部变量）。

##### 通过对象传递参数
在JavaScript中，可以引用对象的值。  
因此我们在函数内部修改对象的属性就会修改其初始的值。  
修改对象属性可作用于函数外部（全局变量）。

---

## <span id="6">JavaScript中的比较符</span>
1. === 表示全等（值和类型），例如：  

> x=\==5 为 true；x==="5" 为 false

---

## <span id="7">JavaScript typeof</span>
你可以使用 typeof 操作符来检测变量的数据类型。
> typeof "John"                // 返回 string   
> typeof 3.14                  // 返回 number  
> typeof false                 // 返回 boolean  
> typeof [1,2,3,4]             // 返回 object  
> typeof {name:'John', age:34} // 返回 object  

## <span id="8">JavaScript 数据类型</span>
在 JavaScript 中有 5 中不同的数据类型：

- string
- number
- boolean
- object
- function

3 种对象类型：

- Object
- Date
- Array

2 个不包含任何值的数据类型：

- null
- undefined

**注意：**

- NaN 的数据类型是 number
- 数组(Array)的数据类型是 object
- 日期(Date)的数据类型为 object
- null 的数据类型是 object
- 未定义变量的数据类型为 undefined

#### constructor 属性
constructor 属性返回所有 JavaScript 变量的构造函数。
> "John".constructor                 // 返回函数 String()  { [native code] }  
> (3.14).constructor                 // 返回函数 Number()  { [native code] }  
> false.constructor                  // 返回函数 Boolean() { [native code] }  
> [1,2,3,4].constructor              // 返回函数 Array()   { [native code] }  
> {name:'John', age:34}.constructor  // 返回函数 Object()  { [native code] }  
> new Date().constructor             // 返回函数 Date()    { [native code] }  
> function () {}.constructor         // 返回函数 Function(){ [native code] }

## <span id="9">JavaScript 类型转换</span>
JavaScript 变量可以转换为新变量或其他数据类型：

- 通过使用 JavaScript 函数
- 通过 JavaScript 自身自动转换  

#### 将数字转换为字符串
全局方法 String() 可以将数字转换为字符串。
> String(123)

Number 方法 toString() 也是有同样的效果。
> (123).toString()

#### 将字符串转换为数字
全局方法 Number() 可以将字符串转换为数字。  
空字符串转换为 0
其他的字符串会转换为 NaN (不是个数字)。
> Number("3.14")    // 返回 3.14

#### 一元运算符 +
Operator + 可用于将变量转换为数字：
> var y = "5";      // y 是一个字符串  
> var x = + y;      // x 是一个数字

如果变量不能转换，它仍然会是一个数字，但值为 NaN (不是一个数字):
> var y = "John";   // y 是一个字符串  
> var x = + y;      // x 是一个数字 (NaN)

#### 将布尔值转换为数字
全局方法 Number() 可将布尔值转换为数字。
> Number(false)     // 返回 0  
> Number(true)      // 返回 1

#### 将日期转换为数字
全局方法 Number() 可将日期转换为数字。
> d = new Date();  
> Number(d)          // 返回 1404568027739

日期方法 getTime() 也有相同的效果。
> d = new Date();
> d.getTime()        // 返回 1404568027739

#### 自动转换类型 Type Conversion
当 JavaScript 尝试操作一个 "错误" 的数据类型时，会自动转换为 "正确" 的数据类型。  
以下输出结果不是你所期望的：
> 5 + null    // 返回 5         because null is converted to 0  
> "5" + null  // 返回"5null"   because null is converted to "null"  
> "5" + 1     // 返回 "51"      because 1 is converted to "1"  
> "5" - 1     // 返回 4         because "5" is converted to 5

#### 自动转换为字符串
当你尝试输出一个对象或一个变量时 JavaScript 会自动调用变量的 toString() 方法：
> document.getElementById("demo").innerHTML = myVar;  
> // if myVar = {name:"Fjohn"}  // toString 转换为 "[object Object]"  
> // if myVar = [1,2,3,4]       // toString 转换为 "1,2,3,4"  
> // if myVar = new Date()      // toString 转换为 "Fri Jul 18 2014 09:08:55 GMT+0200"

数字和布尔值也经常相互转换：
> // if myVar = 123             // toString 转换为 "123"  
> // if myVar = true            // toString 转换为 "true"  
> // if myVar = false           // toString 转换为 "false"

## <span id="10">javascript:void(0) 含义</span>
javascript:void(0) 中最关键的是 void 关键字， void 是 JavaScript 中非常重要的关键字，该操作符指定要计算一个表达式但是不返回值。

#### href="#"与href="javascript:void(0)"的区别 
\# 包含了一个位置信息，默认的锚是#top 也就是网页的上端。  
而javascript:void(0), 仅仅表示一个死链接。  
在页面很长的时候会使用 # 来定位页面的具体位置，格式为：# + id。  
如果你要定义一个死链接请使用 javascript:void(0) 。

---

## <span id="ps">注意事项</span>
1. 在 JavaScript 中，很多时候，你需要避免使用 new 关键字。