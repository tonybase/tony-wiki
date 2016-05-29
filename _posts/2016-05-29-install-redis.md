---
layout: inner
position: right
title: 'install redis'
date: 2016-05-29 19:33:00
categories: development
tags: redis
featured_image: ''
project_link: ''
button_icon: 'github'
button_text: 'Visit Project'
lead_text: 'redis'
---

# install redis

---

## install dirs

	shell> mkdir /data/files
	shell> mkdir /data/apps/redis

## download

	shell> cd /data/files
	shell> wget http://download.redis.io/releases/redis-3.2.0.tar.gz

	http://redis.io/download

## install redis

	shell> tar -zxvf redis-3.2.0.tar.gz
	shell> mv redis-3.2.0 /data/apps/redis

## service script
	
	#!/bin/sh
	### BEGIN INIT INFO
	# Provides: redis
	# Required-Start:    $local_fs $syslog $remote_fs
	# Required-Stop:     $local_fs $syslog $remote_fs
	# Default-Start:     2 3 4 5
	# Default-Stop:      0 1 6
	# Short-Description: Start redis
	### END INIT INFO

	DAEMON_PATH=/data/apps/redis/src
	DAEMON_NAME=redis

	export JAVA_HOME=/data/apps/jdk8
	export PATH=$JAVA_HOME/bin:$PATH
	PATH=$PATH:$DAEMON_PATH

	# See how we were called.
	case "$1" in
	  start)
	        # Start daemon.
	        echo "Starting $DAEMON_NAME";
	        nohup $DAEMON_PATH/redis-server > /data/logs/redis/nohup.log 2>&1 &
	        echo "Done.";
	        exit 0
	        ;;
	  stop)
	        # Stop daemons.
	        echo "Shutting down $DAEMON_NAME";
	        pid=`ps ax | grep -i 'redis' | grep -v grep | awk '{print $1}'`
	        if [ -n "$pid" ]
	          then
	          kill -9 $pid
	        else
	          echo "$DAEMON_NAME was not Running"
	        fi
	        exit 0
	        ;;
	  restart)
	        $0 stop
	        sleep 2
	        $0 start
	        exit 0
	        ;;
	  status)
	        pid=`ps ax | grep -i 'redis' | grep -v grep | awk '{print $1}'`
	        if [ -n "$pid" ]
	          then
	          echo "$DAEMON_NAME is Running as PID: $pid"
	        else
	          echo "$DAEMON_NAME is not Running"
	        fi
	        exit 0
	        ;;
	  *)
	        echo "Usage: $0 {start|stop|restart|status}"
	        exit 1
	esac

## up service
	
	shell> vi /etc/init.d/redis            # save script
	shell> /etc/init.d/redis start         # up service
	shell> update-rc.d redis defaults 100  # auto start & priority 100

## about
	
	http://redis.io/