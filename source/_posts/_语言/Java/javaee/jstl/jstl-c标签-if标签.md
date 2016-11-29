<c:if>标签判断表达式的值，如果表达式的值为 true 则执行其主体内容。

### 语法
```
<c:if test="<boolean>" var="<string>" scope="<string>">
   ...
</c:if>
```

### 属性
- test:条件
    必需:是
    默认值:无

- var:用于存储条件结果的变量
    必需:否
    默认值:无

- scope:var属性的作用域
	必需:否
    默认值:page

### 举例
```
<c:set var="salary" scope="session" value="${2000*2}"/>
<c:if test="${salary > 2000}">
   <p>我的工资为: <c:out value="${salary}"/><p>
</c:if>

我的工资为: 4000
```
