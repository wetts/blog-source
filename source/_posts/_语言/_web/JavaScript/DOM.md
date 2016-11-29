# DOM
---
## 目录
#### 1. [什么是DOM](#1)
#### 2. [DOM的分类](#2)
#### 3. [DOM节点](#3)
##### &nbsp;3.1 [节点类型](#3.1)
##### &nbsp;3.2 [节点类型 - 返回值](#3.2)
##### &nbsp;3.3 [节点类型 - 命名常量](#3.3)
#### 4. [XML DOM](#4)
##### &nbsp;4.1 [XML解析器](#4.1)
##### &nbsp;4.2 [加载XML文档](#4.2)
##### &nbsp;4.3 [加载XML字符串](#4.3)
##### &nbsp;4.4 [XML DOM属性](#4.4)
##### &nbsp;4.5 [XML DOM方法](#4.5)
##### &nbsp;4.6 [XML DOM操作实例](#4.6)
##### &nbsp;4.7 [访问节点](#4.7)
##### &nbsp;4.8 [DOM节点列表](#4.8)
##### &nbsp;4.9 [DOM 属性列表（命名节点图 Named Node Map）](#4.9)
##### &nbsp;4.10 [导航DOM节点](#4.10)
##### &nbsp;4.11 [访问节点的值](#4.11)
##### &nbsp;4.12 [改变节点的值](#4.12)
##### &nbsp;4.13 [删除节点](#4.13)
##### &nbsp;4.14 [替换节点](#4.14)
##### &nbsp;4.15 [创建节点](#4.15)
##### &nbsp;4.16 [添加节点](#4.16)
##### &nbsp;4.17 [克隆节点](#4.17)
##### &nbsp;4.18 [The XMLHttpRequest对象](#4.18)
##### &nbsp;ps [XML DOM注意事项](#xmlps)
#### 5. [DOM中的对象](#5)
##### &nbsp;5.1 [Node对象](#5.1)
##### &nbsp;5.2 [NodeList对象](#5.2)
##### &nbsp;5.3 [NamedNodeMap对象](#5.3)
##### &nbsp;5.4 [Document对象](#5.4)
##### &nbsp;5.5 [DocumentImpl对象](#5.5)
##### &nbsp;5.6 [DocumentType对象](#5.6)
##### &nbsp;5.7 [ProcessingInst对象](#5.7)
##### &nbsp;5.8 [Element对象](#5.8)
##### &nbsp;5.9 [Attribute对象](#5.9)
##### &nbsp;5.10 [Text对象](#5.10)
##### &nbsp;5.11 [CDATA对象](#5.11)
##### &nbsp;5.12 [Comment对象](#5.12)
##### &nbsp;5.13 [XMLHttpRequest对象](#5.13)
##### &nbsp;5.14 [ParseError Obj对象](#5.14)
#### 6. [HTML DOM](#6)
##### &nbsp;6.1 [HTML DOM方法](#6.1)
##### &nbsp;6.2 [HTML DOM属性](#6.2)
##### &nbsp;6.3 [HTML DOM访问](#6.3)
##### &nbsp;6.4 [HTML DOM修改](#6.4)
##### &nbsp;6.5 [HTML DOM事件](#6.5)
##### &nbsp;6.6 [HTML DOM根节点](#6.6)
#### 7. [浏览器差异](#7)
##### &nbsp;7.1 [空白与换行](#7.1)
#### 8. [JQuery DOM](#8)
---
## <span id="1">什么是DOM</span>
DOM是Document Object Model(文本对象模型)的缩写  
DOM是W3C的标准  
DOM定义了访问HTML和XML文档的标准
> "W3C 文档对象模型 （DOM） 是中立于平台和语言的接口，它允许程序和脚本动态地访问和更新文档的内容、结构和样式。"

---
## <span id="2">DOM的分类</span>
W3C DOM 标准被分为 3 个不同的部分：

- 核心 DOM - 针对任何结构化文档的标准模型
- XML DOM - 针对 XML 文档的标准模型
- HTML DOM - 针对 HTML 文档的标准模型

## <span id="3">DOM节点</span>
根据 W3C 的 HTML DOM 标准，HTML 文档中的所有内容都是节点：

- 整个文档是一个文档节点
- 每个 XML 元素是元素节点
- XML 元素内的文本是文本节点
- 每个 XML 属性是属性节点
- 注释是注释节点

#### 1. <span id="3.1">节点类型</span>
| 节点类型        | 描述           | 子类  |
| ------------- |:-------------:| -----:|
| Document      | 代表整个文档（DOM 树的根节点） | Element (max. one), ProcessingInstruction, Comment, DocumentType |
| DocumentFragment     | 代表"轻量级"的 Document 对象，它可以保留文档中的一部分      |   Element, ProcessingInstruction, Comment, Text, CDATASection, Entity参考手册 |
| DocumentType | 为文档中定义的实体提供了一个接口      |    None |
| ProcessingInstruction | 代表一个处理指令      |    None |
| EntityReference | 代表一个实体引用      |    Element, ProcessingInstruction, Comment, Text, CDATASection, EntityReference |
| Element | 表示一个元素      |    Element, Text, Comment, ProcessingInstruction, CDATASection, EntityReference |
| Attr | 代表一个属性      |    Text, EntityReference |
| Text | 代表元素或属性的文本内容      |    None |
| CDATASection | 代表文档中的 CDATA 区段（文本不会被解析器解析）      |    None |
| Comment | 代表一个注释      |    None |
| Entity | 代表一个实体      |    Element, ProcessingInstruction, Comment, Text, CDATASection, EntityReference |
| Notation | 定义一个在 DTD 中声明的符号      |    None |

#### 2. <span id="3.2">节点类型 - 返回值</span>
下面的表格列举了每个节点类型（nodetype）所返回的节点名称（nodeName）和节点值（nodeValue）：

| 节点类型        | 返回的节点名称           | 返回的节点值  |
| ------------- |:-------------:| -----:|
| Document | #document      |    null |
| DocumentFragment | #document fragment      |    null |
| DocumentType | 文档类型名称      |    null |
| Entity参考手册 | 实体引用名称      |    null |
| Element | 元素名称      |    null |
| Attr | 属性名称      |    属性值 |
| ProcessingInstruction | 目标      |    节点的内容 |
| Comment | #comment      |    注释文本 |
| Text | #text      |    节点的内容 |
| CDATASection | #cdata-section      |    节点的内容 |
| Entity | 实体名称      |    null |
| Notation | 符号名称      |    null |

