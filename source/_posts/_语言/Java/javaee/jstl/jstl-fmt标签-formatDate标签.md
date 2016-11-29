<fmt:formatDate>标签用于使用不同的方式格式化日期。

### 语法
```
<fmt:formatDate
  value="<string>"
  type="<string>"
  dateStyle="<string>"
  timeStyle="<string>"
  pattern="<string>"
  timeZone="<string>"
  var="<string>"
  scope="<string>"/>
```

### 属性
- value:要显示的日期
    必需:是
    默认值:无

- type:DATE, TIME, 或 BOTH
    必需:否
    默认值:date

- dateStyle:FULL, LONG, MEDIUM, SHORT, 或 DEFAULT
    必需:否
    默认值:default

- timeStyle:FULL, LONG, MEDIUM, SHORT, 或 DEFAULT
    必需:否
    默认值:default

- pattern:自定义格式模式
    必需:否
    默认值:无

- timeZone:显示日期的时区
    必需:否
    默认值:默认时区

- var:存储格式化日期的变量名
    必需:否
    默认值:显示在页面

- scope:存储格式化日志变量的范围
    必需:否
    默认值:页面

<fmt:formatDate> 标签格式模式
- G
    时代标志
    AD
- y
    不包含纪元的年份。如果不包含纪元的年份小于 10，则显示不具有前导零的年份。
    2002
- M
    月份数字。一位数的月份没有前导零。
    April & 04
- d
    月中的某一天。一位数的日期没有前导零。
    20
- h
    12 小时制的小时。一位数的小时数没有前导零。
    12
- H
    24 小时制的小时。一位数的小时数没有前导零。
    0
- m
    分钟。一位数的分钟数没有前导零。
    45
- s
    秒。一位数的秒数没有前导零。
    52
- S
    毫秒
    970
- E
    周几
    Tuesday
- D
    一年中的第几天
    180
- F
    一个月中的第几个周几
    2 (一个月中的第二个星期三)
- w
    一年中的第几周r
    27
- W
    一个月中的第几周
    2
- a
    a.m./p.m. 指示符
    PM
- k
    小时(12 小时制的小时)
    24
- K
    小时(24 小时制的小时)
    0
- z
    时区
    中部标准时间
- '
    转义文本
- ''
    单引号

### 举例
```
<c:set var="now" value="<%=new java.util.Date()%>" />

<p>日期格式化 (1): <fmt:formatDate type="time" value="${now}" /></p>
<p>日期格式化 (2): <fmt:formatDate type="date" value="${now}" /></p>
<p>日期格式化 (3): <fmt:formatDate type="both" value="${now}" /></p>
<p>日期格式化 (4): <fmt:formatDate type="both" dateStyle="short" timeStyle="short" value="${now}" /></p>
<p>日期格式化 (5): <fmt:formatDate type="both" dateStyle="medium" timeStyle="medium" value="${now}" /></p>
<p>日期格式化 (6): <fmt:formatDate type="both" dateStyle="long" timeStyle="long" value="${now}" /></p>
<p>日期格式化 (7): <fmt:formatDate pattern="yyyy-MM-dd" value="${now}" /></p>

日期格式化:

日期格式化 (1): 11:19:43

日期格式化 (2): 2016-6-26

日期格式化 (3): 2016-6-26 11:19:43

日期格式化 (4): 16-6-26 上午11:19

日期格式化 (5): 2016-6-26 11:19:43

日期格式化 (6): 2016年6月26日 上午11时19分43秒

日期格式化 (7): 2016-06-26
```
