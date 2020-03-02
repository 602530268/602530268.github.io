---
layout: mypost
title: 解决dyld Library not loaded
date:   2020-02-15 22:19:00
categories: [iOS, 踩坑]
---

# iOS 解决dyld: Library not loaded: @rpath/xxx.framework/

程序编译成功，但是运行报错，解决办法：

* Build Phases 
* 点击加号 
*  New Copy Files Phase 
* Destination 选择 Frameworks
* 将报错的xxx.framework 拖进Name栏中即可