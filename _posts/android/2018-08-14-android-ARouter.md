---
layout: post
title: Android-组件化开发之-ARouter源码解析
category: Android
tags: Android ARouter源码解析
keywords: 源码解析
---


## 下载源码后查看Gradle文件后发现这几个东西
``` java
classpath 'com.neenbedankt.gradle.plugins:android-apt:1.8'
compile 'com.google.auto.service:auto-service:1.0-rc2'
compile 'com.squareup:javapoet:1.7.0'
```
哈哈哈 我来解释一下这几个东西是什么玩意哦

## apt
  apt是在编译期对代码中指定的注解进行解析，然后做一些其他处理（如通过javapoet生成新的Java文件）。我们常用的ButterKnife，其原理就是通过注解处理器在编译期扫描代码中加入的@BindView、@OnClick等注解进行扫描处理，然后生成XXX_ViewBinding类，实现了view的绑定。

## javapoet
 javapoet是鼎鼎大名的squareup出品的一个开源库，是用来生成java文件的一个library，它提供了简便的api供你去生成一个java文件。

## auto-service
  AutoService google开源的自动注册工具AutoService

## ARouter原理
  实际上它的核心思想就是，我们在代码里加入的@Route注解，会在编译时期通过apt生成一些存储path和activity. class映射关系的类文件，然后app进程启动的时候会加载这些类文件，把保存这些映射关系的数据读到内存里(保存在map里)，然后在进行路由跳转的时候，通过build()方法传入要到达页面的路由地址，ARouter会通过它自己存储的路由表找到路由地址对应的Activity.class(activity.class = map.get(path))，然后new Intent(context, activity.Class)，调用ARouter的withString()方法它的内部会调用intent.putExtra(String name, String value)传值，调用navigation()方法，它的内部会调用startActivity(intent)进行跳转。
