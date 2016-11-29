JSON （JavaScript Object Notation）一种简单的数据格式，比xml更轻巧。 JSON 是 JavaScript 原生格式，这意味着在 JavaScript 中处理 JSON 数据不需要任何特殊的 API 或工具包。

JSON的规则很简单： 对象是一个无序的“‘名称/值'对”集合。一个对象以“{”（左括号）开始，“}”（右括号）结束。每个“名称”后跟一个“:”（冒号）；“‘名称/值' 对”之间使用“,”（逗号）分隔
```
var str = '{"name": "hanzichi", "age": 10}';
var obj = eval('(' + str + ')');
console.log(obj); // Object {name: "hanzichi", age: 10}
```
是否注意到，向 eval() 传参时，str 变量外裹了一层小括号？为什么要这样做？

我们先来看看 eval 函数的定义以及使用。

eval() 的参数是一个字符串。如果字符串表示了一个表达式，eval() 会对表达式求值。如果参数表示了一个或多个 JavaScript 声明， 那么 eval() 会执行声明。不要调用 eval() 来为算数表达式求值； JavaScript 会自动为算数表达式求值。

简单地说，eval 函数的参数是一个字符串，如果把字符串 "noString" 化处理，那么得到的将是正常的可以运行的 JavaScript 语句。

怎么说？举个栗子，如下代码：
```
var str = "alert('hello world')";
eval(str);
```
执行后弹出 "hello world"。我们把 str 变量 "noString" 化，粗暴点的做法就是去掉外面的引号，内部调整（转义等），然后就变成了：```alert('hello world')```

very good！这是正常的可以运行的 JavaScript 语句！运行之！
再回到开始的问题，为什么 JSON 字符串要裹上小括号。如果不加，是这个样子的：
```
var str = '{"name": "hanzichi", "age": 10}';
var obj = eval(str); // Uncaught SyntaxError: Unexpected token :
```
恩，报错了。为什么会报错？试试把 str "noString" 化，执行一下：
```
{"name": "hanzichi", "age": 10}; // Uncaught SyntaxError: Unexpected token :
```
毫无疑问，一个 JSON 对象或者说是一个对象根本就不是能执行的 JavaScript 语句！等等，试试以下代码：
```
var str = '{name: "hanzichi"}';
var obj = eval(str);
console.log(obj); // hanzichi
```
这又是什么鬼？但是给 name 加上 "" 又报错？
```
var str = '{"name": "hanzichi"}';
var obj = eval(str); // Uncaught SyntaxError: Unexpected token :
console.log(obj);
```
好吧，快晕了，其实还是可以将 str "nostring" 化，看看是不是能正确执行的 JavaScript 语句。前者的结果是：
```
{name: "hanzichi"}
```
这确实是一条合法的 JavaScript 语句。{} 我们不仅能在 if、for 语句等场景使用，甚至可以在任何时候，因为 ES6 之前 JavaScript 只有块级作用域，所以对于作用域什么的并不会有什么冲突。去掉 {} 后 name: "hanzichi" 也是合法的语句，一个 label 语句，label 语句在跳出嵌套的循环中非常好用，具体可以参考 label，而作为 label 语句的标记，name 是不能带引号的，标记能放在 JavaScript 代码的任何位置，用不到也没关系。

一旦一个对象有了两个 key，比如 {name: "hanzichi", age: 10}，ok，两个 label 语句？将 "hanzhichi" 以及 10 分别看做是语句，但是 语句之间只能用封号连接！（表达式之间才能用逗号）。所以改成下面这样也是没有问题的：
```
var str = '{name: "hanzichi"; age: 10}';
var obj = eval(str);
console.log(obj); // 10
```
越扯越远，文章开头代码的错误的原因是找到了，为什么套个括号就能解决呢？简单来说，() 会把语句转换成表达式，称为语句表达式。括号里的代码都会被转换为表达式求值并且返回，对象字面量必须作为表达式而存在。

本文并不会大谈表达式，关于表达式，可以参考文末链接。值得记住的一点是，表达式永远有一个返回值。大部分表达式会包裹在() 内，小括号内不能为空，如果有多个表达式，用逗号隔开，也就是所谓的逗号表达式，会返回最后一个的值。
