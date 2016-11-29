在扫描完包初始化数据之后，我们可以通过getBean获取类的实例

#### 通过getBean获取类的实例
```
Annotation annotation = ac.getBean("annotation", Annotation.class);
```

#### 到之前初始化数据中去获取该类的实例
不考虑该类没有定义的情况。

如果该类设置lazy-init为true，则会根据该类对应的BeanDefinition的信息实例化该类，并且存到一个map中；如果lazy-init为false，则在数据初始化的时候已经将该类实例化，并且存到一个map中。
