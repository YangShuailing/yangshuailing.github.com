---
layout: post
title: "搭建个人独立博客"
date:   2016-04-11 21:57:00 +0800
categories: [git-pages, jekyll, markdown]
tags:
    - blog
    - 博客
    - jekyll
    - github page
---

# 1.前言


我早就想搭建一个自己的博客了，由于拖延症晚期，所以一直到现在我才准备真正动手。*_(:зゝ∠)_* 不多说，进入正题。
我主要采用的是`github-pages` + `jekyll` + `markdown` 这一套架构。主要分工如下：

- github-pages用于显示博客的主页，相当于把自己的博客挂在github上
- jekyll用于将用markdown写的博客转换为静态的html页面
- markdown用于编写博客，十分方便。


# 2. 具体搭建过程


## 2.1 Github-pages

想要github-pages，首先你要拥有一个[Github](https://github.com/)账号。
完成注册后，新建一个**repository**,命名为`你的用户名.github.io`或者`你的用户名.github.com` ，这个命名规则必须的，这个repository就是你账号的github-pages，**每个账号只有一个！**，而对于其他的项目，每个项目可以有多个git-pages。
现在是个空的repository，我们暂时不管它。


## 2.2 安装Jekyll
Jekyll是默认支持markdown语法的，[markdown语法](http://daringfireball.net/projects/markdown/)简单易学，而且高效，无论是做笔记还是写心得都十分适合作为程序员的我们。

本地文件操作简单，不需要管理数据库。新建了一个文件，刷新一下，页面上就有了发布的文件。

+ Jekyll是基于**Ruby**环境的，如果你是使用MAC的用户，那你的电脑里应该默认安装了Ruby环境，而像我这样的windows8用户，就需要先[下载Ruby](http://rubyinstaller.org/downloads/)环境安装以及对应的**development kit**。ruby安装完后,安装完后一定记得将ruby添加的PATH中（安装的时候钩选**add to PATH**选项），我们将下载的development kit解压，如下图：

![]({{ site.BASE_PATH }}/assets/img/2016-4-11_devkit.jpg)

通过cmd我们进入该目录，并且运行指令安装devlopment kit：

    ruby dk.rb init 
    ruby dk.rb install 



接下来就是安装jekyll了，运行指令：

    gem install jekyll      //安装jekyll
    gem install pygments.rb //用于语法高亮

pygments的安装需要python环境的支持，具体可以去[pygments官网](http://pygments.org/)查看。

安装完jekyll后，我们可以在*D:\Ruby22-x64\lib\ruby\gems\2.2.0\gems\jekyll-3.1.2*
找到jekyll，将该路径添加至PATH。

接下来就可以用jekyll新建自己的博客了！在cmd中，进入自己选定的目录，输入命令：

    jekyll new aaa //aaa是你指定的名字

则你就可以获得了一个default配置的博客了，如下图：

![]({{ site.BASE_PATH }}/assets/img/2016-4-11_newblog.jpg)

[jekyll官网](http://jekyllrb.com/docs/home/)给出的目录结构如下图：

![]({{ site.BASE_PATH }}/assets/img/2016-4-11_jekyllcatalogue.png)

可能生成的目录结构会有点不一样，但是基本是一样的，每个目录或文件的用途我自己还不是很懂，毕竟刚刚摸索，大致的用途引用自一个简书作者[原文](http://www.jianshu.com/p/609e1197754c)：

- _layouts：用于存放模板的文件夹。
- _posts：用于存放博客文章的文件夹。
- css：存放博客所用css的文件夹,比如主题文件以及高亮文件都是放在此处的。
- _coinfig.yml：jekyll的配置文件，里面可以定义相当多的配置参数。
- index.html：项目的首页。
- _includes: 用于存放一些固定的HTML代码段，文件为.html格式，可以在模板中通过liquid标签引入，常用来在各个模板中复用如 导航条、标签栏、侧边栏之类的在每个页面上都一样不变的内容，需要注意的是，这个代码段也可以是未被编译的，也就是说也可以使用liquid标签放在这些代码段中。

可以设置每个html文件的title(标题)和layout(布局)。比如index的layout一般是default。你也可以添加其他的页面，加上不同的layout。

定制自己独一无二的博客，离不开上面的文件及文件夹。

进入你博客的目录（就是刚刚用jekyll new的目录），运行命令：

    jekyll serve --watch

接着你就可以通过访问 *127.0.0.1:4000* 或者*http://localhost:4000* 看到生成的博客主页面了：

![]({{  site.BASE_PATH}}/assets/img/2016-4-11_frontpage.jpg)

初始比较简陋，后面可以慢慢自己折腾:-D ，网上别人推荐的一个[jekyll的主题站
](http://jekyllthemes.org/)。


## 2.3 使用Markdown编写博文

Markdown是一种非常方便的标记语言，能够用简单的标记语法，让普通的文本具有一定的格式。[markdown语法](http://www.appinn.com/markdown/)学起来很快。


### 2.3.1 使用Sublime Text编辑器 

首先说说我使用的文本编辑器，我是用**Sublime Text 3**来作为markdown编辑器。Sublime Text下我们需要先下载安装Markdown Editing和Markdown Preview 插件，具体步骤如下：

+ 点击Sublime Text中`Preferences`的`Packet Control`，输入install，选择install packets
+ 在插件库中分别安装`Markdown Editing`和`Markdown Preview`
+ 新建一个文件，以`.md`作为文件后缀，用sublime text打开即可使用markdown编辑了！


### 2.3.2 使用Markdown Preview生成HTML

编辑完文本后，我们输入`ctrl`+`shift`+`p`，补全Markdown Preview，可以看到有输出为HTML的选项，保存以后，可以用浏览器查看HTML的生成效果了，也就是你博文的效果了。

# 后记

第一篇博客，写的很多问题，不过至少已经磕磕碰碰地搭建了自己的博客，本篇主要记录一下大致的过程，以后我会慢慢摸索，包括**选择自己的博客风格**，**语法高亮**，**评论系统**等等，还有很多路要走，所以我也会继续更新本文。








