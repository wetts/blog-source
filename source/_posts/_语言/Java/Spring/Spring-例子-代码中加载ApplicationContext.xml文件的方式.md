## 一、利用ClassPathXmlApplicationContext,可以从classpath中读取XML文件
#### 1. 读取一个文件
```
ApplicationContext context = new ClassPathXmlApplicationContext("applicationContext.xml");
UserDao userDao = (UserDao)context.getBean("userDao");
```

#### 2. 读取多个文件
```
ClassPathXmlApplicationContext resource = new ClassPathXmlApplicationContext(new String[]{"applicationContext-ibatis-oracle.xml","applicationContext.xml","applicationContext-data-racle.xml"});
BeanFactory factory = resource; UserDao userDao = (UserDao) factory.getBean("userDao");
```

## 二、利用ClassPathResource,可以从classpath中读取XML文件
```
Resource cr = new ClassPathResource("applicationContext.xml");
BeanFactory bf=new XmlBeanFactory(cr);
UserDao userDao = (UserDao)bf.getBean("userDao");
```
## 三、利用XmlWebApplicationContext读取
```
XmlWebApplicationContext ctx = new XmlWebApplicationContext();
ctx.setConfigLocations(new String[] {"/WEB-INF/ applicationContext.xml");
ctx.setServletContext(pageContext.getServletContext());
ctx.refresh();
UserDao userDao = (UserDao ) ctx.getBean("userDao ");
```
## 四、利用FileSystemResource读取
```
Resource rs = new FileSystemResource("D:/tomcat/webapps/test/WEB-INF/classes/ applicationContext.xml");
BeanFactory factory = new XmlBeanFactory(rs);
UserDao userDao = (UserDao )factory.getBean("userDao");
```
注意:利用FileSystemResource，则配置文件必须放在project直接目录下，或者写明绝对路径，否则就会抛出找不到文件的异常
## 五、利用FileSystemXmlApplicationContext读取,可以指定XML定义文件的相对路径或者绝对路径来读取定义文件。
#### 1. String[]
```
path={"WebRoot/WEB-INF/applicationContext.xml","WebRoot/WEB-NF/applicationContext_task.xml"};
ApplicationContext context = new FileSystemXmlApplicationContext(path);
```
#### 2.
```
String path="WebRoot/WEB-INF/applicationContext*.xml";
ApplicationContext context = new FileSystemXmlApplicationContext(path);
```
#### 3.
```
ApplicationContext ctx = new FileSystemXmlApplicationContext("classpath:地址");
```
