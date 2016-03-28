---
layout: inner
position: right
title: 'android naming conventions'
date: 2016-03-28 21:48:00
categories: development
tags: android
featured_image: ''
project_link: ''
button_icon: 'github'
button_text: 'Visit Project'
lead_text: 'android'
---

# 命名规范  

## 简介
开发时请遵守以下编程规范与命名约定，以便内部团队风格统一。

### Java Class
+ 规则：每个java类的声明需要加上简单的功能阐述
+ Activity: 功能名称+Activity，如：LoginActivity
+ Fragment: 功能名称+Fragment，如：UserFragment
+ Adapter: 功能名称+Adapter，如：MovieAdapter
+ Dialog: 功能名称+Dialog，如：MovieDetailsDialog

### Xml  
+ 规则：命名方式类似于Java Class
+ Activity: activity_，如：activity_login.xml
+ Dialog: dialog_，如：dialog_loading.xml
+ Window: window_，如：window_buy.xml
+ Fragment: fragment_，如：fragment_user.xml
+ Adapter: item_，如：item_movie.xml
+ View: view_，如：view_loading_more
+ Include: include_，如：include_goods_detail

### 图片资源
+ icon类：ic_，如：ic_menu.png
+ 背景：bg_，如：bg_user.png
+ 示例图：test_，如：test_avatar.png  

### Widget ID（控件ID）
+ RelativeLayout: rl_
+ LinearLayout: ll_
+ FrameLayout: fl_
+ TableLayout: tl_
+ TextView: tv_
+ ImageView: iv_
+ Button: btn_
+ ImageButton: ib_
+ RadioGroup: rg_
+ RadioButton: rb_
+ ListView: lv_
+ ProgressBar: pb_
+ EditText: et_
+ ScrollView: sv_
+ CheckBox: cb_
+ 事件绑定型控件: action_

### 其他资源文件
+ selector: selector_
+ shape: shape_

### selector状态 
+ Normal：	_normal    ，如： btn_order_normal.png
+ Pressed：	_pressed   ，如： btn_order_pressed.png
+ Focused：	_focused   ，如： btn_order_focused.png
+ Disabled：_disabled  ，如： btn_order_disabled.png
+ Selected：_selected  ，如： btn_order_selected.png

### Java 类，接口命名
+ 驼峰式：首字母为大写，其他字母均为小写；如果类名称由多个单词组成，则每个单词的首字母均应为大写 UserResponse

### Java 变量名  
+ 控件：以 控件ID 作为java变量名（tv_title）
+ 普通变量：遵循java命名规范和JSON，命名应该采用首字母小写，其他字母首字母大写的方式，使用”驼峰“命名即可（mUserList, mUserInfo）. 界面数据成员名字以 m 开头(如 mOpenId) 
+ 常量变量：final static变量的名字应该都大写，如果一个常量名称由多个单词组成，则应该用下划线来分割这些单词（CONFIG_LOGIN_USER, PARAM_USER）
+ 页面间（Activity, Fragment）传参，请使用public final static常量作为key，切勿直接使用手写的字符串作为key，具体key的命名：PARAM_，如：PARAM_USER

### Java 方法名
+ 设置/获取某个值的方法，应该遵循setV/getV规范
+ 返回长度/数量的方法，应该命名为length()/size()/conut()
+ 测试某个布尔值的方法，应该命名为isLogin()
+ 将对象转换为某个特定类型的方法应该命名为toDate()
+ getDate(), length(), isReady(), toDate()

## About
+ [Android Code Style for Contributors](https://source.android.com/source/code-style.html)  
