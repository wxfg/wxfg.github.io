---
title: java获取mysql datetime类型值时差问题
date: 2025-06-06+0800
categories: [java]
tags: [java,mysql,时区]
description: 
---

#### 基础
- mysql datime类型不包含时区信息
- java Date类型不包含时区信息
- mysql
  : 全局级别时区
    ```sql
    SELECT @@GLOBAL.time_zone;
    SET GLOBAL time_zone = '+8:00';
    ```

  : 会话级别时区
    ```sql
    SELECT @@SESSION.time_zone;
    SET time_zone = '+8:00';
    ```
    
    ```java
    jdbc:mysql://{host}:{port}/{database}?serverTimezone={GMT%2B8}
    ```
- jvm
  : TZ环境变量
     ```shell
     export TZ=Asia/Shanghai
     ```

  : JVM property -Duser.timezone
    ```shell
    java -Duser.timezone=Asia/Shanghai -jar {x.jar}
    ```
- 写入时，java Date值会从jvm时区转换为mysql时区；读取时，mysql datetime值会从mysql时区转换为jvm时区

#### 原因
jvm与mysql时区不一致

#### 解决方法
将jvm与mysql时区设置一致，建议在分别用-Duser.timezone和jdbc设置