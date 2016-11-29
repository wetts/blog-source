自php5.3.3开始，php源码中包含了php-fpm，不需要单独通过补丁的方式安装php-fpm，在源码安装的时候直接 configure 中增加参数 –enable-fpm 即可。

所以启动、关闭和重新加载的方式和以前不同，需要使用信号控制：

php-fpm master 进程可以理解一下信号：

- SIGINT, SIGTERM 立刻终止
- SIGQUIT 平滑终止
- SIGUSR1 重新打开日志文件
- SIGUSR2 平滑重载所有worker进程并重新载入配置和二进制模块

例如：关闭php-fpm
```
kill -SIGINT `cat /usr/local/php/var/run/php-fpm.pid`
```

php-fpm 重启
```
kill -SIGUSR2 `cat /usr/local/php/var/run/php-fpm.pid`
```

注意：/usr/local/php/var/run/php-fpm.pid 指存储master进程号的文件，这里是默认地址，在配置中可以修改，另外可以使用ps命令找到master的进程号，然后使用 kill 信号 进程号 的方式。