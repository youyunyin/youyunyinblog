---
title: mac中JDK安装配置
categories: java
tags: [mac,java]
date: 2017-09-24
---
## 系统内置JDK
mac默认自带一个jdk6

## 自定义安装JDK
从oracle下载jdk安装后
默认安装路径如下
```
/Library/Java/JavaVirtualMachines/jdk1.8.0_101.jdk/Contents/Home
```
并且系统内置的jdk会默认为最新安装的

## 环境变量配置
vi .bash_profile
输入：
```
export JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk1.8.0_101.jdk/Contents/Home
export CLASSPAHT=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
export PATH=$JAVA_HOME/bin:$PATH:
export PATH
```

## 删除已经安装的jdk
```
sudo rm -rf jdk1.8.0_101.jdk
```
可以进入
```
cd /usr/libexec
java_home -V
```
查看所有jdk的路径
```
/Library/Java/JavaVirtualMachines/jdk1.8.0_101.jdk/Contents/Home
```


