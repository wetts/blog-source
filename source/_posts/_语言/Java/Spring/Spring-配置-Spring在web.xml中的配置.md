Spring的配置文件applicationcontext.xml是通过spring提供的加载机制，自动加载的容器中去，在web项目中，配置文件加载到web容器中进行解析，目前，spring提供了两种加载器，以供web容器的加载：一种是ContextLoaderListener，另一种是ContextLoaderServlet。这两种在功能上完全相同，只是一种是基于Servlet2.3版本中新引入的Listener接口实现，而另一种是基于Servlet接口实现，以下是这两种加载器在web.xml中的时机配置应用：

第一种：
```
<listener>
  <listener-class>org.springframework.context.ContextLoaderListener</listener-class>
</listener>
```
另一种：
```
<servlet>
  <servlet-name>context</servlet-name>
  <servlet-class>org.springframework.context.ContextLoaderServlet</servlet-class>
  <load-on-startup>1</load-on-startup>
</servlet>
```
通过上面的配置，web容器会自动加载applicationcontext.xml初始化。

如果需要指定配置文件的位置，可通过context-param加以指定：
```
<context-param>
  <param-name>contextConfigLocation</param-name>
  <param-value>/WEB-INF/myApplicationContext.xml</param-value>
</context-param>
```
之后，可以通过WebApplicationContextUtils.getWebApplicationContext方法在web应用中获取applicationcontext的引用。
