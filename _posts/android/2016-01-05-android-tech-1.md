---
layout: post
title: 组件化开发之-反射
category: Android
tags: 开发框架
keywords: Android,工具
---

在组件化开发中。有的时候为了解耦可以用一下反射。虽然反射对性能有影响，大家自己衡量一下吧

### JOOR简化版本的反射框架

这个JOOR太适合运用在Android上了，这货只有两个文件哦。

[GitHub地址](https://github.com/jOOQ/jOOR)

#### 用法

compile 'org.jooq:joor:0.9.7'

``` java

String world = on("java.lang.String")  // 类似我们调用 Class.forName()
                .create("Hello World") // 初始化带参数"Hello World"的构造函数
                .call("substring", 6)  // 调用substring() 方法
                .call("toString")      // 调用toString() 方法
                .get();                // Get the wrapped object, in this case a String

```


