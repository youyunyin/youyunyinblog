---
title: mac中配置eclipse启动使用的jdk，eclipse.ini文件
categories: 研发工具
tags: [mac,eclipse,研发工具]
date: 2017-09-24
---
## 设置eclipse使用的jdk
* application中找到eclipse右键show content找到eclipse的配置文件eclipse.ini
* 增加配置如下  
```
-vm
/Library/Java/JavaVirtualMachines/jdk1.8.0_101.jdk/Contents/Home
```

其中jdk的路径可以通过命令
```
/usr/libexec/java_home -V
```
最后是大写的V查看


