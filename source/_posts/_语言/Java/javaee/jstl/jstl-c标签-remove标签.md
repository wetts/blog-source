<c:remove>标签用于移除一个变量，可以指定这个变量的作用域，若未指定，则默认为变量第一次出现的作用域。

这个标签不是特别有用，不过可以用来确保JSP完成清理工作。

### 语法
```
<c:remove var="<string>" scope="<string>"/>
```

### 属性
- var:要移除的变量名称
	必需:是
    默认值:无

- scope:变量所属的作用域
	必需:否
    默认值:所有作用域

### 举例
```
<c:set var="salary" scope="session" value="${2000*2}"/>
<p>salary 变量值: <c:out value="${salary}"/></p>
<c:remove var="salary"/>
<p>删除 salary 变量后的值: <c:out value="${salary}"/></p>

salary 变量值: 4000

删除 salary 变量后的值:
```
