---
title: MAC破解安装IntelliJ IDEA方法
categories: mac
tags: [idea,mac,研发工具]
date: 2018-01-11
---

# MAC下破解安装Intellij IDEA 2017 方法
破解的版本：
```  
IntelliJ IDEA 2017.3.2 (Ultimate Edition)  
Build #IU-173.4127.27, built on December 26, 2017  
Licensed to Rover12421 / Rover12421  
You have a perpetual fallback license for this version  
Subscription is active until December 31, 2099  
JRE: 1.8.0_152-release-1024-b8 x86_64  
JVM: OpenJDK 64-Bit Server VM by JetBrains s.r.o  
Mac OS X 10.13.2  
```

## 1、下载IntelliJ IDEA 2017
[IDEA官网下载无限制版](https://www.jetbrains.com/idea/download/#section=mac)  
<img src="/images/idea/ideadownload.jpg" width="60%"/>
   
## 2、下载破解文件JetbrainsCrack-2.6.2.jar  
[进入下载界面](http://idea.lanyus.com)  

<img src="/images/idea/coderegist.png" width="60%"/>

## 3、安装IntelliJ IDEA 2017

## 4、安装后Applications文件夹中找到IDEA,右键show package contents找到bin目录下，将下载的破解文件拷贝到该目录下
<img src="/images/idea/registaccess.png" width="60%"/>

## 5、打开上图中的idea.vmoptions追加如下配置
```
-javaagent:/Applications/IntelliJ IDEA.app/Contents/bin/JetbrainsCrack-2.6.10-release-enc.jar
```
## 6、启动IDEA 提示需要注册，将获取的注册码填入
Help > Register  
<img src="/images/idea/registin.png" width="60%"/>  
选中Activation code 将注册码填入下面的输入框中即可   
<img src="/images/idea/registwindow.png" width="60%"/>


