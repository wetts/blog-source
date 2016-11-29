Ajax由于受到浏览器的限制，该方法不允许跨域通信。如果尝试从不同的域请求数据，会出现安全错误。

解决方法：
1. 在你的web中使用后端的语言，比如php、java去请求api接口拿到数据，然后给你web项目
2. header("Access-Control-Allow-Origin:*");
3. jsonp

---
## JSONP
#### Jsonp原理： 
首先在客户端注册一个callback, 然后把callback的名字传给服务器。

此时，服务器先生成 json 数据。

然后以 javascript 语法的方式，生成一个function , function 名字就是传递上来的参数 jsonp.

最后将 json 数据直接以入参的方式，放置到 function 中，这样就生成了一段 js 语法的文档，返回给客户端。

客户端浏览器，解析script标签，并执行返回的 javascript 文档，此时数据作为参数，传入到了客户端预先定义好的 callback 函数里.（动态执行回调函数）