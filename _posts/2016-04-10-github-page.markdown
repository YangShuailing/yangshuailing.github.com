---
layout: post
title: "使用GIthub搭建个人博客"
date:   2016-04-10  
categories: [git-pages, jekyll, markdown]
tags:
    - blog
    - 博客
    - jekyll
    - github page
---

# 1.前言

Github作为最大的程序员交友网站，功能相当强大，今天就介绍一下如何使用github搭建自己的个人blog主页。github是提供Pages功能的，允许用户自定义项目首页，用来替代默认的源码列表。所以，github Pages可以被认为是用户编写的、托管在github上的静态网页。而Jekyll（发音/'dʒiːk əl/，"杰克尔"）是一个静态站点生成器，它会根据网页源码生成静态文件。它提供了模板、变量、插件等功能，所以实际上可以用来编写整个网站。那么整体思路是在本地编写符合Jekyll规范的网站源码，然后上传到github，由github生成并托管整个网站。编写博客通常使用markdown来进行，因为markdown使用起来十分方便。 
Github Pages有以下几个优点：

- 轻量级的博客系统，没有麻烦的配置
- 使用标记语言，比如Markdown
- 无需自己搭建服务器
- 根据Github的限制，对应的每个站有300MB空间
- 可以绑定自己的域名

当然也有缺点：

- 使用Jekyll模板系统，相当于静态页发布，适合博客，文档介绍等。
- 动态程序的部分相当局限，比如没有评论，不过还好我们有解决方案。
- 基于Git，很多东西需要动手，不像Wordpress有强大的后台
![]({{ site.BASE_PATH }}/img/in-post/create blog/2016-04-17-github-page.jpg)

# 2. 具体搭建过程

## 2.1 Github-pages
第一步：创建个人站点
    没有Github账号的童鞋需要先注册一个[Github](https://github.com/)，完成注册后，新建一个**repository**,命名为`你的用户名.github.io`或者`你的用户名.github.com` ，这个命名规则必须的，`命名规则一定要按照这个格式来`,这个repository就是你账号的github-pages。
    ![]({{ site.BASE_PATH }}/img/in-post/create blog/step1.jpg)

第二步：设置站点主题
进入资源-setting
    ![]({{ site.BASE_PATH }}/img/in-post/create blog/step2.jpg)

第三步
点击automatic page generator，然后点击Continue to layouts,然后选择主题并发布，等几分钟输入刚才注册的用户名XXX.github.io即可访问了。
![]({{ site.BASE_PATH }}/img/in-post/create blog/step3.jpg)

## 2.2 安装Jekyll
Jekyll是一种简单的、适用于博客的、静态网站生成引擎。它使用一个模板目录作为网站布局的基础框架，支持Markdown、Textile等标记语言的解析，提供了模板、变量、插件等功能，最终生成一个完整的静态Web站点。说白了就是，只要安装Jekyll的规范和结构，不用写html，就可以生成网站。

jekyll本地环境搭建：

Jekyll是基于**Ruby**环境的，下载最新的RubyInstaller并安装(我下载的是rubyinstaller-1.9.3-p194.exe)，设置环境变量，path中配置C:\Ruby193\bin目录，然后在命令行终端下输入gem update --system来升级gem；

下载最新的DevKit，DevKit是windows平台下编译和使用本地C/C++扩展包的工具。它就是用来模拟Linux平台下的make,gcc,sh来进行编译。但是这个方法目前仅支持通过RubyInstaller安装的Ruby，并双击运行解压到C:\DevKit。然后打开终端cmd，输入下列命令进行安装：

    cd C:\DevKit
    ruby dk.rb init 
    ruby dk.rb install 
 
完成上面的准备就可以安装Jekyll了,因为Jekyll是用Ruby编写的,最好的安装方式是通过RubyGems(gem):

 
    gem install jekyll  //安装jekyll
    gem install pygments.rb //用于语法高亮
    gem install paginate  //分页
    gem install rdiscount //解析Markdown标记

pygments的安装需要python环境的支持，具体可以去[pygments官网](http://pygments.org/)查看。

安装完jekyll后，我们可以在*D:\Ruby22-x64\lib\ruby\gems\2.2.0\gems\jekyll-3.1.2*
找到jekyll，将该路径添加至PATH。

进入你博客的目录，运行命令：

    jekyll serve --watch

## 2.3 jekyll目录结构

[jekyll官网](http://jekyllrb.com/docs/home/)给出的目录结构如下图：

![]({{ site.BASE_PATH }}/img/in-post/create blog/2016-4-11_jekyllcatalogue.png)

可能生成的目录结构会有点不一样，但是基本是一样的大致的用途引用自一个简书作者[原文](http://www.jianshu.com/p/609e1197754c)：

- layouts：用于存放模板的文件夹。_layouts中的模板一般指向了_includes/themes中的模板。目录是用来存放模板的，在这里你可以定义页面中不同的头部和底部。
- posts：用于存放博客文章的文件夹。 _posts中的数据文档，通过注入_layouts定义的模板，通过jekyll --server最终生成的静态页面在_sites目录。目录是用来存放你的文章的，一般以日期的形式书写标题。
- css：存放博客所用css的文件夹,比如主题文件以及高亮文件都是放在此处的。
- coinfig.yml：jekyll的配置文件,站点的全局变量在_config.yml中定义，用site.访问；页面的变量在YAML Front Matter中定义，用page.访问，更多的模板变量可参考模板数据。
- assets: 渲染页面的CSS和JS文档在assets/themes中
- index.html：你的页面首页。
- includes: 用于存放一些固定的HTML代码段，文件为.html格式，可以在模板中通过liquid标签引入，常用来在各个模板中复用如 导航条、标签栏、侧边栏之类的在每个页面上都一样不变的内容，需要注意的是，这个代码段也可以是未被编译的，也就是说也可以使用liquid标签放在这些代码段中。
    1) includes/JB中有一些常用的工具，用于列表显示、评论等；
    2) includes/themes中可参看主题的相关html文档。
    3) includes/themes中的主题一般包含default.html、post.html和page.html三个文档。default.html定义了网站的最上层框架（模板），post.html和page.html是其子框架（模板）。
    4) 生成好的html子页面通过default.html的`content`变量调用，生成整个页面。
<!--  -->
<!--  -->


接着你就可以通过访问*127.0.0.1:4000*或者*http://localhost:4000* ,看成的博客主页面了，接下来可以推荐的一个[jekyll的主题站
](http://jekyllthemes.org/)。


## 2.4 使用Markdown编写博文

Markdown是一种非常方便的标记语言，能够用简单的标记语法，让普通的文本具有一定的格式。需要的可以看一下我的blog，[markdown语法](http://yangshuailing.github.io/2016/04/17/markdown-notes/)学起来很快。

# 后记

我也是刚开始学习写blog，把自己的学习历程记录下来，希望对别人有所帮助。
感谢：
- [Hux](http://huangxuan.me/)
- [小胡](http://hujunyu1222.github.io/)
- [简书](http://www.jianshu.com/)













