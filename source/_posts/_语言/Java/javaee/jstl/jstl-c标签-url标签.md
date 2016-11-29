<c:url>标签将URL格式化为一个字符串，然后存储在一个变量中。

这个标签在需要的时候会自动重写URL。

var属性用于存储格式化后的URL。

<c:url>标签只是用于调用response.encodeURL()方法的一种可选的方法。它真正的优势在于提供了合适的URL编码，包括<c:param>中指定的参数。

### 语法
```
<c:url
  var="<string>"
  scope="<string>"
  value="<string>"
  context="<string>"/>
```

### 属性
- value:基础URL
    必需:是
    默认值:无

- context:本地网络应用程序的名称
    必需:否
    默认值:当前应用程序

- var:代表URL的变量名
	必需:否
    默认值:Print to page

- scope:var属性的作用域
	必需:否
    默认值:Page

### 举例
```
<a href="<c:url value="http://www.runoob.com"/>">
```