#### 3. <span id="3.3">节点类型 - 命名常量</span>
| 节点类型        | 命名常量           |
| ------------- |:-------------:|
| 1 | ELEMENT_NODE      |
| 2 | ATTRIBUTE_NODE      |
| 3 | TEXT_NODE      |
| 4 | CDATA_SECTION_NODE      |
| 5 | ENTITY_REFERENCE_NODE      |
| 6 | ENTITY_NODE      |
| 7 | PROCESSING_INSTRUCTION_NODE      |
| 8 | COMMENT_NODE      |
| 9 | DOCUMENT_NODE      |
| 10 | DOCUMENT_TYPE_NODE      |
| 11 | DOCUMENT_FRAGMENT_NODE      |
| 12 | NOTATION_NODE      |

---
## <span id="4">XML DOM</span>
#### 1. <span id="4.1">XML解析器</span>
XML DOM 包含了遍历 XML 树，访问、插入及删除节点的方法（函数）。  
然而，在访问和操作 XML 文档之前，它必须加载到 XML DOM 对象。  
XML 解析器读取 XML，并把它转换为 XML DOM 对象，这样才可以使用 JavaScript 访问它。  
大多数浏览器有一个内建的 XML 解析器。

#### 2. <span id="4.2">加载XML文档</span>
> if (window.XMLHttpRequest) {  
xhttp=new XMLHttpRequest();  
} else {  
//IE 5&6  
xhttp=new ActiveXObject("Microsoft.XMLHTTP");  
}  
xhttp.open("GET","books.xml",false);  
xhttp.send();  
xmlDoc=xhttp.responseXML;

#### 3. <span id="4.3">加载XML字符串</span>
> if (window.DOMParser) {  
parser=new DOMParser();  
xmlDoc=parser.parseFromString(text,"text/xml");  
} else {  
// Internet Explorer
xmlDoc=new ActiveXObject("Microsoft.XMLDOM");  
xmlDoc.async=false;  
xmlDoc.loadXML(text);   
}

#### 4. <span id="4.4">XML DOM属性</span>
一些典型的DOM属性：

- x.nodeName - x 的名称
- x.nodeValue - x 的值
- x.parentNode - x 的父节点
- x.childNodes - x 的子节点
- x.attributes - x 的属性节点
- x.nodeType - x 的类型

注释：在上面的列表中，x 是一个节点对象。
> #### nodeName属性
> nodeName 属性规定节点的名称。
> 
> - nodeName 是只读的
> - 元素节点的 nodeName 与标签名相同
> - 属性节点的 nodeName 是属性的名称
> - 文本节点的 nodeName 永远是 #text
> - 文档节点的 nodeName 永远是 #document
> 
> #### nodeValue属性
> nodeValue 属性规定节点的值。
> 
> - 元素节点的 nodeValue 是 undefined
> - 文本节点的 nodeValue 是文本本身
> - 属性节点的 nodeValue 是属性的值
> 
> #### nodeType属性
> nodeType 属性规定节点的类型。  
> nodeType 是只读的。  
> 
> - 元素 - 1
> - 属性 - 2
> - 文本 - 3
> - 注释 - 4
> - 文档 - 5

#### 5. <span id="4.5">XML DOM方法</span>

- x.getElementsByTagName(name) - 获取带有指定标签名称的所有元素
- x.appendChild(node) - 向 x 插入子节点
- x.removeChild(node) - 从 x 删除子节点

注释：在上面的列表中，x 是一个节点对象。

#### 6. <span id="4.6">XML DOM操作实例</span>
从 books.xml 中的 &lt;title&gt; 元素获取文本的 JavaScript 代码：
> txt=xmlDoc.getElementsByTagName("title")[0].childNodes[0].nodeValue

解释：

- xmlDoc - 由解析器创建的 XML DOM 对象
- getElementsByTagName("title")[0] - 第一个 &lt;title&gt; 元素
- childNodes[0] - &lt;title&gt; 元素的第一个子节点（文本节点）
- nodeValue - 节点的值（文本本身）

#### 7. <span id="4.7">访问节点</span>
访问节点有三种方式：

> 1.通过使用 getElementsByTagName() 方法。
>> 语法：node.getElementsByTagName("tagname");  
 
> 下面的实例返回 x 元素下的所有 &lt;title&gt; 元素：
>> x.getElementsByTagName("title");

> 返回 XML 文档中的所有 &lt;title&gt; 元素
>> xmlDoc.getElementsByTagName("title");

> 在这里，xmlDoc 就是文档本身（文档节点）。 

> 2.通过循环（遍历）节点树。  
>> xmlDoc=loadXMLDoc("books.xml");  
x=xmlDoc.documentElement.childNodes;  
for (i=0;i<x.length;i++) {  
if (x[i].nodeType==1) {  
//Process only element nodes (type 1)  
document.write(x[i].nodeName);  
document.write("&lt;br&gt;");}  
}
> 
> 解释：
> 
> 1. 使用 loadXMLDoc() 把 "books.xml" 载入 xmlDoc 中
> 2. 获取根元素的子节点
> 3. 检查每个子节点的节点类型。如果节点类型是 "1"，则是元素节点
> 4. 如果是元素节点，则输出节点的名称
> 
> 3.通过利用节点的关系在节点树中导航。
>> xmlDoc=loadXMLDoc("books.xml");  
>> x=xmlDoc.getElementsByTagName("book")[0].childNodes;  
>> y=xmlDoc.getElementsByTagName("book")[0].firstChild;  
>> for (i=0;i&lt;x.length;i++) {  
>> if (y.nodeType==1) {  
>> //Process only element nodes (type 1)  
>> document.write(y.nodeName + "&lt;br&gt;");}  
>> y=y.nextSibling;}
> 
> 解释：
> 
> 1. 使用 loadXMLDoc() 把 "books.xml" 载入 xmlDoc 中
> 2. 获取第一个 book 元素的子节点
> 3. 把 "y" 变量设置为第一个 book 元素的第一个子节点
> 4. 对于每个子节点（第一个子节点从 "y" 开始），检查节点类型，如果节点类型为 "1"，则是元素节点
> 5. 如果是元素节点，则输出该节点的名称
> 6. 把 "y" 变量设置为下一个同级节点，并再次运行循环

