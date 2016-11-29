<c:param>标签用于在<c:url>标签中指定参数，而且与URL编码相关。

在<c:param>标签内，name属性表明参数的名称，value属性表明参数的值。

### 语法:
```
<c:param name="<string>" value="<string>"/>
```

### 属性:
- name:URL中要设置的参数的名称
    必需:是
    默认值:无

- value:参数的值
    必需:是
    默认值:Body

### 举例:
```
<c:url var="myURL" value="main.jsp">
    <c:param name="name" value="Runoob"/>
    <c:param name="url" value="www.runoob.com"/>
</c:url>
<a href="/<c:out value="${myURL}"/>">

通过浏览器访问以上页面，然后查看源代码
```
