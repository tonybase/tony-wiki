---
layout: inner
position: right
title: 'android log'
date: 2016-03-28 21:50:00
categories: development
tags: android
featured_image: ''
project_link: ''
button_icon: 'github'
button_text: 'Visit Project'
lead_text: 'android'
---

# Android 日志管理

## 简介
+ 在程序中输出日志, 使用 GLog、Logger、LoggerFactory 类，用于控制应用全局日志输出级别（默认VERBOSE），以及Pretty输出日志。
+ 日志级别：VERBOSE、DEBUG、INFO、WARN、ERROR
+ 应用发布时，日志级别设置为INFO，这时只输出INFO、WARN、ERROR三种日志信息。

### 使用方式
	
	// 直接使用TAG
    private final Logger logger = LoggerFactory.getLogger(“G_HTTP”);
    // 直接使用类名为TAG，建议使用
    private final Logger logger = LoggerFactory.getLogger(MainActivity.class);

    logger.v("log content");

    如果在静态方法使用：
    private static final Logger LOG = LoggerFactory.getLogger(MainActivity.class); 

    LOG.v("log content");

### 标注
+ json自动判断转换为pretty输出。
+ log可以直接传object，也可以传空，过虑null异常。
+ tag是一个标识，可以是任意字符串,通常可以使用类名，主要是用来在查看日志时提供一个筛选条件。
+ http网络构架日志默认输出TAG为“G_HTTP”，可以通过这标记查看请求内容。

### 日志级别
+ VERBOSE 一般冗长数据值信息，例如接口request/response，模块中的非重要调试值输出。
+ DEBUG 模块中变量数据值，或者调试结果值输出。
+ INFO 模块中重要的显示信息输出，例如app信息、渠道名称、包名、版本号，关键功能信息。
+ WARN 模块中的一些警告信息输出，方便测试查看。
+ ERROR 模块中的异常信息输出，比较关键的一种信息。