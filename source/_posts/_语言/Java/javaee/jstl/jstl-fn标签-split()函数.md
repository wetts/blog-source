fn:split()函数将一个字符串用指定的分隔符分裂为一个子串数组。

### 语法
```
${fn:split(<带分隔符的字符串>, <分隔符>)}
```

### 举例
```
<c:set var="string1" value="www runoob com"/>
<c:set var="string2" value="${fn:split(string1, ' ')}" />
<c:set var="string3" value="${fn:join(string2, '-')}" />

<p>string3 字符串 : ${string3}</p>

<c:set var="string4" value="${fn:split(string3, '-')}" />
<c:set var="string5" value="${fn:join(string4, ' ')}" />

<p>string5 字符串: ${string5}</p>

string3 字符串 : www-runoob-com

string5 字符串: www runoob com
```
