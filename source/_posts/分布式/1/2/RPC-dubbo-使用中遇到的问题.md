### java.net.SocketException: Can't assign requested address

```虚拟机参数：-Djava.net.preferIPv4Stack=true```

### dubbo中接口provider和consumer的包路径必须一致

### springMVC dubbo注解无效，service层返回空指针
出现空指针的原因是：spring mvc扫描的时候根本无法识别@Reference ，同一方面，dubbo的扫描也无法识别Spring @Controller ,所以两个扫描的顺序要排列好，  

如果先扫了controller，这时候把控制器都实例化好了，再扫dubbo的服务，就会出现空指针。   
