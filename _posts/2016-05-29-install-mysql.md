---
layout: inner
position: right
title: 'install mysql'
date: 2016-05-29 19:34:00
categories: development
tags: mysql
featured_image: ''
project_link: ''
button_icon: 'github'
button_text: 'Visit Project'
lead_text: 'mysql'
---

# install mysql

---

## dirs

	/data
	/data/apps
	/data/apps/mysql
	/data/files
	/data/logs

## init dirs

	shell> mkdir /data/apps
	shell> mkdir /data/files
	shell> mkdir /data/logs/mysql

## download mysql

	shell> cd /data/files
	shell> wget http://cdn.mysql.com//Downloads/MySQL-5.7/mysql-5.7.12-linux-glibc2.5-x86_64.tar.gz
	shell> tar -zxvf mysql-5.7.12-linux-glibc2.5-x86_64.tar.gz
	shell> mv mysql-5.7.12-linux-glibc2.5-x86_64 /data/apps/mysql

## install mysql

	shell> cd /data/apps/mysql
	shell> groupadd mysql
	shell> useradd -r -g mysql -s /bin/false mysql
	shell> mkdir mysql-files
	shell> chmod 750 mysql-files
	shell> chown -R mysql .
	shell> chgrp -R mysql .
	shell> bin/mysqld --initialize-insecure --user=mysql
	shell> bin/mysql_ssl_rsa_setup
	shell> chown -R root .
	shell> chown -R mysql data mysql-files

## auto start script

	shell> cp support-files/mysql.server /etc/init.d/mysql
	shell> update-rc.d mysql defaults
	shell> /etc/init.d/mysql start

## login mysql, passowrd is empty.

	shell> mysql -u root
	mysql> ALTER USER 'root'@'localhost' IDENTIFIED BY 'chen'; # set Password

## create user and remote access
	
	CREATE USER 'test'@'%' IDENTIFIED BY 'tony';
	GRANT ALL PRIVILEGES ON *.* TO 'test'@'%' WITH GRANT OPTION;

## about

	http://dev.mysql.com/doc/refman/5.7/en/binary-installation.html