配置nginx.conf
```
server{
	listen       8081;
	#server_name  api.aiwei365.com;
	root /home/www;
	index index.php index.html index.htm;
	access_log /root/www/log/api.access.log main buffer=16k;
			   
	location / {
           # index  index.php index.html ;
		    try_files $uri $uri/ /index.php$is_args$args;
        }
	 location ~ .*\.(php|php5)?$ {
	    fastcgi_pass  127.0.0.1:9000;
        fastcgi_index index.php;
	    fastcgi_param  SCRIPT_FILENAME  /home/www$fastcgi_script_name;
        include        fastcgi_params;
        }
	
}
```