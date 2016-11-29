<c:import>标签提供了所有<jsp:include>行为标签所具有的功能，同时也允许包含绝对URL。

举例来说，使用<c:import>标签可以包含一个FTP服务器中不同的网页内容。

### 语法
```
<c:import
   url="<string>"
   var="<string>"
   scope="<string>"
   varRender="<string>"
   context="<string>"
   charEncoding="<string>"/>
```

### 属性
- url:待导入资源的URL，可以是相对路径和绝对路径，并且可以导入其他主机资源
    必需:是
    默认值:无

- context:当使用相对路径访问外部context资源时，context指定了这个资源的名字。
	必需:否
    默认值:当前应用程序

- charEncoding:所引入的数据的字符编码集
    必需:否
    默认值:ISO-8859-1

- var:用于存储所引入的文本的变量
    必需:是
    默认值:无

- scope:var属性的作用域
	必需:否
    默认值:page

- varReader:可选的用于提供java.io.Reader对象的变量
    必需:否
    默认值:无

### 举例
```
<c:import var="data" url="http://www.runoob.com"/>
<c:out value="${data}"/>

以上程序将会打印http://www.runoob.com"页面的源代码
```
