---
layout: inner
position: right
title: 'install kafka'
date: 2016-05-29 19:32:00
categories: development
tags: kafka
featured_image: ''
project_link: ''
button_icon: 'github'
button_text: 'Visit Project'
lead_text: 'kafka'
---

# install kafka

---

## install dirs

	shell> mkdir /data/files
	shell> mkdir /data/apps/kafka

## download

	shell> cd /data/files
	shell> wget https://www.apache.org/dyn/closer.cgi?path=/kafka/0.9.0.1/kafka_2.10-0.9.0.1.tgz

	http://kafka.apache.org/downloads.html

## install kafka
	
	shell> tar -zxvf kafka_2.10-0.9.0.1.tgz
	shell> mv kafka_2.10-0.9.0.1 /data/apps/kafka

## service script

	#!/bin/sh
	### BEGIN INIT INFO
	# Provides: kafka
	# Required-Start:    $local_fs $syslog $remote_fs dbus
	# Required-Stop:     $local_fs $syslog $remote_fs
	# Default-Start:     2 3 4 5
	# Default-Stop:      0 1 6
	# Short-Description: Start kafka
	### END INIT INFO

	DAEMON_PATH=/data/apps/kafka/bin
	DAEMON_NAME=kafka
	JAVA_PATH=/data/apps/jdk8/bin
	# Check that networking is up.
	#[ ${NETWORKING} = "no" ] && exit 0

	export JAVA_HOME=/data/apps/jdk8
	export PATH=$JAVA_HOME/bin:$PATH
	PATH=$PATH:$JAVA_PATH$DAEMON_PATH

	# See how we were called.
	case "$1" in
	  start)
	        # Start daemon.
	        echo "Starting $DAEMON_NAME"
	        nohup $DAEMON_PATH/kafka-server-start.sh /data/apps/kafka/config/server.properties > /data/logs/kafka/nohup.log 2>&1 &
	        echo "Done."
	        exit 0
	        ;;
	  stop)
	        # Stop daemons.
	        echo "Shutting down $DAEMON_NAME"
	        pid=`ps ax | grep -i 'kafka.Kafka' | grep -v grep | awk '{print $1}'`
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
	        pid=`ps ax | grep -i 'kafka.Kafka' | grep -v grep | awk '{print $1}'`
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
	
	shell> vi /etc/init.d/kafka            # save script
	shell> /etc/init.d/kafka start         # up service
	shell> update-rc.d kafka defaults 101  # auto start & priority 101, zookeeper is 100.

## about

	http://kafka.apache.org