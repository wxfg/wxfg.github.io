---
title: npm run dev异常：digital envelope routines::unsupported
date: 2025-05-22+0800
categories: [web]
tags: [node,npm,webpack]
description: 
---

#### 问题
执行 npm run dev，报错 Error: error:0308010C:digital envelope routines::unsupported

#### 原因
Node.js 从17版本开始，OpenSSL 从1.x升级到了OpenSSL 3，弃用了老的加密算法；
但是webpack还依赖这些被弃用的加密算法

#### 解决方法1
windows平台下需要将export改为set

```shell
export NODE_OPTIONS=--openssl-legacy-provider

npm run dev
```


#### 解决方法2
修改package.json，windows平台下需要将export改为set

```json
"scripts": {
   "dev": "export NODE_OPTIONS=--openssl-legacy-provider && vue-cli-service serve",
   "build": "export NODE_OPTIONS=--openssl-legacy-provider && vue-cli-service build"
}
```