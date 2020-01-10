---
layout: mypost
title: GitHub配置SSH
date:   2020-01-10 12:03:00
categories: [iOS, 功能块]
---



GitHub上有些工程下载需要配置SSH，配置方法如下：

打开终端

```
设置Git的user name和email：
$ git config --global user.name "chen"
$ git config --global user.email "xxxx@qq.com"

生成SSH
先查看是否已经有了ssh密钥，有则备份删除
$ ssh-keygen -t rsa -C "xxxx@qq.com"

一直回车，密码设置为空，最后得到两个文件id_rsa和id_rsa.pub
Your identification has been saved in /Users/chencheng/.ssh/id_rsa.
Your public key has been saved in /Users/chencheng/.ssh/id_rsa.pub.

打开id_rsa.pub公钥文件，并拷贝内容

在GitHub上新建SSH（New SSH Key）
Title填密钥标题
Key填刚刚拷贝的公钥内容
保存即可
```

这样就可以下载需要SSH的工程了。