#### 8. <span id="4.8">DOM节点列表</span>

- 当使用诸如 childNodes 或 getElementsByTagName() 的属性或方法是，会返回节点列表对象。
- 节点列表对象会保持自身的更新。如果删除或添加了元素，列表会自动更新。  
- 节点列表的 length 属性是列表中节点的数量。

#### 9. <span id="4.9">DOM 属性列表（命名节点图 Named Node Map）</span>

- 元素节点的 attributes 属性返回属性节点的列表。
- 这被称为命名节点图（Named Node Map），除了方法和属性上的一些差别以外，它与节点列表相似。
- 属性列表会保持自身的更新。如果删除或添加属性，这个列表会自动更新。

#### 10. <span id="4.10">导航DOM节点</span>
通过节点间的关系访问节点树中的节点，通常称为导航节点（"navigating nodes"）。  
在 XML DOM 中，节点的关系被定义为节点的属性：

- parentNode - 父节点
- childNodes - 所有子节点
- firstChild - 第一个子节点
- lastChild - 最后一个子节点
- nextSibling - 返回指定节点之后紧跟的节点,在相同的树层级中
- previousSibling - 返回指定节点之前的节点,在相同的树层级中

#### 11. <span id="4.11">获取节点的值</span>
##### 获取元素的值
元素节点没有文本值。
##### 获取文本的值
nodeValue 属性用于获取节点的文本值。
##### 获取属性的值
在 DOM 中，属性也是节点。与元素节点不同，属性节点拥有文本值。  
获取属性的值的方法，就是获取它的文本值。  
可以通过使用 getAttribute() 方法或属性节点的 nodeValue 属性来完成这个任务。
> xmlDoc=loadXMLDoc("books.xml");
> txt=xmlDoc.getElementsByTagName("title")[0].getAttribute("lang");

or
> xmlDoc=loadXMLDoc("books.xml");   
> x=xmlDoc.getElementsByTagName("title")[0].getAttributeNode("lang");   
> txt=x.nodeValue;

#### 12. <span id="4.12">改变节点的值</span>
##### 改变元素的值
元素节点没有文本值。
##### 改变文本的值
nodeValue 属性可用于改变文本节点的值。
##### 改变属性的值
在 DOM 中，属性也是节点。与元素节点不同，属性节点拥有文本值。  
改变属性的值的方法，就是改变它的文本值。  
可以通过使用 setAttribute() 方法或属性节点的 nodeValue 属性来完成这个任务。
> xmlDoc=loadXMLDoc("books.xml");  
> x=xmlDoc.getElementsByTagName('book');  
> x[0].setAttribute("category","food");

or
> xmlDoc=loadXMLDoc("books.xml");  
> x=xmlDoc.getElementsByTagName("book")[0];  
> y=x.getAttributeNode("category");  
> y.nodeValue="food";

#### 13. <span id="4.13">删除节点</span>
removeChild() 方法是唯一可以删除指定节点的方法。  
当一个节点被删除时，其所有子节点也会被删除。
##### 删除元素节点
> xmlDoc=loadXMLDoc("books.xml");  
> x=xmlDoc.getElementsByTagName("book")[0];  
> x.parentNode.removeChild(x);

##### 删除文本节点
不太常用 removeChild() 从节点删除文本。可以使用 nodeValue 属性代替它。请看下一段。
> xmlDoc=loadXMLDoc("books.xml");  
> x=xmlDoc.getElementsByTagName("title")[0].childNodes[0];  
> x.nodeValue="";

##### 删除属性节点
removeAttribute(name) 方法用于根据名称删除属性节点。  
> xmlDoc=loadXMLDoc("books.xml");  
> x=xmlDoc.getElementsByTagName("book");  
> x[0].removeAttribute("category");  

根据对象删除属性节点  
removeAttributeNode(node) 方法通过使用 node 对象作为参数，来删除属性节点。
> xmlDoc=loadXMLDoc("books.xml");   
> x=xmlDoc.getElementsByTagName("book");  
> for (i=0;i&lt;x.length;i++) {  
> while (x[i].attributes.length&gt;0) {  
> attnode=x[i].attributes[0];  
> old_att=x[i].removeAttributeNode(attnode);  
> }}

#### 14. <span id="4.14">替换节点</span>
##### 替换节点
replaceChild() 方法用于替换节点。
> x.replaceChild(newNode,y);

##### 替换文本节点中的数据
replaceData() 方法用于替换文本节点中的数据。  
replaceData() 方法有三个参数：

- offset - 在何处开始替换字符。offset 值以 0 开始。
- length - 要替换多少字符
- string - 要插入的字符串

> xmlDoc=loadXMLDoc("books.xml");  
> x=xmlDoc.getElementsByTagName("title")[0].childNodes[0];  
> x.replaceData(0,8,"Easy");

or （使用 nodeValue 属性代替）
> xmlDoc=loadXMLDoc("books.xml");  
> x=xmlDoc.getElementsByTagName("title")[0].childNodes[0];  
> x.nodeValue="Easy Italian";

#### 15. <span id="4.15">创建节点</span>
##### 创建元素节点
createElement() 方法创建一个新的元素节点
> newel=xmlDoc.createElement("edition");

##### 创建属性节点
createAttribute() 用于创建一个新的属性节点
> newatt=xmlDoc.createAttribute("edition");  
> newatt.nodeValue="first";  
> x=xmlDoc.getElementsByTagName("title");  
> x[0].setAttributeNode(newatt);

or （使用 setAttribute() 创建属性）  
由于 setAttribute() 方法可以在属性不存在的情况下创建新的属性，我们可以使用这个方法来创建一个新的属性。
> xmlDoc=loadXMLDoc("books.xml");  
> x=xmlDoc.getElementsByTagName('book');  
> x[0].setAttribute("edition","first");

##### 创建文本节点
createTextNode() 方法创建一个新的文本节点
> newtext=xmlDoc.createTextNode("first");

##### 创建 CDATA Section 节点
createCDATASection() 方法创建一个新的 CDATA section 节点
> xmlDoc=loadXMLDoc("books.xml");  
> newCDATA=xmlDoc.createCDATASection("Special Offer & Book Sale");  
> x=xmlDoc.getElementsByTagName("book")[0];  
> x.appendChild(newCDATA);

