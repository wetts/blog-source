1. git clone https://github.com/phpredis/phpredis.git
2. cd phpredis
3. git checkout php7 #拉取php7分支
4. /web/php/bin/phpize #用phpize生成configure配置文件
5. ./configure --with-php-config=/web/php/bin/php-config  #配置
6. make && make install
7. extension=redis.so #php.ini添加。