### 1. 在/etc/init.d/目录下创建脚本
```
vi  /etc/init.d/php-fpm
```

### 2. 更改脚本权限
```
chmod 775 /etc/init.d/php-fpm
```

### 3. 编写脚本内容
```
#!/bin/sh
#
# php-fpm - this script starts and stops the php-fpm daemin
#
# chkconfig: - 85 15
# processname: php-fpm
# config:      /usr/local/php/etc/php-fpm.conf

set -e

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DESC="php-fpm daemon"
NAME=php-fpm
DAEMON=/usr/local/php/sbin/$NAME     //这里设成自己的目录
CONFIGFILE=/usr/local/php/etc/php-fpm.conf   //这里设成自己的目录
PIDFILE=/usr/local/php/var/run/$NAME.pid   //这里设成自己的目录
SCRIPTNAME=/etc/init.d/$NAME   //这里设成自己的目录

# If the daemon file is not found, terminate the script.
test -x $DAEMON || exit 0

d_start(){
   $DAEMON -y $CONFIGFILE || echo -n " already running"
}

d_stop(){
   kill -QUIT `cat $PIDFILE` || echo -n " no running"
}

d_reload(){
   kill -HUP `cat $PIDFILE` || echo -n " could not reload"
}

case "$1" in
   start)
       echo -n "Starting $DESC: $NAME"
       d_start
       echo "."
       ;;
   stop)
       echo -n "Stopping $DESC: $NAME"
       d_stop
       echo "."
       ;;
   reload)
       echo -n "Reloading $DESC configuration..."
       d_reload
       echo "Reloaded."
       ;;
   restart)
       echo -n "Restarting $DESC: $NAME"
       d_stop
       # Sleep for two seconds before starting again, this should give the nginx daemon some time to perform a graceful stop
       sleep 2
       d_start
       echo "."
       ;;
   *)
       echo "Usage: $SCRIPTNAME {start|stop|restart|force-reload)" >&2
       exit 3
       ;;
esac
exit 0`
```

### 4. 设置开机启动
```
chkconfig php-fpm on
```