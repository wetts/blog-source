fn:substring()函数返回字符串中指定开始和结束索引的子串。

### 语法
```
${fn:substring(<string>, <beginIndex>, <endIndex>)}
```

### 举例
```
<c:set var="string1" value="This is first String."/>
<c:set var="string2" value="${fn:substring(string1, 5, 15)}" />
<p>生成的子字符串为 : ${string2}</p>

生成的子字符串为 : is first S
```