##### 创建注释节点
createComment() 方法创建一个新的注释节点
> xmlDoc=loadXMLDoc("books.xml");  
> newComment=xmlDoc.createComment("Revised March 2008");  
> x=xmlDoc.getElementsByTagName("book")[0];  
> x.appendChild(newComment);

#### 16. <span id="4.16">添加节点</span>
##### 添加节点 - appendChild()
appendChild() 方法向一个已有的节点添加一个子节点。  
新节点会添加（追加）到任何已有的子节点之后。
> x.appendChild(newel);

##### 添加节点 - insertBefore()
insertBefore()方法用于在指定的子节点之前插入节点。
> x.insertBefore(newNode,y);

##### 添加新属性
addAtribute() 这个方法是不存在的。  
如果属性不存在，则 setAttribute() 可创建一个新的属性

##### 向文本节点添加文本 - insertData()
insertData() 方法将数据插入已有的文本节点中。  
insertData() 方法有两个参数：  

- offset - 在何处开始插入字符（以 0 开始）
- string - 要插入的字符串

> xmlDoc=loadXMLDoc("books.xml");  
> x=xmlDoc.getElementsByTagName("title")[0].childNodes[0];  
> x.insertData(0,"Easy ");

#### 17. <span id="4.17">克隆节点</span>
cloneNode() 方法创建指定节点的副本。  
cloneNode() 方法有一个参数（true 或 false）。该参数指示被克隆的节点是否包括原节点的所有属性和子节点。
> xmlDoc=loadXMLDoc("books.xml");  
> oldNode=xmlDoc.getElementsByTagName('book')[0];  
> newNode=oldNode.cloneNode(true);  
> xmlDoc.documentElement.appendChild(newNode);  

#### 18. <span id="4.18">The XMLHttpRequest对象</span>
通过 XMLHttpRequest 对象，您可以在不重新加载整个页面的情况下更新网页中的某个部分。  
XMLHttpRequest 对象用于幕后与服务器交换数据。  
XMLHttpRequest 对象是开发者的梦想，因为您可以：

- 在不重新加载页面的情况下更新网页
- 在页面已加载后从服务器请求数据
- 在页面已加载后从服务器接收数据
- 在后台向服务器发送数据

##### 创建 XMLHttpRequest 对象
所有现代的浏览器（IE7+、Firefox、Chrome、Safari 和 Opera）都有一个内建的 XMLHttpRequest 对象。
> xmlhttp=new XMLHttpRequest();

旧版本的 Internet Explorer（IE5 和 IE6）使用 ActiveX 对象。
> xmlhttp=new ActiveXObject("Microsoft.XMLHTTP");

为了处理所有现代的浏览器，包括 IE5 和 IE6，请检查浏览器是否支持 XMLHttpRequest 对象。如果支持，则创建一个 XMLHttpRequest 对象，如果不支持，则创建一个 ActiveX 对象：
> if (window.XMLHttpRequest) {  
> xmlhttp=new XMLHttpRequest();  
> } else {  
> xmlhttp=new ActiveXObject("Microsoft.XMLHTTP");  
> }

##### 发送请求到服务器
open(method,url,async)  
规定请求的类型，URL，请求是否应该进行异步处理。

- method：请求的类型：GET 或 POST
- url：文件在服务器上的位置
- async：true（异步）或 false（同步）

send(string)  
发送请求到服务器。

- string：仅用于 POST 请求

<pre>
<blod style="font-size:18px;">GET 或 POST？</blod>
GET 比 POST 简单并且快速，可用于大多数情况下。
然而，下面的情况下请始终使用 POST 请求：
<ul>
<li>缓存的文件不是一个选项（更新服务器上的文件或数据库）</li>
<li>发送到服务器的数据量较大（POST 没有大小的限制）</li>
<li>发送用户输入（可以包含未知字符），POST 比 GET 更强大更安全</li>
</ul>
<blod style="font-size:18px;">异步 - True 或 False?</blod>
发送异步请求对于 Web 开发人员是一个巨大的进步。在服务器上执行的许多任务非常费时。
不推荐使用 async=false，但如果处理几个小的请求还是可以的。
通过异步发送，JavaScript 不需要等待服务器的响应，但可以替换为：
<ul>
<li>等待服务器的响应时，执行其他脚本</li>
<li>响应准备时处理响应</li>
</ul>
</pre>

##### 服务器响应
如需从服务器获取响应，请使用 XMLHttpRequest 对象的 responseText 或 responseXML 属性。

- responseText - 获取响应数据作为字符串
- responseXML - 获取响应数据作为 XML 数据

如果来自服务器的响应不是 XML，请使用 responseText 属性。  
如果来自服务器的响应不是 XML，且您想要把它解析为 XML 对象，请使用 responseXML 属性

##### onreadystatechange 事件
当请求被发送到服务器，我们要根据响应执行某些动作。  
onreadystatechange 事件在每次 readyState 变化时被触发。  
readyState 属性持有 XMLHttpRequest 的状态。  
XMLHttpRequest 对象的三个重要的属性：

- onreadystatechange - 存储函数（或函数的名称）在每次 readyState 属性变化时被自动调用
- readyState - 存放了 XMLHttpRequest 的状态。从 0 到 4 变化：0-请求未初始化；1-服务器建立连接；2-收到的请求；3-处理请求；4-请求完成和响应准备就绪
- status - 200："OK"；404：找不到页面

> xmlhttp.onreadystatechange=function() {  
> if (xmlhttp.readyState\=\=4 && xmlhttp.status\=\=200) {  
> document.getElementById("myDiv").innerHTML=xmlhttp.responseText;  
> }}  

***onreadystatechange 事件在每次 readyState 发生变化时被触发，总共触发了四次。***

### <span id="xmlps">提示</span>
出于安全原因，现代的浏览器不允许跨域访问。  
这意味着，网页以及 XML 文件，它必须位于同一台服务器上尝试加载。  
W3CSchool 上的实例中所有打开的 XML 文件都是位于 W3CSchool 域上的。  
如果您想要在您的网页上使用上面的实例，您加载的 XML 文件必须位于您自己的服务器上。

---

