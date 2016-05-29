---
layout: inner
position: right
title: 'install java'
date: 2016-05-29 19:30:00
categories: development
tags: java
featured_image: ''
project_link: ''
button_icon: 'github'
button_text: 'Visit Project'
lead_text: 'java'
---

# install java

---

## install dirs

	shell> mkdir /data/files
	shell> mkdir /data/apps/jdk8

## download
	
	shell> cd /data/files
	shell> wget http://xxx/jdk-VERSION-linux-i586.tar.gz

	http://www.oracle.com/technetwork/java/javase/downloads/index.html

## install java

	shell> tar -zxvf jdk-VERSION-linux-i586.tar.gz
	shell> mv jdk-VERSION-linux-i586 /data/apps/jdk8

## environment

	shell> sudo vi /etc/profile
	shell> source /etc/profile

	# java
	export JAVA_HOME=/data/apps/jdk8
	export PATH=$PATH:$JAVA_HOME/bin

## test

	shell> java -version

	java version "1.8.0_91"
	Java(TM) SE Runtime Environment (build 1.8.0_91-b14)
	Java HotSpot(TM) 64-Bit Server VM (build 25.91-b14, mixed mode)

## about
	
	http://java.sun.com/