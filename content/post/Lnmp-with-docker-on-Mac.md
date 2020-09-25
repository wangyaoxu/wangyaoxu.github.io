+++
title = "Lnmp-with-docker-on-Mac"
date = 2020-09-09T00:00:00+08:00
description = "Github Pages with hugo"
tags = ["github", "hugo"]
+++

Lnmp-with-docker-on-Mac

<!--more-->


```bash

$ docker images
$ docker pull ubuntu	# 拉取镜像
$ docker run -tid -p 8080:80 -p 3309:3306 -v ~/www:/var/www/html --name mylnmp ubuntu /bin/bash	# 端口映射、目录映射

$ docker exec -ti mylnmp /bin/bash	# 进入容器

# 进入容器后

$ apt update 
$ apt upgrade
$ apt -y install nginx php-fpm mysql-client mysql-server vim

# 配置 PHP-FPM

$ vim /etc/php/7.4/fpm/pool.d/www.conf


# cp /run/php/php7.4-fpm.sock


$ vim /etc/nginx/sites-enabled/default


# 替换 fastcgi_pass 

# 修改后的

        # pass PHP scripts to FastCGI server
        #
        location ~ \.php$ {
               include snippets/fastcgi-php.conf;
        #
        #       # With php-fpm (or other unix sockets):
                fastcgi_pass unix:/run/php/php7.4-fpm.sock;
        #       # With php-cgi (or other tcp sockets):
        #       fastcgi_pass 127.0.0.1:9000;
        }
### 配置 MySQL

# 通过 mysql_secure_installation 完成设置
# 8.0 以后执行

$ mysql > set global validate_password.policy=0;
$ mysql > set global validate_password.length=4;


$ mysql >  grant all on *.* to 'root'@'localhost';  	# 授权

$ mysql >  update user set user.host='%' where user.user='root';	


# 服务端设置
$ vim /etc/mysql/mysql.conf.d/mysqld.cnf

# 开启外部链接

bind-address            = 127.0.0.1

-> 

# bind-address            = 127.0.0.1

# 运行设置

$ usermod -d /var/lib/mysql mysql
$ chown -R mysql:mysql /var/lib/mysql






```


### Links
- http://chungwei.github.io/2016/04/25/blog-hugo-github/