## <span id="5">DOM中的对象</span>
#### 1. <span id="5.1">Node对象</span>
**Node 对象代表文档树中的一个单独的节点。**   
这里的节点可以是：元素节点、属性节点、文本节点以及所有在 节点类型这章中所提到的所有其他的节点类型。  
请注意，尽管所有的对象都继承了用以处理父节点和子节点的 Node 属性 / 方法，但是并不是所有的对象都可以包含父节点或子节点。举个例子来说，Text 节点中可能不包含子节点，所以把子节点添加到文本节点中可能会导致一个 DOM 错误。
##### Node 对象属性

| 属性        | 描述           |
| ------------- |:-------------:|
|baseURI	| 返回节点的绝对基准 URI。|
|childNodes	|返回节点的子节点的节点列表。|
|firstChild	|返回节点的第一个子节点。|
|lastChild	|返回节点的最后一个子节点。|
|localName	|返回节点名称的本地部分。|
|namespaceURI	|返回节点的命名空间 URI。|
|nextSibling	|返回元素之后紧接的节点。|
|nodeName	|返回节点的名称，根据其类型。|
|nodeType	|返回节点的类型。|
|nodeValue	|设置或返回节点的值，根据其类型。|
|ownerDocument|	返回节点的根元素（document 对象）。|
|parentNode	|返回节点的父节点。|
|prefix	|设置或返回节点的命名空间前缀。|
|previousSibling	|返回元素之前紧接的节点。|
|textContent	|设置或返回节点及其后代的文本内容。|

##### Node 对象方法

| 方法        | 描述           |
| ------------- |:-------------:|
|appendChild()	|把新的子节点添加到节点的子节点列表末尾。|
|cloneNode()|	克隆节点。|
|compareDocumentPosition()	|比较两个节点的文档位置。|
|getFeature(feature,version)	|返回 DOM 对象，此对象可执行带有指定特性和版本的专门的 API。|
|getUserData(key)|	返回与节点上键关联的对象。此对象必须首先通过使用相同的键调用 setUserData 来设置到此节点。|
|hasAttributes()	|如果节点拥有属性，则返回 ture，否则返回 false。|
|hasChildNodes()	|如果节点拥有子节点，则返回 true，否则返回 false。|
|insertBefore()	|在已有的子节点之前插入一个新的子节点。|
|isDefaultNamespace(URI)|	返回指定的 namespaceURI 是否默认。|
|isEqualNode()	|检查两个节点是否相等。|
|isSameNode()	|检查两个节点是否为同一节点。|
|isSupported(feature,version)	|返回指定的特性是否在此节点上得到支持。|
|lookupNamespaceURI()	|返回匹配指定前缀的命名空间 URI。|
|lookupPrefix()|	返回匹配指定命名空间 URI 的前缀。|
|normalize()	|把节点（包括属性）下的所有文本节点放置到一个"标准"的格式中，其中只有结构（比如元素、注释、处理指令、CDATA 区段以及实体引用）来分隔 Text 节点，例如，既没有相邻的 Text 节点，也没有空的 Text 节点。|
|removeChild()	|删除子节点。|
|replaceChild()	|替换子节点。|
|setUserData(key,data,handler)	|把对象关联到节点上的键。|

#### 2. <span id="5.2">NodeList 对象</span>
**NodeList 对象代表一个有序的节点列表。**  
节点列表中的节点可以通过其对应的索引数字（从 0 开始计数）进行访问。  
节点列表可保持其自身的更新。如果节点列表或 XML 文档中的某个元素被删除或添加，列表也会被自动更新。  
注意：在一个节点列表中，节点被返回的顺序与它们在 XML 文档中被规定的顺序相同。  

##### NodeList 对象属性
| 属性        | 描述           |
| ------------- |:-------------:|
|length|	返回节点列表中的节点数量。|

##### NodeList 对象方法
| 方法        | 描述           |
| ------------- |:-------------:|
|item()	|返回节点列表中指定索引号的节点。|

#### 3. <span id="5.3">NamedNodeMap 对象</span>
**NamedNodeMap 对象代表一个节点的无序列表。**  
NamedNodeMap 中的节点可以通过它们的名称进行访问。  
NamedNodeMap 将会自我更新。如果在节点列表或 XML 文档中删除或添加一个元素，那么该列表将会自动更新。  
注意：在命名节点图中，节点不会以任何特定的顺序返回。

##### NamedNodeMap 对象属性
| 属性        | 描述           |
| ------------- |:-------------:|
|length|	返回列表中节点的数量。|

##### NamedNodeMap 对象方法
| 方法        | 描述           |
| ------------- |:-------------:|
|getNamedItem()	|返回指定的节点（通过名称）。|
|getNamedItemNS()|	返回指定的节点（通过名称和命名空间）。|
|item()	|返回指定索引号的节点。|
|removeNamedItem()	|删除指定的节点（通过名称）。|
|removeNamedItemNS()|	删除指定的节点（通过名称和命名空间）。|
|setNamedItem()	|设置指定的节点（通过名称）。|
|setNamedItemNS()	|设置指定的节点（通过名称和命名空间）。|

#### 4. <span id="5.4">Document 对象</span>
**Document 对象代表整个 XML 文档。**  
Document 对象是文档树的根，并为我们提供对文档数据的最初（或最顶层）的访问入口。  
由于元素节点、文本节点、注释、处理指令等均无法存在于文档之外，Document 对象也提供了创建这些对象的方法。Node 对象提供了一个 ownerDocument 属性，此属性可把它们与在其中创建它们的 Document 关联起来。

##### Document 对象属性
| 属性        | 描述           |
| ------------- |:-------------:|
|async	规定 XML |文件的下载是否应当被异步处理。|
|childNodes	|返回文档的子节点的节点列表。|
|doctype	|返回与文档相关的文档类型声明（DTD，全称 Document Type Declaration）。|
|documentElement|	返回文档的根节点。|
|documentURI	|设置或返回文档的位置。|
|domConfig	|返回 normalizeDocument() 被调用时所使用的配置。|
|firstChild	|返回文档的第一个子节点。|
|implementation|	返回处理该文档的 DOMImplementation 对象。|
|inputEncoding|	返回用于文档的编码方式（在解析时）。|
|lastChild|	返回文档的最后一个子节点。|
|nodeName	|返回节点的名称（根据节点的类型）。|
|nodeType	|返回节点的节点类型。|
|nodeValue	|设置或返回节点的值（根据节点的类型）。|
|strictErrorChecking	|设置或返回是否强制进行错误检查。|
|xmlEncoding	|返回文档的 XML 编码。|
|xmlStandalone|	设置或返回文档是否为 standalone。|
|xmlVersion	|设置或返回文档的 XML 版本。|

