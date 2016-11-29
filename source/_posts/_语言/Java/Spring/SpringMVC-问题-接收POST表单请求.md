前段时间遇到一个问题，在spring mvc 服务端接收post请求时，通过html 表单提交的时候，服务端能够接收到参数的值。但是使用httpclient4.3构造post请求，却无法接收到参数的值。

spring 代码：
```
@RequestMapping(value = "login.do", method = RequestMethod.POST)
@ResponseBody
public String login(String username, String password) throws Exception {
    return username + ":" + password;
}
```
表单代码：
```
<form action="http://localhost:8080/test/login.do" id="frm" method="post">
  name:<input type="text" name="username" id="username"/>   </br>
  psword:<input type="text" name="password" id="password"/>  </br>
  <input id="submit" type="submit" />
</form>
```
httpclient4.3发送post代码：
```
@Test
public void testMultipartPost() throws IOException {
    HttpPost httpPost = new HttpPost("http://localhost:8080/test/login.do");
    try {
        HttpClientBuilder httpClientBuilder = HttpClientBuilder.create();
        CloseableHttpClient httpClient = httpClientBuilder.build();
        RequestConfig config = RequestConfig.custom().setConnectTimeout(200000).setSocketTimeout(200000).build();
        httpPost.setConfig(config);
        MultipartEntityBuilder multipartEntityBuilder = MultipartEntityBuilder.create();
        multipartEntityBuilder.setCharset(Charset.forName("UTF-8"));
        multipartEntityBuilder.addTextBody("username", "taozi");
        multipartEntityBuilder.addTextBody("password", "123");
        HttpEntity httpEntity = multipartEntityBuilder.build();
        httpPost.setEntity(httpEntity);
        HttpResponse response = httpClient.execute(httpPost);
        System.out.println(EntityUtils.toString(response.getEntity()));
    } finally {
        httpPost.releaseConnection();
    }
}
```
一直在查找原因，为什么通过httpclient4.3构造的post请求，服务端无法接收到传输的参数。比较与html的差异，发现httpclient构造的请求使用的是multipart形式。而表单上传使用的是默认形式的编码```x-www-form-urlencoded```，所以表单能够成功。现在找到问题了，将httpclient的构造代码，改为```x-www-form-urlencoded```编码上传，
```
@Test
public void testUrlencodedPost() throws IOException {
    HttpPost httpPost = new HttpPost("http://localhost:8080/test/login.do");
    try {
        CloseableHttpClient client = HttpClients.createDefault();
        List<NameValuePair> params = new ArrayList<NameValuePair>();
        params.add(new BasicNameValuePair("username", "taozi"));
        params.add(new BasicNameValuePair("password", "123"));
        HttpEntity httpEntity = new UrlEncodedFormEntity(params, "UTF-8");
        httpPost.setEntity(httpEntity);
        CloseableHttpResponse response = client.execute(httpPost);
        System.out.println(EntityUtils.toString(response.getEntity()));
    } finally {
        httpPost.releaseConnection();
    }
}
```
现在服务端能够正常的接收到请求了，现在总结一下表单两种编码的形式

```
application/x-www-form-urlencoded
```
空格转换为 "+" 加号，特殊符号转换为 ASCII HEX 值

```
multipart/form-data
```
不对字符进行编码，使用二进制数据传输，一般用于上传文件，非文本的数据传输。

spring mvc如果要接收 multipart/form-data 传输的数据，应该在spring上下文配置
```
<bean id="multipartResolver" class="org.springframework.web.multipart.commons.CommonsMultipartResolver">       
</bean>
```
这样服务端就既可以接收multipart/form-data 传输的数据，也可以接收application/x-www-form-urlencoded传输的文本数据了。
