---
title: mac中配置环境变量
categories: mac
tags: [mac,环境变量]
date: 2016-12-06
---
## mac修改环境变量

### 修改当前用户环境变量

以配置tomcat为例

打开终端：输入如下指令

``` 
wangzhikuiMacBook-Pro:~ wangzhikui$ vi .bash_profile
```
编辑.bash_prifile文件

在英文输入下按i ，进入编辑状态输入如下

```
export PATH=/Users/wangzhikui/develop/tomcat8.0.39/bin:$PATH:
export JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk1.7.0_71.jdk/Contents/Home
export CLASSPAHT=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
export PATH=$JAVA_HOME/bin:$PATH:
export PATH=/usr/local/mysql/bin:$PATH:
export M2_HOME=/Users/wangzhikui/develop/apache-maven-3.3.9
export PATH=$M2_HOME/bin:$PATH:
export PATH=/Applications/Sublime\ Text.app/Contents/SharedSupport/bin:$PATH:
export PATH
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                                                                                                             
".bash_profile" 9L, 465C
```
按esc键后

输入 :wq

保存退出

配置完后退出终端再打开即可在终端中直接输入tomcat的启动，停止命令
