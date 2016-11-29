fn:trim()函数将字符串两端的空白符移除。

### 语法
```
${fn.trim(<string>)}
```

### 举例
```
<c:set var="string1" value="I am from runoob         "/>
<p>string1 长度 : ${fn:length(string1)}</p>

<c:set var="string2" value="${fn:trim(string1)}" />
<p>string2 长度 : ${fn:length(string2)}</p>
<p>字符串为 : ${string2}</p>

string1 长度 : 25

string2 长度 : 16

字符串为 : I am from runoob
```
