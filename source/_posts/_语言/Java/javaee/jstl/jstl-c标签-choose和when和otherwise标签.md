<c:choose>标签与Java switch语句的功能一样，用于在众多选项中做出选择。

switch语句中有case，而<c:choose>标签中对应有<c:when>，switch语句中有default，而<c:choose>标签中有<c:otherwise>。

### 语法
```
<c:choose>
    <c:when test="<boolean>"/>
        ...
    </c:when>
    <c:when test="<boolean>"/>
        ...
    </c:when>
    ...
    ...
    <c:otherwise>
        ...
    </c:otherwise>
</c:choose>
```

### 属性
<c:choose>标签没有属性。

<c:when>标签只有一个属性，在下表中有给出。

<c:otherwise>标签没有属性。

- test:条件
    必需:是
    默认值:无

### 举例
```
<c:set var="salary" scope="session" value="${2000*2}"/>
<p>你的工资为 : <c:out value="${salary}"/></p>
<c:choose>
    <c:when test="${salary <= 0}">
       太惨了。
    </c:when>
    <c:when test="${salary > 1000}">
       不错的薪水，还能生活。
    </c:when>
    <c:otherwise>
        什么都没有。
    </c:otherwise>
</c:choose>

你的工资为 : 4000

不错的薪水，还能生活。
```
