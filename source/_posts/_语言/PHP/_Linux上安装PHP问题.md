## libtool: link: `ext/date/php_date.lo' is not a valid libtool object
./configure 后，直接make可能会出现libtool: link: `ext/date/php_date.lo' is not a valid libtool object 的错误。

make clean 一下然后再make，即可。

## undefined reference to `libiconv'
```
ext/gd/libgd/.libs/gdkanji.o: In function `do_convert':
/root/php-5.2.12/ext/gd/libgd/gdkanji.c:350: undefined reference to `libiconv_open'
/root/php-5.2.12/ext/gd/libgd/gdkanji.c:365: undefined reference to `libiconv'
/root/php-5.2.12/ext/gd/libgd/gdkanji.c:381: undefined reference to `libiconv_close'
ext/iconv/.libs/iconv.o: In function `_php_iconv_strlen':
/root/php-5.2.12/ext/iconv/iconv.c:603: undefined reference to `libiconv_open'
/root/php-5.2.12/ext/iconv/iconv.c:626: undefined reference to `libiconv'
/root/php-5.2.12/ext/iconv/iconv.c:660: undefined reference to `libiconv_close'
ext/iconv/.libs/iconv.o: In function `php_iconv_string':
/root/php-5.2.12/ext/iconv/iconv.c:441: undefined reference to `libiconv_open'
/root/php-5.2.12/ext/iconv/iconv.c:453: undefined reference to `libiconv'
/root/php-5.2.12/ext/iconv/iconv.c:467: undefined reference to `libiconv'
/root/php-5.2.12/ext/iconv/iconv.c:478: undefined reference to `libiconv_close'
ext/iconv/.libs/iconv.o: In function `_php_iconv_strpos':
/root/php-5.2.12/ext/iconv/iconv.c:851: undefined reference to `libiconv_open'
/root/php-5.2.12/ext/iconv/iconv.c:879: undefined reference to `libiconv'
/root/php-5.2.12/ext/iconv/iconv.c:993: undefined reference to `libiconv_close'
ext/iconv/.libs/iconv.o: In function `_php_iconv_appendl':
/root/php-5.2.12/ext/iconv/iconv.c:348: undefined reference to `libiconv'
/root/php-5.2.12/ext/iconv/iconv.c:385: undefined reference to `libiconv'
ext/iconv/.libs/iconv.o: In function `_php_iconv_substr':
/root/php-5.2.12/ext/iconv/iconv.c:723: undefined reference to `libiconv_open'
/root/php-5.2.12/ext/iconv/iconv.c:747: undefined reference to `libiconv'
/root/php-5.2.12/ext/iconv/iconv.c:802: undefined reference to `libiconv_close'
/root/php-5.2.12/ext/iconv/iconv.c:806: undefined reference to `libiconv_close'
/root/php-5.2.12/ext/iconv/iconv.c:755: undefined reference to `libiconv_open'
ext/iconv/.libs/iconv.o: In function `_php_iconv_mime_decode':
/root/php-5.2.12/ext/iconv/iconv.c:1354: undefined reference to `libiconv_open'
/root/php-5.2.12/ext/iconv/iconv.c:1465: undefined reference to `libiconv_close'
/root/php-5.2.12/ext/iconv/iconv.c:1468: undefined reference to `libiconv_open'
/root/php-5.2.12/ext/iconv/iconv.c:1823: undefined reference to `libiconv_close'
/root/php-5.2.12/ext/iconv/iconv.c:1826: undefined reference to `libiconv_close'
ext/iconv/.libs/iconv.o: In function `php_iconv_stream_filter_dtor':
/root/php-5.2.12/ext/iconv/iconv.c:2465: undefined reference to `libiconv_close'
ext/iconv/.libs/iconv.o: In function `_php_iconv_mime_encode':
/root/php-5.2.12/ext/iconv/iconv.c:1043: undefined reference to `libiconv_open'
/root/php-5.2.12/ext/iconv/iconv.c:1057: undefined reference to `libiconv_open'
/root/php-5.2.12/ext/iconv/iconv.c:1316: undefined reference to `libiconv_close'
/root/php-5.2.12/ext/iconv/iconv.c:1319: undefined reference to `libiconv_close'
/root/php-5.2.12/ext/iconv/iconv.c:1176: undefined reference to `libiconv'
/root/php-5.2.12/ext/iconv/iconv.c:1128: undefined reference to `libiconv'
/root/php-5.2.12/ext/iconv/iconv.c:1160: undefined reference to `libiconv'
/root/php-5.2.12/ext/iconv/iconv.c:1319: undefined reference to `libiconv_close'
/root/php-5.2.12/ext/iconv/iconv.c:1228: undefined reference to `libiconv'
/root/php-5.2.12/ext/iconv/iconv.c:1259: undefined reference to `libiconv'
/root/php-5.2.12/ext/iconv/iconv.c:1303: undefined reference to `libiconv'
ext/iconv/.libs/iconv.o: In function `php_iconv_stream_filter_append_bucket':
/root/php-5.2.12/ext/iconv/iconv.c:2615: undefined reference to `libiconv'
/root/php-5.2.12/ext/iconv/iconv.c:2615: undefined reference to `libiconv'
ext/iconv/.libs/iconv.o:/root/php-5.2.12/ext/iconv/iconv.c:2537: more undefined references to `libiconv' follow
ext/iconv/.libs/iconv.o: In function `php_iconv_stream_filter_ctor':
/root/php-5.2.12/ext/iconv/iconv.c:2491: undefined reference to `libiconv_open'
ext/xmlrpc/libxmlrpc/.libs/encodings.o: In function `convert':
/root/php-5.2.12/ext/xmlrpc/libxmlrpc/encodings.c:73: undefined reference to `libiconv_open'
/root/php-5.2.12/ext/xmlrpc/libxmlrpc/encodings.c:81: undefined reference to `libiconv'
/root/php-5.2.12/ext/xmlrpc/libxmlrpc/encodings.c:101: undefined reference to `libiconv_close'
collect2: ld returned 1 exit status
make: *** [sapi/cli/php] ?.. 1
```

处理方法：
```
vi Makefile
找到下面这行：

EXTRA_LIBS = -lcrypt ...

在最后添加-liconv
```
