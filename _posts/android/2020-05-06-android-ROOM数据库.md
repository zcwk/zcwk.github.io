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


## 数据库升级的坑

fallbackToDestructiveMigration()。将会删除数据库并重建

```
vesion增加，提供Migration - 数据正常
static final Migration MIGRATION_1_2 = new Migration(1, 2) {
    @Override
    public void migrate(SupportSQLiteDatabase database) {
        // 因为没有变化，所以是一个空实现
    }
};
```
改表结构
```
static final Migration MIGRATION_2_3 = new Migration(2, 3) {
    @Override
    public void migrate(SupportSQLiteDatabase database) {
        database.execSQL("ALTER TABLE users "
                + " ADD COLUMN last_update INTEGER");
    }
};
```
复杂的Migration
```
static final Migration MIGRATION_3_4 = new Migration(3, 4) {
    @Override
    public void migrate(SupportSQLiteDatabase database) {
        // 创建临时表
        database.execSQL(
                "CREATE TABLE users_new (userid TEXT, username TEXT, last_update INTEGER, PRIMARY KEY(userid))");
        // 拷贝数据
        database.execSQL(
                "INSERT INTO users_new (userid, username, last_update) SELECT userid, username, last_update FROM users");
        // 删除老的表
        database.execSQL("DROP TABLE users");
        // 改名
        database.execSQL("ALTER TABLE users_new RENAME TO users");
    }
};
```


## 常用注解

[常用注解](https://www.sunzn.com/2019/02/23/Android-Room-%E4%BD%BF%E7%94%A8%E6%8C%87%E5%8D%97/)
 

## 常用SQL语句

```
//创建新的数据表
database.execSQL("CREATE TABLE IF NOT EXISTS `owner` (`id` INTEGER PRIMARY KEY AUTOINCREMENT NOT NULL, `room_id` TEXT, `name` TEXT, `portrait` TEXT)");

//模糊查询
@Query("SELECT * FROM owner WHERE room_id LIKE '%' || :roomId || '%'")
    fun getAllOwnerByRoomId(roomId: String): List<Owner>

        
```














