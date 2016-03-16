---
layout: post
title: Android-TextView
category: Android
tags: Android 控件
keywords: Android,控件
---

android里TextView加下划线的几种方式

如果是在资源文件里：
```java
 <resources>
    <string name="hello"><u>链接</u></string>
    <string name="app_name">hello</string>
</resources>
 ```

如果是代码里：
```java
TextView textView = (TextView)findViewById(R.id.tv_test); 
textView.setText(Html.fromHtml("<u>"+"链接"+"</u>"));
```

代码也可以这样：
```java
tvTest.getPaint().setFlags(Paint. UNDERLINE_TEXT_FLAG ); //下划线
tvTest.getPaint().setAntiAlias(true);//抗锯齿
```
