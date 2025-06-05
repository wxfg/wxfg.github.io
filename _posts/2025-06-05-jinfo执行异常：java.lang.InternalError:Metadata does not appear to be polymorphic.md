---
title: jinfo执行异常：java.lang.InternalError:Metadata does not appear to be polymorphic
date: 2025-06-05+0800
categories: [java]
tags: [java,openjdk,jinfo]
description: 
---

#### 环境
Ubuntu  22.04 + OpenJDK 1.8

#### 问题
执行 jinfo {pid}，报错 java.lang.InternalError:Metadata does not appear to be polymorphic

#### 原因
需要安装 openjdk dbg包

#### 解决方法
```shell
sudo apt-get install openjdk-8-dbg
```