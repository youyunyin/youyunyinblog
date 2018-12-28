---
title: hexo结合gitpage搭建无限空间静态博客
categories: 笔记
tags: [hexo,github,gitpage]
date: 2018-10-19
---

# 什么是Hexo
Hexo 是一个快速、简洁且高效的博客框架。Hexo 使用 [Markdown](http://wushuning.com/2018/10/01/markdown/)（或其他渲染引擎）解析文章，在几秒内，即可利用靓丽的主题生成静态网页。  
生成静态网页即可托管到任何支持静态网页的服务器上。

# 什么是GitPage
[GitHub Pages](https://pages.github.com/) 与GitHub同属一个研发组织，免费为你的GitHub项目提供项目部署和托管服务，一个GitHub账号可以创建一个GitPage空间。GitPage支持静态和markdown语法的项目，并与GitHub上的项目实时同步自动渲染。所以你可以很容易使用GitPage搭建自己的博客。

特别注意：一个GitHub账号只能创建一个GitPage空间，并且名称有特殊要求下文详细说明。

可选框架：
[jekyll](https://jekyllrb.com/docs/)

# 环境准备
```
nodejs
Git
```

# 创建github账号和同名项目

* 申请账号如:wangzhikui
* 创建同名项目:wangzhikui.github.io  

如图:
![](/images/hexo/hexo-gitpage-1.png)

进入项目的【setting > GitHub Pages】

如图：

![](/images/hexo/hexo-gitpage-2.png)
按照描述设置开启即可。

到此为止GitPages已经可以使用，提交到wangzhikui.github.io的静态或markdown形式的文件会自动同步到GitPages空间。可通过http://wangzhikui.github.io访问。

# 配置域名(无此需要可跳过)
## 一、上一步GitPages设置中设置域名如：wushuning.com

## 二、配置域名的A地址和CNAME别名

本域名在阿里云申请，所以登录aliyun.com进入域名配置，域名解析做如下配置

![域名配置](/images/hexo/域名配置.png)

## 三、项目根目录中添加名为CNAME的文件，内容为 wushuning.com

![CNAME](/images/hexo/cname.png)

# hexo使用
## 安装hexo并使用hexo创建项目
安装hexo脚手架工具并使用脚手架创建项目
```
npm install hexo-cli -g
hexo init wangzhikuiblog
cd wangzhikuiblog
npm install
hexo server
```
1. 全局安装脚手架hexo-cli
2. 创建一个名为wangzhikuiblog的项目
3. 进入项目目录
4. 安装依赖包
5. 启动服务

服务启动成功出现如下图：
![](/images/hexo/hexo-start.png)

通过http://localhost:4000访问示例程序
到此使用hexo创建项目已经完成

## 手动部署
进入项目目录运行命令
```
hexo g
```
则会在项目路径中生成一个public文件夹，里边的内容即为hexo为我们生成的所有静态文件。手动将public里边的所有文件git传到wangzhikui.github.io即可。

到此可通过  
http://wangzhikui.bighub.io  
或域名（如果配置了）  
http://wushuning.com  
访问你的网站。

## 自动部署
打开项目根目录下的_config.yml 找到如下配置:
``` yml
deploy:
  type: git
  repo:
    github: git@github.com:wangzhikui/wangzhikui.github.io.git
```
运行命令
```
hexo d
```
则将public下的文件部署到wangzhikui.github.io.git上，我这里只有一个分支master，所以默认，如果要填写分支可以配置repo。建议保持一个分支就可以了。

hexo d 命令push代码使用的是ssh，所以需要配置github的ssh key 关于key生成配置这里不赘述。

**`注：如果本地要维护两个github账号，这种情况有可能遇到ssh key冲突，该情况在下一篇博文描述`**

## hexo生成的项目目录结构简介
使用hexo创建的项目路径如下图：

![hexo 项目结构](/images/hexo/hexo-project.png)  

[项目源码](https://github.com/wangzhikui/wangzhikuiblog)

## hexo常用命令
| 命令 | 简写 | 描述 |
|:----|:----|:----|
| hexo server | hexo s | 启动服务 |
| hexo generate | hexo g | 生成静态文件 |
| hexo deploy | hexo d | 将静态文件部署到github上 |
| hexo clean | 无 | 清除缓存文件 (db.json) 和已生成的静态文件 (public) |

查看更多命令: [hexo 命令大全](https://hexo.io/zh-cn/docs/commands)

本人在部署的时候喜欢使用三个命令组合
```
hexo clean
hexo g
hexo d
```
## 使用主题
主题文件存放在 /themes下。本博客基于主题[hexo-theme-pure](https://github.com/cofess/hexo-theme-pure) 修改而来。大家也可前往[hexo 主题库](https://hexo.io/themes/) 下载自己需要的主题。

下载主题后放入/thems下

打开项目根目录的配置文件._config.yml.修改配置theme为你主题的文件夹名称即可
```
theme: hexo-theme-yyy
```
## 创建博文
### 通过命令
进入项目目录
```
hexo new test
```
常见一篇名为test.md的博文，路径在/source/_posts/test.md
打开test.md使用markdown编辑即可。
### 手动创建
直接在_posts文件夹下创建一个test.md的文件即可

# 未完待续  

> hexo的_config.yml和themes_config.yml分别有哪些重要配置

> hexo中博文md文件都有哪些配置

> hexo中使用gitalk添加评论功能

> 一个hexo主题都包含什么，如何入手修改主题满足自己个性化设置

> 本地同时维护两个github账号如何设置ssh key