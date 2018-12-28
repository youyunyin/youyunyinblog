---
title: markdown常用语法
categories: markdown
tags: [markdown]
date: 2018-10-01
---
本文参考 [Github markdown 基本写法](https://help.github.com/articles/basic-writing-and-formatting-syntax/#further-reading)，更多详细描述可直接前往Github查看 

# 目录
- [标题](#标题)
- [文本样式](#文本样式)
- [引用文本](#引用文本)
- [引用代码](#引用代码)
- [链接](#链接)
- [部分链接](#部分链接)

```
- [标题](#标题)
- [文本样式](#文本样式)
- [引用文本](#引用文本)
- [引用代码](#引用代码)
- [链接](#链接)
- [部分链接](#部分链接)
```

# 标题
文字前使用(1-6个)#，不同数量代表文字不一样大小
# 标题1
## 标题2
### 标题3
#### 标题4
##### 标题5
###### 标题6
```
# 标题1
## 标题2
### 标题3
#### 标题4
##### 标题5
###### 标题6

```
# 文本样式
| 样式 | 语法 | 快捷键 | 示例 | 效果 |
|:----|:----:|-----:|-----:|----:|
| 粗体 | `** **`或`__ __` | command/control + b | `**Hello World**` | **Hello World**|
| 斜体 | `* *`或`_ _` | command/control + i | `*Hello World*` | *Hello World* |
| 删除 | `~~ ~~` | 无 | `~~Hello World~~` | ~~Hello World~~ |
| 粗体&斜体 | `~~ ~~`和`_ _` | 无 | `**Hello _World_**` | **Hello _World_** |

表格源码
```
| 样式 | 语法 | 快捷键 | 示例 | 效果 |
|:----|:----:|-----:|-----:|----:|
| 粗体 | `** **`或`__ __` | command/control + b | `**Hello World**` | **Hello World**|
| 斜体 | `* *`或`_ _` | command/control + i | `*Hello World*` | *Hello World* |
| 删除 | `~~ ~~` | 无 | `~~Hello World~~` | ~~Hello World~~ |
| 粗体&斜体 | `~~ ~~`和`_ _` | 无 | `**Hello _World_**` | **Hello _World_** |
```

# 引用文本
使用 >，可以使用多个>来嵌套
> 被引用的文字
>> 被引用的文字2
>>> 被引用的文字3  

```
> 被引用的文字
>> 被引用的文字2
>>> 被引用的文字3  
```
# 引用代码
使用如下标志将文字包含即可

```
  使用``` ``` 将代码包含即可
  也可以加上语言来使得块中语法高亮
    ``` java
    ``` javascript
    ``` html
```
基础格式
```
git status
git add
git commit
```
java  
``` java
public static void main(String[] args){
  System.out.print("Hello World")
}
```
javascript  
``` javascript
function sayHello(){
  console.log('Hello World')
}
```
html  
``` html
<div>
  <h1> Hello World </h1>
</div>
```
Github使用[Linguist](https://github.com/github/linguist)进行语言检测，并选择[第三方语法](https://github.com/github/linguist/blob/master/vendor/README.md)进行语法突出显示。您可以在[YAML](https://github.com/github/linguist/blob/master/lib/linguist/languages.yml)文件中找到哪些关键字是有效的。

# 链接

```
 [友云音](http://yyy.yonyoucloud.com)
```
[友云音](http://yyy.yonyoucloud.com)

链接可以使用相对地址

| 语法 | 目录 |
|:----|:----:|
| / | 根目录 |
| ./ | 当前目录 |
| ../ | 上级目录 |
```
[友云音logo](/images/logo/youyunyin-logo.png)
```
[友云音logo](/images/logo/youyunyin-logo.png)

# 部分链接
当我们写好md发布渲染生成html之后，当鼠标移动到某一块的头部的时候会显示#（也有可能是其他图表），点击之后地址栏会生成一个部分连接。使用该地址栏的地址访问该文章会自动定位到点击的这个块。  
比如本文的地址是:  
http://youyunyin.com/2018/10/01/markdown/  
点击[文本样式]这个标题，地址栏url变为
http://youyunyin.com/2018/10/01/markdown/#文本样式
点击改链接就会直接进入该页面并跳转到[文本样式]块中

# 列表
使用 - 或者 *

- 第1行
- 第2行
  - 第2-1行
    - 第2-1-1行
    - 第2-1-2行
  - 第2-2行
- 第3行

```
- 第1行
- 第2行
  - 第2-1行
    - 第2-1-1行
    - 第2-1-2行
  - 第2-2行
- 第3行
```
使用数字  
1. 第1行
2. 第2行
3. 第3行

```
1. 第1行
2. 第2行
3. 第3行
```
# 任务列表（gihub扩展，非标准markdown）
- [x] 任务1
- [ ] 任务2
- [ ] 任务3

```
- [x] 任务1
- [ ] 任务2
- [ ] 任务3
```
# 段落
文字后面输入两个空格换行

# 图片
![友云音logo](/images/logo/youyunyin-logo.png "友云音logo")
```
![友云音logo](/images/logo/youyunyin-logo.png "友云音logo")
```
# 分割线
使用 三个以上 - 或 *
```
---
----
***
****
```
---
----
***
****