---
title: 前端技术选型yyy-1.0
categories: 研发管理
tags: [研发管理]
date: 2016-05-24
---

# 前端技术选型
## 一，AngularJS+BootStrap+RequireJS
### AngularJS  前端js框架，MVVM、模块化、自动化双向数据绑定、语义化标签、依赖注入
http://www.apjs.net/

http://docs.angularjs.cn/api

### BootStrap。Css/html框架，前端UI类库

http://bootstrap.evget.com/

http://v3.bootcss.com/

### RequireJS。Js模块化按需加载工具，遵循AMD提前加载

http://www.requirejs.cn/

http://requirejs.org/

模块化定义规范AMD与CMD

http://www.zhihu.com/question/20351507/answer/14859415

特点：angularjs新的前端设计思想，将后端MVC，依赖注入前置，本身就是一套完整的前端mvc架构

前端js单元测试框架QUnit, Mocha 或者 Jasmine
## 二，Jquery+Bootstrap+RequireJS
特点：主流前端开发思想，简单，上手快，对于前端功能不复杂的情况非常实用
## 三， React + Redux + RequireJS + jQuery(或Zepto) + UIKit(或Bootstrap、SUI)+ReactRouter(单页面路由器框架)
React技术背景：Facebook于13年发布的开源框架，技术针对模型层和数据层，地址：

http://facebook.github.io/react/

React技术特点：
* 采用虚拟DOM技术，可以高效率进行DOM渲染；
* 组件化组装式开发模式，简单高效；
* 单向数据流，数据维护简单；
* 支持JSX；
* 支持数据渲染；
* 可以采用后端JS开发模式。

其他技术介绍：

* Redux：数据层框架，采用事件模型进行数据维护，在数据复用和数据同步方面优势明显。
* RequireJS：按需加载JS
* Zepto：移动端使用的jQuery替代技术
* UIKit：前端UI框架，类似于Bootstrap，技术成熟，使用相对简单；
* SUI：移动端UI框架，淘宝团队开发，采用iOS风格；新框架，迭代很快，几天一个版本，坑比较少
* ReactRouter：针对ReactJS的单页面框架
* ES6支持：可以使用ES6语法进行开发，生产环境使用Babel等转义到ES5运行。

浏览器支持情况：IE8+

学习成本：主要学习成本在于React、Redux和jQuery。React API很简单，入手大概1.5天；Redux学习成本大概一天。

技术成熟度：技术成熟，背景比较强大，很多互联网公司的产品正在逐步迁移到React，比如美团、乐视、阿里等；基于React的React Native，是Facebook 15年刚发布的移动开发开源技术，现在国内已经有部分APP在尝试了。

其他
* IDE：intellj idea   webstorm
* 包管理：nodejs，npm，bower
Bower:https://segmentfault.com/a/1190000002971135

* 代码结构：angular-seed，yeoman，自定义
* 参考：http://angularjs.cn/A04g
* 测试：karma，jasmine
* 构建：grunt
