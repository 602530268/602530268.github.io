---
layout: mypost
title: Beego+swagger自动化文档
date:   2020-01-25 20:21:00
categories: [Golang]
---

### 新建项目：

> $ bee api beegoapi

### 生成swagger风格文档：

在conf/app.conf配置文件中添加：

> EnableDocs = true

然后终端执行命令：

> $ bee generate docs

成功后在根目录下会多出一个**swagger**文件夹，里面有两个文档：

> swagger.json
>
> swagger.yml

### 下载swagger网页文件：

> bee run -downdoc=true

该命令会检测swagger目录下是否有swagger-ui文件，没有就会从GitHub上面下载，目前最新的下载地址是[https://github.com/beego/swagger/archive/v3.zip](https://github.com/beego/swagger/archive/v3.zip)

#### 访问swagger文档

[http://localhost:8080/swagger/](http://localhost:8080/swagger/)