#####Document 对象方法
| 方法        | 描述           |
| ------------- |:-------------:|
|adoptNode(sourcenode)	|从另一个文档向本文档选定一个节点，然后返回被选节点。|
|createAttribute(name)	|创建带有指定名称的属性节点，并返回新的 Attr 对象。|
|createAttributeNS(uri,name)	|创建带有指定名称和命名空间的属性节点，并返回新的 Attr 对象。|
|createCDATASection()	|创建 CDATA 区段节点。|
|createComment()	|创建注释节点。|
|createDocumentFragment()	|创建空的 DocumentFragment 对象，并返回此对象。|
|createElement()	|创建元素节点。|
|createElementNS()	|创建带有指定命名空间的元素节点。|
|createEntityReference(name)	|创建 EntityReference 对象，并返回此对象。|
|createProcessingInstruction(target,data)|	创建一个 ProcessingInstruction 对象，并返回此对象。|
|createTextNode()	|创建文本节点。|
|getElementById(id)	|返回带有指定值的 ID 属性的元素。如果不存在这样的元素，则返回 null。|
|getElementsByTagName()	|返回带有指定名称的所有元素的 NodeList。|
|getElementsByTagNameNS()	|返回带有指定名称和命名空间的所有元素的 NodeList。|
|importNode(nodetoimport,deep)	|从另一个文档向本文档选定一个节点。该方法创建源节点的一个新的副本。如果 deep 参数设置为 true，它将导入指定节点的所有子节点。 如果设置为 false，它将只导入节点本身。该方法返回被导入的节点。|
|normalizeDocument()||	
|renameNode()|	重命名元素或属性节点。|

#### 5. <span id="5.5">DocumentImplementation 对象</span>
**DOMImplementation 对象执行的操作是独立于文档对象模型的任何特定实例。**  

##### DocumentImplementation 对象方法
| 方法        | 描述           |
| ------------- |:-------------:|
|createDocument(nsURI, name, doctype)	|创建一个新的指定文档类型的 DOM Document 对象。|
|createDocumentType(name, pubId, systemId)	|创建一个空的 DocumentType 节点。
|getFeature(feature, version)	|返回一个对象，此对象可执行带有指定特性和版本的 API。|
|hasFeature(feature, version)	|检查 DOM implementation 是否实现指定的特性和版本。|

#### 6. <span id="5.6">DocumentType 对象</span>
每个文档都包含一个 DOCTYPE 属性，该属性值可以是一个空值或是一个 DocumentType 对象。  
DocumentType 对象提供了一个接口，用于定义 XML 文档的实体。  

##### DocumentType 对象属性
| 属性        | 描述           |
| ------------- |:-------------:|
|entities|	返回包含有在 DTD 中所声明的实体的 NamedNodeMap。|
|internalSubset|	以字符串形式返回内部 DTD。|
|name|	返回 DTD 的名称。|
|notations	|返回包含 DTD 声明的符号的 NamedNodeMap。|
|systemId	|返回外部 DTD 的系统标识符。|

#### 7. <span id="5.7">ProcessingInstruction 对象</span>
**ProcessingInstruction 对象代表一个处理指令。**  
处理指令用于维护 XML 文档的文本中特定处理器的信息。  

##### ProcessingInstruction 对象属性
| 属性        | 描述           |
| ------------- |:-------------:|
|data	|设置或返回处理指令的内容。|
|target	|返回处理指令的目标。|

#### 8. <span id="5.8">Element 对象</span>
**Element 对象代表 XML 文档中的一个元素。**  
元素可以包含属性、其他元素或文本。如果一个元素包含文本，则在文本节点中表示该文本。  
由于 Element 对象也是一种节点，因此它可继承 Node 对象的属性和方法。

##### Element 对象属性
| 属性        | 描述           |
| ------------- |:-------------:|
|attributes|	返回元素的属性的 NamedNodeMap。|
|baseURI	|返回元素的绝对基准 URI。|
|childNodes|	返回元素的子节点的 NodeList。|
|firstChild|	返回元素的第一个子节点。|
|lastChild|	返回元素的最后一个子节点。|
|localName|	返回元素名称的本地部分。|
|namespaceURI|	返回元素的命名空间 URI。|
|nextSibling|	返回元素之后紧接的节点。|
|nodeName	|返回节点的名称，根据其类型。|
|nodeType|	返回节点的类型。|
|ownerDocument|	返回元素所属的根元素 (document 对象)。|
|parentNode|	返回元素的父节点。|
|prefix	|设置或返回元素的命名空间前缀。|
|previousSibling	|返回元素之前紧接的节点。|
|schemaTypeInfo	|返回与元素相关联的类型信息。|
|tagName	|返回元素的名称。|
|textContent	|设置或返回元素及其后代的文本内容。|

