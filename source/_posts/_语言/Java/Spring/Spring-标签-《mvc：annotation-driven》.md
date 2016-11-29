以下为spring mvc 3.1中annotation-driven所支持的全部配置
```
<mvc:annotation-driven  message-codes-resolver ="bean ref" validator="" conversion-service="">
    <mvc:return-value-handlers>
        <bean></bean>
    </mvc:return-value-handlers>
    
    <mvc:argument-resolvers>
    </mvc:argument-resolvers>
    
    <mvc:message-converters>
    </mvc:message-converters>
</mvc:annotation-driven>
```

### return-value-handlers 

允许注册实现了HandlerMethodReturnValueHandler接口的bean，来对handler method的特定的返回类型做处理HandlerMethodReturnValueHandler接口中定义了两个方法：

- supportsReturnType 方法用来确定此实现类是否支持对应返回类型。
- handleReturnValue 则用来处理具体的返回类型

例如以下的handlerMethod 
```
@RequestMapping("/testReturnHandlers")
public User testHandlerReturnMethod(){
    User u  = new User();
    u.setUserName("test");
    return u;
}
```

所返回的类型为一个pojo，正常情况下spring mvc无法解析，将转由DefaultRequestToViewNameTranslator 解析出一个缺省的view name，转到testReturnHandlers.jsp
我们增加以下配置
```
<mvc:annotation-driven validator="validator">
    <mvc:return-value-handlers> 
        <bean class="net.zhepu.web.handlers.returnHandler.UserHandlers"></bean> 
    </mvc:return-value-handlers>
</mvc:annotation-driven>    
```

实现类
```
public class UserHandlers implements HandlerMethodReturnValueHandler {
    Logger logger = LoggerFactory.getLogger(this.getClass());
    @Override
    public boolean supportsReturnType(MethodParameter returnType) {
        Class<?> type = returnType.getParameterType();
        if(User.class.equals(type))
        {
            return true;
        }
        return false;
    }

    @Override
    public void handleReturnValue(Object returnValue,
            MethodParameter returnType, ModelAndViewContainer mavContainer,
            NativeWebRequest webRequest) throws Exception {
        logger.info("handler  for return type users ");
        mavContainer.setViewName("helloworld");
    }
}    
```

此时再访问 http://localhost:8080/springmvc/testReturnHandlers ，将交由 UserHandlers来处理返回类型为User的返回值

### argument-resolvers

允许注册实现了WebArgumentResolver接口的bean，来对handlerMethod中的用户自定义的参数或annotation进行解析 
```
<mvc:annotation-driven validator="validator">
    <mvc:argument-resolvers>
        <bean class="net.zhepu.web.handlers.argumentHandler.MyCustomerWebArgumentHandler" />
    </mvc:argument-resolvers>
</mvc:annotation-driven>
```

java代码如下
```
public class MyCustomerWebArgumentHandler implements WebArgumentResolver {
    @Override
    public Object resolveArgument(MethodParameter methodParameter,
            NativeWebRequest webRequest) throws Exception {
        if (methodParameter.getParameterType().equals(MyArgument.class)) {
            MyArgument argu = new MyArgument();
            argu.setArgumentName("winzip");
            argu.setArgumentValue("123456");
            return argu;
        }
        return UNRESOLVED;
    }
}
```

这里我们定义了一个 customer webArgumentHandler，当handler method中参数类型为 MyArgument时生成对参数的类型绑定操作

注意新注册的webArgumentHandler的优先级最低，即如果系统缺省注册的ArgumentHandler已经可以解析对应的参数类型时，就不会再调用到新注册的customer ArgumentHandler了

### message-converters 
允许注册实现了HttpMessageConverter接口的bean，来对requestbody 或responsebody中的数据进行解析

例如

假设我们使用text/plain格式发送一串字符串来表示User对象，各个属性值使用”|”来分隔。

例如 winzip|123456|13818888888，期望转为user对象，各属性内容为user.username = winzip,user.password=123456;user.mobileNO = 13818888888 

以下代码中supports表示此httpmessageConverter实现类针对User类进行解析。

构造函数中调用super(new MediaType("text", "plain"));以表示支持 text/plain格式的输入
```
public class MyCustomerMessageConverter extends AbstractHttpMessageConverter<Object> {
    @Override
    protected boolean supports(Class<?> clazz) {
        if (clazz.equals(User.class)) {
            return true;
        }
        return false;
    }

    public MyCustomerMessageConverter() {
        super(new MediaType("text", "plain"));
    }

    @Override
    protected Object readInternal(Class<? extends Object> clazz,
            HttpInputMessage inputMessage) throws IOException,
            HttpMessageNotReadableException {
        Charset charset;
        MediaType contentType = inputMessage.getHeaders().getContentType();
        if (contentType != null && contentType.getCharSet() != null) {
            charset = contentType.getCharSet();
        } else {
            charset = Charset.forName("UTF-8");
        }
        String input = FileCopyUtils.copyToString(new InputStreamReader(
                inputMessage.getBody(), charset));
        logger.info(input);
        String[] s = input.split("\\|");
        User u = new User();
        u.setUserName(s[0]);
        u.setPassword(s[1]);
        u.setMobileNO(s[2]);
        return u;
    }

    @Override
    protected void writeInternal(Object t, HttpOutputMessage outputMessage)
            throws IOException, HttpMessageNotWritableException {

    }
}
```

修改servlet context xml配置文件，增加message-converters的相应配置如下
```
<mvc:message-converters>
    <bean class="net.zhepu.web.handlers.messageConverterHandler.MyCustomerMessageConverter"></bean>
</mvc:message-converters>
```

