---
layout: post
title: ROOM 数据库的使用
category: Android
tags: ROOM 数据库的使用
keywords: ROOM 数据库的使用
---

## 相关用法请看Google 

[ROOM](https://developer.android.com/training/data-storage/room?hl=zh-cn)

## ROOM 数据库查看内容

[sqlitebrowser](https://github.com/sqlitebrowser/sqlitebrowser)
用这个查看数据库的数据


## 开发中遇到的问题点

单元测试会在Device File Explorer -》 data/data/包名.text 中


## 常用注解

```
@Fts4
@Entity(tableName = "users",ignoredColumns = "picture",indices = {@Index("name"), @Index(value = {"last_name", "address"})})
@TypeConverters({DeviceIotInfoConverters.class, ThumbConverter.class})
public class User {
    @PrimaryKey
    public int id;

    public String firstName;
    public String address;

    @ColumnInfo(name = "last_name")
    public String lastName;

    @Ignore
    Bitmap picture;
}
```

[常用注解](https://www.sunzn.com/2019/02/23/Android-Room-%E4%BD%BF%E7%94%A8%E6%8C%87%E5%8D%97/)
 
