##### Element 对象方法
| 方法        | 描述           |
| ------------- |:-------------:|
|appendChild()|	把新的子节点添加到节点的子节点列表末尾。|
|cloneNode()	|克隆节点。|
|compareDocumentPosition()|	比较两个节点的文档位置。|
|getAttribute()	|返回属性的值。|
|getAttributeNS()	|返回属性的值（带有命名空间）。|
|getAttributeNode()	|以 Attribute 对象返回属性节点。|
|getAttributeNodeNS()	|以 Attribute 对象返回属性节点（带有命名空间）。|
|getElementsByTagName()	|返回匹配的元素节点及它们的子节点的 NodeList。|
|getElementsByTagNameNS()	|返回匹配的元素节点（带有命名空间）及它们的子节点的 NodeList。|
|getFeature(feature,version)|	返回 DOM 对象，此对象可执行带有指定特性和版本的专门的 API。|
|getUserData(key)	|返回与节点上键关联的对象。此对象必须首先通过使用相同的键调用 setUserData 来设置到此节点。|
|hasAttribute()	|返回元素是否拥有匹配指定名称的属性。|
|hasAttributeNS()|	返回元素是否拥有匹配指定名称和命名空间的属性。|
|hasAttributes()	|返回元素是否拥有属性。|
|hasChildNodes()	|返回元素是否拥有子节点。|
|insertBefore()	|在已有的子节点之前插入一个新的子节点。|
|isDefaultNamespace(URI)	|返回指定的 namespaceURI 是否为默认。|
|isEqualNode()	|检查两个节点是否相等。|
|isSameNode()	|检查两个节点是否为同一节点。|
|isSupported(feature,version)	|返回指定的特性是否在此元素上得到支持。|
|lookupNamespaceURI()	|返回匹配指定前缀的命名空间 URI。|
|lookupPrefix()	|返回匹配指定命名空间 URI 的前缀。|
|normalize()	|把节点（包括属性）下的所有文本节点放置到一个"标准"的格式中，其中只有结构（比如元素、注释、处理指令、CDATA 区段以及实体引用）来分隔 Text 节点，例如，既没有相邻的 Text 节点，也没有空的 Text 节点。|
|removeAttribute()	|删除指定的属性。|
|removeAttributeNS()	|删除指定的属性（带有命名空间）。|
|removeAttributeNode()	|删除指定的属性节点。|
|removeChild()	|删除子节点。|
|replaceChild()	|替换子节点。|
|setUserData(key,data,handler)	|把对象关联到元素上的键。|
|setAttribute()	|添加新属性。|
|setAttributeNS()	|添加新属性（带有命名空间）。|
|setAttributeNode()	|添加新的属性节点。|
|setAttributeNodeNS(attrnode)	|添加新的属性节点（带有命名空间）。|
|setIdAttribute(name,isId)	|如果 Attribute 对象的 isId 属性为 true，那么此方法会把指定的属性声明为一个用户确定 ID 的属性（user-determined ID attribute）。|
|setIdAttributeNS(uri,name,isId)	|如果 Attribute 对象的 isId 属性为 true，那么此方法会把指定的属性声明为一个用户确定 ID 的属性（user-determined ID attribute）（带有命名空间）。|
|setIdAttributeNode(idAttr,isId)|	如果 Attribute 对象的 isId 属性为 true，那么此方法会把指定的属性声明为一个用户确定 ID 的属性（user-determined ID attribute）。|

#### 9. <span id="5.9">Attr 对象</span>
**Attr 对象表示 Element 对象的属性。**  
属性的容许值通常定义在 DTD 中。  
由于 Attr 对象也是一种节点，因此它继承 Node 对象的属性和方法。不过属性无法拥有父节点，同时属性也不被认为是元素的子节点，对于许多 Node 属性来说都将返回 null。  

##### Attr 对象属性
| 属性        | 描述           |
| ------------- |:-------------:|
|baseURI|	返回属性的绝对基准 URI。|
|isId	|如果属性是 ID 类型，则返回 true，否则返回 false。|
|localName|	返回属性名称的本地部分。|
|name	|返回属性的名称。|
|namespaceURI|	返回属性的命名空间 URI。|
|nodeName	|返回节点的名称，根据其类型。|
|nodeType	|返回节点的类型。|
|nodeValue|	设置或返回节点的值，根据其类型。|
|ownerDocument	|返回属性所属的根元素（document 对象）。|
|ownerElement|	返回属性所附属的元素节点。|
|prefix|	设置或返回属性的命名空间前缀。|
|schemaTypeInfo|	返回与属性相关联的类型信息。|
|specified	|如果属性值被设置在文档中，则返回 true，如果其默认值被设置在 DTD/Schema 中，则返回 false。|
|textContent|	设置或返回属性的文本内容。|
|value|	设置或返回属性的值。|

#### 10. <span id="5.10">Text 对象</span>
**Text 对象表示元素或属性的文本内容。**  

##### Text 对象属性
| 属性        | 描述           |
| ------------- |:-------------:|
|data	|设置或返回元素或属性的文本。|
|isElementContentWhitespace	|判断文本节点是否包含空白字符内容。如果文本节点包含空白字符内容，则返回 true，否则返回 false。|
|length|	返回元素或属性的文本长度。|
|wholeText|	以文档中的顺序向此节点返回相邻文本节点的所有文本。|

##### Text 对象方法
| 方法        | 描述           |
| ------------- |:-------------:|
|appendData()	|向节点追加数据。|
|deleteData()	|从节点删除数据。|
|insertData()	|向节点中插入数据。|
|replaceData()|	替换节点中的数据。|
|replaceWholeText(text)	|使用指定文本来替换此节点以及所有相邻的文本节点。|
|splitText()|	在指定的偏移处将此节点拆分为两个节点，同时返回包含偏移处之后的文本的新节点。|
|substringData()	|从节点提取数据。|

#### 11. <span id="5.11">CDATASection 对象</span>
**CDATASection 对象表示文档中的 CDATA 区段。**  
CDATA 区段包含了不会被解析器解析的文本。一个 CDATA 区段中的标签不会被视为标记，同时实体也不会被展开。主要的目的是为了包含诸如 XML 片段之类的材料，而无需转义所有的分隔符。  
在一个 CDATA 区段中唯一被识别的分隔符是 "]]>"，它可标示 CDATA 区段的结束。CDATA 区段不能进行嵌套。

##### CDATASection 对象属性
| 属性        | 描述           |
| ------------- |:-------------:|
|data	|设置或返回此节点的文本。|
|length	|返回 CDATA 区段的长度。|

##### CDATASection 对象方法
| 方法        | 描述           |
| ------------- |:-------------:|
|appendData()	|向节点追加数据。|
|deleteData()	|从节点删除数据。|
|insertData()	|向节点中插入数据。|
|replaceData()	|替换节点中的数据。|
|splitText()	|把 CDATA 节点分拆为两个节点。|
|substringData()	|从节点提取数据。|

#### 12. <span id="5.12">Comment 对象</span>
**Comment 对象表示文档中注释节点的内容。**  

##### Comment 对象属性
| 属性        | 描述           |
| ------------- |:-------------:|
|data	|设置或返回此节点的文本。|
|length	|返回此节点的文本的长度。|

##### Comment 对象方法
| 方法        | 描述           |
| ------------- |:-------------:|
|appendData()	|向节点追加数据。|
|deleteData()	|从节点删除数据。|
|insertData()	|向节点中插入数据。|
|replaceData()	|替换节点中的数据。|
|substringData()	|从节点提取数据。|

#### 13. <span id="5.13">XMLHttpRequest 对象</span>
**通过 XMLHttpRequest 对象，您可以在不重新加载整个页面的情况下更新网页中的某个部分。**  

