---
title: web语义化
categories: web前端
tags: [web前端]
date: 2018-10-31
---

## 定义
wiki(维基百科需要翻墙)的定义：[语义化](http://zh.wikipedia.org/wiki/语义化)是前端开发里面的一个专用术语，其优点在于标签语义化有助于构架良好的html结构，有利于搜索引擎的建立索引、抓取；另外，亦有利于页面在不同的设备上显示尽可能相同；此外，亦有利于构建清晰的机构，有利于团队的开发、维护。

所以在html5中w3c引入了很多的标签：article、footer、header、nav、section等
![](/images/html标签布局.png)

**一些标签语义：**

| 标签	| 语义 |
|:-----:|:----|
| h1~h6 | 标题 |
| th | table的header |
| p	| 段落 |
| ul | 无序列表 |
| ol | 排序列表 |
| dl | definition list，定义列表 |
| dt | definition title，定义名称 |
| dd | definition  description定义描述 |
| em | emphasized，局部强调,段落内强调 |
| strong | 更强烈的强调，全文强调 |

## 核心点

### 便于机器识别html页面中的内容
通常在开发前端过程我们最常用的标签就是div，然后用css来控制样式，各种组件效果都可以做出来，比如table，list,nav等。通常这些对于开发来说是比较容易理解，但是对于机器爬虫就很难快速识别页面中的内容，比如哪些是你的联系方式，哪些是你的文章区域，哪些是你的导航等。

此时如果有效的通过标签对内容尽可能的划分开，比如用footer标签来写copyright，爬虫就会很容知道这是网页的底部，进而很快的抓取到copyright等相关内容等。又比如用nav标签来定义导航块，爬虫根据标签就能很快获取网页的主要内容

### 便于其他研发人员快速读懂页面内容
使用div的时候为了区分div中的内容通常的做法是定义id或者name属性，这样也能达到使用语义标签的效果，但是一旦div非常多，命名不规范的时候很容易造成混乱，对后续维护人员造成很大困难。

合理的使用标签能使得代码易读。当然标签只是一种手段，更重要的还是要有语义化的思想，最终的目的就是让维护人员快速读懂页面内容

通常来说，语义化好的页面，代码量会比较少，html结构清晰，有利于维护代码和添加样式

## 如何做
判断网页标签语义化是否良好的一个简单方法是：去掉样式，看网页结构是否组织良好有序，是否仍然有好的可读性。语义良好的网页去掉样式后结构仍然是比较清晰的。尤其是在图片较少的网页中。

## 实例
对如下内容格式化：
![](/images/语义化.png)
### 方案一
``` html
<div class="main">
     <div class="h2">标签的语义<a href="#">更多</a></div>
     <div class="p">段落1内容<span class="strong">强调内容</span></div>
     <div class="p">段落2内容</div>
</div>
```
上述代码添加CSS样式可以达到效果，但用的只是向div,span这样的无语义标签，我们从标签上看不出结构这样显然是不行的，我们需要用代码清晰表现出：“哪是标题”，“哪是内容”

### 方案二
```html
<div class="main">
    <h2>标签的语义 <a href="#">更多</a></h2>
    <p>段落一的各种内容.....<strong>强调的内容</strong></p>
    <p>段落二的内容。。。段落二的内容。。。</p>
</div>
```
方案二比方案一大有改进，从标签可以分清哪是标题哪是内容，也能看到哪被强调，但仔细看有a链接在h2标签中，虽然它们是在同一行，但a链接并不是属于标题！而且还是有无语义标签

### 方案三
```html
<main>
    <header class="title">
        <h2>标签的语义化</h2>
        <a href="#">更多</a>
    </header>
    <article class="content">
        <p>段落一的各种内容.....<strong>强调的内容</strong></p>
        <p>段落二的内容。。。</p>
    </article>
</main>
```
方案三又有一些进步，利用HTML5定义的新标签是语义化更加完美，写到这里基本上也就可以了，但其实我们还可以利用[ARIA](https://developer.mozilla.org/en-US/docs/Web/Accessibility/An_overview_of_accessible_web_applications_and_widgets#ARIA)(无障碍网页倡议)更加使代码完美。更加具有可读性。

### 方案四
```html
<main role="main">
    <header class="title"  role="heading">
        <h2>标签的语义化</h2>
        <a href="#">更多</a>
    </header>
    <article class="content" role="contentinfo">
        <p>段落一的各种内容.....<strong>强调的内容</strong></p>
        <p>段落二的内容。。。</p>
    </article>
</main>
```
现在可以看到标签中多了一些role属性，那是ARIA中定义的地标角色定义它们可以使屏幕阅读器更好的工作。当然并不是使用div这些标签就是不重视语义化，有些时候因为样式的需求必须使用这些无语义标签，这时我们就应该大胆使用它们。但能少用尽量少用。

## 参考
> https://zh.wikipedia.org/wiki/%E8%AF%AD%E4%B9%89%E5%8C%96
> http://www.w3school.com.cn/html5
> https://www.cnblogs.com/p2227/p/3586725.html
> https://blog.csdn.net/hui1845/article/details/54955251
> https://developer.mozilla.org/en-US/docs/Web/Accessibility/An_overview_of_accessible_web_applications_and_widgets#ARIA
