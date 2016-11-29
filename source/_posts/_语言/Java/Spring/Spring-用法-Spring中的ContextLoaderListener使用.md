作用：在启动Web容器时，自动装配Spring applicationContext.xml的配置信息。

如果在web.xml中不写任何参数配置信息，默认的路径是"/WEB-INF/applicationContext.xml，在WEB-INF目录下创建的xml文件的名称必须是applicationContext.xml。

如果是要自定义文件名可以在web.xml里加入contextConfigLocation这个context参数：
```
<context-param>  
    <param-name>contextConfigLocation</param-name>  
    <param-value>  
        /WEB-INF/classes/applicationContext-*.xml   
    </param-value>  
</context-param> 
```

IUploaddatafileManager uploadmanager = (IUploaddatafileManager) ContextLoaderListener.getCurrentWebApplicationContext().getBean("uploadManager");
