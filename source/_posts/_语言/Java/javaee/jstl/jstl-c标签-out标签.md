<c:out>标签用来显示一个表达式的结果，与<%= %>作用相似，它们的区别就是<c:out>标签可以直接通过"."操作符来访问属性。

举例来说，如果想要访问customer.address.street，只需要这样写：<c:out value="customer.address.street">。

<c:out>标签会自动忽略XML标记字符，所以它们不会被当做标签来处理。

### 语法
```
<c:out value="<string>" default="<string>" escapeXml="<true|false>"/>
```

### 属性
- value:输出的信息
    必需:是
    默认值:None

- default:输出的默认值
    必需:否
    默认值:主体中的内容

- escapeXml:是否忽略XML特殊字符
    必需:否
    默认值:true

### 举例
```
<c:out value="&lt要显示的数据对象（未使用转义字符）&gt" escapeXml="true" default="默认值"></c:out><br/>
<c:out value="&lt要显示的数据对象（使用转义字符）&gt" escapeXml="false" default="默认值"></c:out><br/>
<c:out value="${null}" escapeXml="false">使用的表达式结果为null，则输出该默认值</c:out><br/>

&lt要显示的数据对象（未使用转义字符）&gt
<要显示的数据对象（使用转义字符）>
使用的表达式结果为null，则输出该默认值
```
