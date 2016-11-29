# 关于在spring  容器初始化 bean 和销毁前所做的操作定义方式有三种：
1. 通过@PostConstruct 和 @PreDestroy 方法实现初始化和销毁bean之前进行的操作
2. 通过 在xml中定义init-method 和 destory-method方法
3. 通过bean实现InitializingBean和 DisposableBean接口

例子查看test/java/com/wetts/spring/init_destroy