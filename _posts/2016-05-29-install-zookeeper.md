---
layout: inner
position: right
title: 'install zookeeper'
date: 2016-05-29 19:31:00
categories: development
tags: zookeeper
featured_image: ''
project_link: ''
button_icon: 'github'
button_text: 'Visit Project'
lead_text: 'zookeeper'
---

# install zookeeper

---

## install dirs

	shell> mkdir /data/files
	shell> mkdir /data/apps/zk

## download
	
	shell> cd /data/files
	shell> wget https://mirrors.tuna.tsinghua.edu.cn/apache/zookeeper/zookeeper-3.4.8/zookeeper-3.4.8.tar.gz

	https://zookeeper.apache.org/releases.html

## install zookeeper

	shell> tar -zxvf zookeeper-3.4.8.tar.gz
	shell> mv zookeeper-3.4.8 /data/apps/zk

## service script
	
	#!/bin/sh
	### BEGIN INIT INFO
	# Provides: zk
	# Required-Start:    $local_fs $syslog $remote_fs
	# Required-Stop:     $local_fs $syslog $remote_fs
	# Default-Start:     2 3 4 5
	# Default-Stop:      0 1 6
	# Short-Description: Start zk
	### END INIT INFO

	DAEMON_PATH=/data/apps/zookeeper/bin
	DAEMON_NAME=zookeeper

	export JAVA_HOME=/data/apps/jdk8
	export PATH=$JAVA_HOME/bin:$PATH
	PATH=$PATH:$DAEMON_PATH

	# See how we were called.
	case "$1" in
	  start)
	        # Start daemon.
	        echo "Starting $DAEMON_NAME";
	        nohup $DAEMON_PATH/zkServer.sh start > /data/logs/zk/nohup.log 2>&1 &
	        echo "Done.";
	        exit 0
	        ;;
	  stop)
	        # Stop daemons.
	        echo "Shutting down $DAEMON_NAME";
	        pid=`ps ax | grep -i 'zookeeper' | grep -v grep | awk '{print $1}'`
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
	        pid=`ps ax | grep -i 'zookeeper' | grep -v grep | awk '{print $1}'`
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
	
	shell> vi /etc/init.d/zk            # save script
	shell> /etc/init.d/zk start         # up service
	shell> update-rc.d zk defaults 100  # auto start & priority 100

## about
	
	http://zookeeper.apache.org