# mac 安装 php 的 mcrypt 扩展步骤以及注意事项

1. 首先安装 libmcrypt
	- cd ~/Downloads/mcrypt-2.5.8
	- ./configure --disable-posix-threads --enable-static
	- make
	- sudo make install
	
	> 安装 xcode 就可以使用 make 命令
	
2. 安装 php 源码中的 mcrypt 扩展
	- cd ~/Downloads/php-5.5.14/ext/mcrypt
	- phpize
	- ./configure
	- make
	- cd modules
	- sudo cp mcrypt.so /usr/lib/php/extensions/no-debug-non-zts-20121212/
	
	> phpize 可能会出现如下错误
	>> grep: /usr/include/php/main/php.h: No such file or directory
grep: /usr/include/php/Zend/zend_modules.h: No such file or directory
grep: /usr/include/php/Zend/zend_extensions.h: No such file or directory
Configuring for:
PHP Api Version:
Zend Module Api No:
Zend Extension Api No:
Cannot find autoconf. Please check your autoconf installation and the
$PHP_AUTOCONF environment variable. Then, rerun this script.
	
	> sudo ln -s /Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX10.10.sdk/usr/include /usr/include 可以解决
	>> 但是此命令可能提示权限不够	
	>> 重启 Mac, 按住 command+R, 进入 recovery 模式。选择打开 Utilities 下的终端，输入：csrutil disable 并回车，然后正常重启 Mac 即可
	
	> 如果 make 出现如下错误
	>> 安装 autoconf 即可
	
3. 修改 php.ini
	> sudo vi /etc/php.ini	
	> extension=/usr/lib/php/extensions/no-debug-non-zts-20121212/mcrypt.so