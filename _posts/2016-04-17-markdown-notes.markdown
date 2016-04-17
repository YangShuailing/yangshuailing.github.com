---
layout: post
title: "Markdown 学习笔记"
date: 2016-04-17
author:     "Yang"
tags:
    - markdown
    - sublime
    - 笔记
---

# Markdown 学习笔记

笔者在学习Markdown写blog时做的一些笔记笔记。学完这些Markdown的基本使用已经不成问题。Markdown的编辑器有很多，笔者推荐使用Sublime，这是一个很简便的编辑文本器。
首先，我们需要安装package control组件，使用快捷键 Ctrl+~或者通过View->Show Console菜单打开命令行，粘贴如下代码：
 
	 import urllib.request,os; pf= 'Package Control.sublime-package';ipp= sublime.installed_packages_path();urllib.request.install_opener(urllib.request.build_opener(urllib.request ProxyHandler()));open(os.path.join(ipp,pf),'wb').write(urllib.request.urlopen('[http://sublime.wbond.net/(http://sublime.wbond.net/)'+pf.replace(' ','%20')).read())

如果在Preferences → Package Settings 中看到 Package Control 这一项，说明安装成功。
在安装好package control组件之后，还需要安装一下两个插件。按下Ctrl+Shift+P调出命令面板，输入install， 调出 Install Package 选项并回车，然后输入要安装的插件名称，在列表中选中要安装的插件即可。

- MarkDown Editing：支持Markdown语法高亮；支持Github Favored Markdown语法；
- MarkdownPreview：按CTRL + B生成网页HTML；在最前面添加[TOC]可以自动生成目录；

### 1. 标题设置（让字体变大，和word的标题意思一样）
在Markdown当中设置标题，有两种方式：

- 第一种：通过在文字下方添加“=”和“-”，他们分别表示一级标题和二级标题。
- 第二种：在文字开头加上 “#”，通过“#”数量表示几级标题。（一共只有1~6级标题，1级标题字体最大）

### 2. 块注释（blockquote）
通过在文字开头添加“>”表示块注释。（当>和文字之间添加五个blank时，块注释的文字会有变化。）

### 3. 斜体
将需要设置为斜体的文字两端使用1个“*”或者“_”夹起来

### 4. 粗体
将需要设置为斜体的文字两端使用2个“*”或者“_”夹起来

###  5. 无序列表
在文字开头添加(*, +, and -)实现无序列表。但是要注意在(*, +, and -)和文字之间需要添加空格。（建议：一个文档中只是用一种无序列表的表示方式）

### 6. 有序列表
使用数字后面跟上句号。（还要有空格）

### 7. 链接（Links）
Markdown中有两种方式，实现链接，分别为内联方式和引用方式。
内联方式：This is an [example link](http://example.com/)（http://example.com/）.
引用方式：
I get 10 times more traffic from [Google][1] than from [Yahoo][2] or [MSN][3].  

[1]: http://google.com/        "Google" 

[2]: http://search.yahoo.com/  "Yahoo Search" 

[3]: http://search.msn.com/    "MSN Search"

    [1]: http://google.com/        "Google" 
    [2]: http://search.yahoo.com/  "Yahoo Search" 
    [3]: http://search.msn.com/    "MSN Search"
 
### 8. 图片（Images）
图片的处理方式和链接的处理方式，非常的类似。
内联方式：

    ![alt text](/path/to/img.jpg "Title")

引用方式：

    ![alt text][id] 

    [id]: /path/to/img.jpg "Title"

### 9. 代码（HTML中所谓的Code）
实现方式有两种：
第一种：简单文字出现一个代码框。使用`<blockquote>`。（`不是单引号而是左上角的ESC下面~中的`）
第二种：大片文字需要实现代码框。使用Tab和四个空格。

### 10. 脚注（footnote）
实现方式如下：

     hello[^hello]
     [^hello]: hi

### 11. 下划线
在空白行下方添加三条“-”横线。（前面讲过在文字下方添加“-”，实现的2级标题）


## References： 

以上内容根据[官方文档](http://daringfireball.net/projects/markdown/basics)基本文档进行整理

[Markdown官方网站](http://daringfireball.net/projects/markdown/) 

推荐一款[在线的Markdown编辑器](https://stackedit.io/)