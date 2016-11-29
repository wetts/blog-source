#### 1> 下载
```
wget  http://cn2.php.net/distributions/php-7.0.4.tar.gz
```

#### 2> 解压
```
tar zxvf php-7.0.4.tar.gz
cd php-7.0.4
```

#### 3> 设置配置
```
./configure \
--prefix=/usr/local/php7 \
--exec-prefix=/usr/local/php7 \
--with-config-file-path=/usr/local/php7/etc \
 --with-curl \
 --with-freetype-dir \
 --with-gd \
 --with-gettext \
 --with-iconv-dir \
 --with-kerberos \
 --with-libdir=lib64 \
 --with-libxml-dir \
 --with-mysqli \
 --with-openssl \
 --with-pcre-regex \
 --with-pdo-mysql \
 --with-pdo-sqlite \
 --with-pear \
 --with-png-dir \
 --with-xmlrpc \
 --with-xsl \
 --with-zlib \
--with-zlib-dir \
--with-mhash \
--with-mcrypt \
--with-openssl-dir \
--with-jpeg-dir \
--enable-gd-jis-conv \
 --enable-fpm \
 --enable-bcmath \
 --enable-libxml \
 --enable-inline-optimization \
 --enable-gd-native-ttf \
 --enable-mbregex \
 --enable-mbstring \
 --enable-opcache \
 --enable-pcntl \
 --enable-shmop \
 --enable-soap \
 --enable-sockets \
 --enable-sysvsem \
 --enable-xml \
 --enable-zip
 ```
 
#### 4> 编译安装
```
make &&  make install
```