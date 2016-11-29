fn:length()函数返回字符串长度或集合中元素的数量。

### 语法
```
${fn:length(collection | string)}
```

### 举例
```
<c:set var="string1" value="This is first String."/>
<c:set var="string2" value="This is second String." />

<p>字符串长度 (1) : ${fn:length(string1)}</p>
<p>字符串长度 (2) : ${fn:length(string2)}</p>

字符串长度 (1) : 21

字符串长度 (2) : 22
```
