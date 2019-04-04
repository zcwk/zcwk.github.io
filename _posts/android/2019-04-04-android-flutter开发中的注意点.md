---
layout: post
title: Flutter 开发中的注意点
category: Flutter
tags: Flutter Flutter
keywords: Flutter 填坑
---


## 适配刘海屏
 
 根布局用SafeArea 可以自动处理上和下的间距，避开刘海屏和底部的遮挡

## 沉侵式布局可以利用SafeArea 设置top为false，这里有个巨坑。如果你的布局是ListView 你需要加个间距padding: new EdgeInsets.all(0.0),不然布局上部分不会上去的。始终会显示statusBar的高度





