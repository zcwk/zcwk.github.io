---
layout: post
title: 别人开发遇到的坑
category: Android
tags: Android 开发总结
keywords: Android,开发总结
---

1.处理Date类型，因为JSON本身没有Date类型，因此，JSON库将Date类型的数据序列化时会转为String。这时，不同环境，不同平台，以及用不同的JSON解析库，转换后的结果经常会不同。比如，你在开发机上可能得到的结果是”2016-1-1 17:11:11”，但放到服务器后结果却变成了“Jan 1,2016 5:11:11 PM” ，客户端进行反序列化时无疑会失败。后来，我取消了所有Date类型，统一采用时间戳表示，就再没有转化的烦恼了。
