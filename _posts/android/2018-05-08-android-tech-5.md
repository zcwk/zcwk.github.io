---
layout: post
title: Android-ORM-对象关系映射
category: Android
tags: Android ORM
keywords: Android,对象关系映射
---

在开发IM即时通信的APP中。我们一般会把用户消息存储在数据库中。下面是我常用的两款ORM开源框架

1.GreenDao
2.Realm

性能对比。Realm完爆GreenDao,但是GreenDao的体积很小哦。小于100KB  ，而Realm 那是1M起啊。大家斟酌一下吧。
其实我目前还是用GreenDao。但是我用了他的升级版本 [ObjectBox](http://objectbox.io/),这个的性能有很大的提升。而且体积也小。

| 框架名 | 添加10000条数据的时间 | 查询10000条数据的时间 | 删除10000条数据的时间 |
| - | :-: | -: | -: | 
| GreenDao | 10466| 600 | 47 | 
| Realm | 1597 | 8 | 136 | 


除了删除数据有点优势。其他真的是被完爆了
