<c:redirect>标签通过自动重写URL来将浏览器重定向至一个新的URL，它提供内容相关的URL，并且支持c:param标签。

### 语法
```
<c:redirect url="<string>" context="<string>"/>
```

### 属性
- url:目标URL
    必需:是
    默认值:无

- context	紧接着一个本地网络应用程序的名称
    必需:否
    默认值:当前应用程序

### 举例
```
<c:redirect url="http://www.runoob.com"/>

浏览器打开以上页面将跳转至 http://www.runoob.com。
```
