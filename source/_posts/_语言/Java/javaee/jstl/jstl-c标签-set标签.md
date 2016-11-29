<c:set>标签用于设置变量值和对象属性。

<c:set>标签就是<jsp:setProperty>行为标签的孪生兄弟。

这个标签之所以很有用呢，是因为它会计算表达式的值，然后使用计算结果来设置 JavaBean 对象或 java.util.Map 对象的值。

### 语法
```
<c:set
   var="<string>"
   value="<string>"
   target="<string>"
   property="<string>"
   scope="<string>"/>

如果指定了target属性，那么property属性也需要被指定。
```

### 属性
- value:要存储的值
	必需:否
    默认值:主体的内容

- target:要修改的属性所属的对象
    必需:否
    默认值:无

- property:要修改的属性
    必需:否
    默认值:无

- var:存储信息的变量
    必需:否
    默认值:无

- scope:var属性的作用域
	必需:否
    默认值:Page

### 举例:
```
<c:set var="salary" scope="session" value="${2000*2}"/>
<c:out value="${salary}"/>

4000
```
