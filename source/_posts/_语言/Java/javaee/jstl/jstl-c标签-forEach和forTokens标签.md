这些标签封装了Java中的for，while，do-while循环。

相比而言，<c:forEach>标签是更加通用的标签，因为它迭代一个集合中的对象。

<c:forTokens>标签通过指定分隔符将字符串分隔为一个数组然后迭代它们。

### 语法
```
<c:forEach
    items="<object>"
    begin="<int>"
    end="<int>"
    step="<int>"
    var="<string>"
    varStatus="<string>">

<c:forTokens
    items="<string>"
    delims="<string>"
    begin="<int>"
    end="<int>"
    step="<int>"
    var="<string>"
    varStatus="<string>">
```

### 属性
<c:forEach>标签有如下属性：
- items:要被循环的信息
    必需:否
    默认值:无

- begin:开始的元素（0=第一个元素，1=第二个元素）(循环从哪儿开始)
    必需:否
    默认值:0

- end:最后一个元素（0=第一个元素，1=第二个元素）(循环到哪儿结束)
    必需:否
    默认值:Last element

- step:每一次迭代的步长
    必需:否
    默认值:1

- var:代表当前条目的变量名称
    必需:否
    默认值:无

- varStatus:代表循环状态的变量名称(每个对象的状态)
    必需:否
    默认值:无
    index       getIndex()               当前这次迭代从 0 开始的迭代索引
    count       getCount()             当前这次迭代从 1 开始的迭代计数
    first          isFirst()                  用来表明当前这轮迭代是否为第一次迭代的标志
    last          isLast()                  用来表明当前这轮迭代是否为最后一次迭代的标志
    begin      getBegin()             begin 属性值
    end         getEnd()                 end 属性值
    step        getStep()                step 属性值


<c:forTokens>标签与<c:forEach>标签有相似的属性，不过<c:forTokens>还有另一个属性：

- delims:分隔符
    必需:是
    默认值:无

### 举例
```
<c:forEach var="i" begin="1" end="5">
   Item <c:out value="${i}"/><p>
</c:forEach>

Item 1
Item 2
Item 3
Item 4
Item 5

<c:forTokens items="google,runoob,taobao" delims="," var="name">
   <c:out value="${name}"/><p>
</c:forTokens>

google
runoob
taobao
```