##### XMLHttpRequest 对象方法
| 属性        | 描述           |
| ------------- |:-------------:|
|abort()	|取消当前的请求。|
|getAllResponseHeaders()	|返回头信息。|
|getResponseHeader()|	返回指定的头信息。|
|open(method,url,async,uname,pswd)	|规定请求的类型，URL，请求是否应该进行异步处理，以及请求的其他可选属性。 method：请求的类型：GET 或 POST。url：文件在服务器上的位置。async：true（异步）或 false（同步）|
|send(string)	|发送请求到服务器。|
|string：|仅用于 POST 请求|
|setRequestHeader()|	把标签/值对添加到要发送的头文件。|

##### XMLHttpRequest 对象属性
| 方法        | 描述           |
| ------------- |:-------------:|
|onreadystatechange|	存储函数（或函数的名称）在每次 readyState 属性变化时被自动调用。|
|readyState	|存放了 XMLHttpRequest 的状态。从 0 到 4 变化：0：请求未初始化。1：服务器建立连接。2：收到的请求。3：处理请求。4：请求完成和响应准备就绪|
|responseText|	返回作为一个字符串的响应数据。|
|responseXML|	返回作为 XML 数据响应数据。|
|status|	返回状态数（例如 "404" 为 "Not Found" 或 "200" 为 "OK"）。|
|statusText	|返回状态文本（如 "Not Found" 或 "OK"）。|

#### 14. <span id="5.14">Parse Error 对象</span>
**微软的 parseError 对象可用于从微软的 XML 分析器取回错误信息。**  
在您试图打开一个 XML 文档时，就可能发生一个解析器错误（parser-error）。  通过这个 parseError 对象，您可取回错误代码、错误文本、引起错误的行等等。  
注意：parseError 对象不属于 W3C DOM 标准！  

##### parseError 对象的属性
| 属性        | 描述           |
| ------------- |:-------------:|
|errorCode|	返回一个长整数错误代码。|
|reason	|返回一个字符串，包含错误的原因。|
|line	|返回一个长整数，代表错误的行号。|
|linepos|	返回一个长整数，代表错误的行位置。|
|srcText|	返回一个字符串，包含引起错误的行。|
|url	|返回指向被加载文档的 URL。|
|filepos|	返回错误的一个长整型文件位置。|

---
## <span id="6">HTML DOM</span>
#### 1. <span id="6.1">HTML DOM方法</span>
一些常用的 HTML DOM 方法：

- getElementById(id) - 获取带有指定 id 的节点（元素）
- appendChild(node) - 插入新的子节点（元素）
- removeChild(node) - 删除子节点（元素）
- replaceChild() - 替换子节点
- insertBefore() - 在指定的子节点前面插入新的子节点
- createAttribute() - 创建属性节点
- createElement() - 创建元素节点
- createTextNode() - 创建文本节点
- getAttribute() - 返回指定的属性值
- setAttribute() - 把指定属性设置或修改为指定的值

#### 2. <span id="6.2">HTML DOM属性</span>
一些常用的 HTML DOM 属性：

- innerHTML - 节点（元素）的文本值
- parentNode - 节点（元素）的父节点
- childNodes - 节点（元素）的子节点
- attributes - 节点（元素）的属性节点

> #### innerHTML 属性
>> 获取元素内容的最简单方法是使用 innerHTML 属性。
>> innerHTML 属性对于获取或替换 HTML 元素的内容很有用。

#### 3. <span id="6.3">HTML DOM访问</span>
访问 HTML 元素等同于访问节点  
您能够以不同的方式来访问 HTML 元素：

- 通过使用 getElementById() 方法
- 通过使用 getElementsByTagName() 方法
- 通过使用 getElementsByClassName() 方法

***注意：getElementsByClassName() 在 Internet Explorer 5,6,7,8 中无效。***

#### 4. <span id="6.4">HTML DOM修改</span>
修改 HTML DOM 意味着许多不同的方面：

- 改变 HTML 内容
- 改变 CSS 样式
- 改变 HTML 属性
- 创建新的 HTML 元素
- 删除已有的 HTML 元素
- 改变事件（处理程序）

> #### 创建 HTML 内容
> 改变元素内容的最简单的方法是使用 innerHTML 属性。
>> document.getElementById("p1").innerHTML="New text!";

> #### 改变 HTML 样式
> 通过 HTML DOM，您能够访问 HTML 元素的样式对象。
>> document.getElementById("p2").style.color="blue";

> #### 创建新的 HTML 元素
> 如需向 HTML DOM 添加新元素，您首先必须创建该元素（元素节点），然后把它追加到已有的元素上。
>> var para=document.createElement("p");
>> var node=document.createTextNode("This is new.");
>> para.appendChild(node);
>> var element=document.getElementById("d1");
>> element.appendChild(para);

#### 5. <span id="6.5">HTML DOM事件</span>
分配事件例子：
> document.getElementById("myBtn").onclick=function(){displayDate()};

#### 6. <span id="6.6">HTML DOM根节点</span>
这里有两个特殊的属性，可以访问全部文档：

- document.documentElement - 全部文档
- document.body - 文档的主体

---
## <span id="7">浏览器差异</span>
#### 1. <span id="7.1">空白和换行</span>
XML 经常在节点之间包含换行或空白字符。这是在使用简单的编辑器（比如记事本）编辑文档时经常出现的情况。
下面的例子（由记事本编辑）在每行之间包含 CR/LF（换行），在每个子节点之前包含两个空格。***Internet Explorer 将不会把空的空白或换行作为文本节点，而其他浏览器会。***
> 避免空的文本节点
Firefox 以及其他一些浏览器，把空的空白或换行当作文本节点，而 Internet Explorer 不会这么做。  
这会在使用以下属性：firstChild、lastChild、nextSibling、previousSibling 时产生一个问题。  
为了避免导航到空的文本节点（元素节点之间的空格和换行符），我们使用一个函数来检查节点类型：  
function get_nextSibling(n) {  
y=n.nextSibling;  
while (y.nodeType!=1) {  
y=y.nextSibling;}  
return y;  
}  
function get_lastChild(n) {  
y=n.lastChild;  
while (y.nodeType!=1) {  
  y=y.previousSibling; }  
return y;  
}  
function get_previousSibling(n) {  
y=n.previousSibling;  
while (y.nodeType!=1) {  
  y=y.previousSibling;}  
return y;  
}  