---
title: SpringBoot无法启动，启动后报404错误
categories: springboot
tag: springboot
date: 2017-11-24
---

# SpringBoot无法启动
可能的原因：直接将启动类放在了src.java.main下  
解决方案：在main下创建自己的packadge  
如:src.java.main.com.wzk.starter  

# SpringBoot正常启动，但是访问的时候提示404
原因是：controller没有被spring容器扫描到  
解决方案1：spring boot默认扫描启动类的当前包和下级包  
比如：启动类在 com.wzk.starter包下，那么spring 会扫描 com.wzk.starter和com.wzk.starter.*
如果编写的controller没有放置在这些位置就是报错

解决方案2：配置spring boot的扫描路径  
在启动类上面添加注解：@ComponentScan(basePackages = {"com.wzk.*"})  
