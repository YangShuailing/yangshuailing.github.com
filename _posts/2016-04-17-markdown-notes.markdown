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

笔者在学习Markdown写blog时做的一些笔记笔记。学完这些Markdown的基本使用已经不成问题。Markdown的编辑器有很多，笔者推荐使用Sublime，一个很强大的的文本编辑器。
首先，我们需要安装package control组件，使用快捷键 Ctrl+~或者通过View->Show Console菜单打开命令行，粘贴如下代码：
 
	 import urllib.request,os; pf= 'Package Control.sublime-package';ipp= sublime.installed_packages_path();urllib.request.install_opener(urllib.request.build_opener(urllib.request ProxyHandler()));open(os.path.join(ipp,pf),'wb').write(urllib.request.urlopen('[http://sublime.wbond.net/(http://sublime.wbond.net/)'+pf.replace(' ','%20')).read())

如果在Preferences → Package Settings 中看到 Package Control 这一项，说明安装成功。
在安装好package control组件之后，还需要安装一下两个插件。按下Ctrl+Shift+P调出命令面板，输入install， 调出 Install Package 选项并回车，然后输入要安装的插件名称，在列表中选中要安装的插件即可。

- MarkDown Editing：支持Markdown语法高亮；支持Github Favored Markdown语法；
- MarkdownPreview：按CTRL + B生成网页HTML；在最前面添加[TOC]可以自动生成目录；

## 1. 标题设置（让字体变大，和word的标题意思一样）
<!-- 生成目录使用 [TOC] 。 -->
在Markdown当中设置标题，有两种方式：

- 第一种：通过在文字下方添加“=”和“-”，他们分别表示一级标题和二级标题。
  在单独一行里输入3个或者以上短横线('-','*','_')以下每一行都产生水平分割线。使用 --- 作为水平分割线时，要在它的前后都空一行，防止 --- 被当成标题标记的表示方式。
- 第二种：在文字开头加上“#”，通过“#”数量表示几级标题。（一共只有1~6级标题，1级标题字体最大）。
‘#’和标题之间最好加一个空格。不要问我为什么，貌似有时候不会被识别为标题？已经忘记自己为什么要加空格了，也许是任性。

<!-- # 一级标题 -->

    First Level Header
    ==================
    Second Level Header
    -------------------
    # Header 1 (equal '=')
    # Header 2 (equal '-')

    #  一级标题
    ## 二级标题
    ### 三级标题
    #### 四级标题
    ##### 五级标题
    ###### 六级标题

## 2. 块注释（blockquote）
通过在文字开头添加“>”表示块注释。（当>和文字之间添加五个blank时，块注释的文字会有变化。）

**注意**：
引用的区块内也可以使用其他的 Markdown 语法，包括标题、列表、代码区块等。

## 3. 段落
Markdown通过一个以上的空行来区别不同段落，一般段落没有缩进，如果需要首行缩进
可用`&emsp;`(全方大空白)或`&ensp;`(半方大空格)

## 4. 强调
将需要设置为斜体的文字两端使用1个“*”或者“_”夹起来

    *斜体*
    **粗体**
    ***粗斜体***  

##  5. 列表
在文字开头添加(`*`,`+`,`-`)实现无序列表。但是要注意在(`*`,`+`,`-`)和文字之间需要添加空格。（建议：一个文档中只是用一种无序列表的表示方式）

    - 内容
    - 
    - 
    或
    * 内容
    * 
    *
 
## 6. 有序列表
使用数字后面跟上句号。（还要有空格）

    1. 内容
    2. 
    3. 

## 7. 链接（Links）
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
 
## 8. 图片（Images）
图片的处理方式和链接的处理方式，非常的类似，只需使用`![](图片链接地址)`这样的语法即可。
内联方式：

    ![alt text](/path/to/img.jpg "Title")
引用方式：

    ![alt text][id] 
    [id]: /path/to/img.jpg "Title"

<!--  -->
注：插入图片的语法和链接的语法很像，只是前面多了一个'!'。

## 9. 代码（HTML中所谓的Code）
实现方式有两种：

第一种：简单文字出现一个代码框。使用`<blockquote>`。（这里，到的是左上角的ESC键）

第二种：大片文字需要实现代码框，使用Tab或者四个空格。也可以使用```来表示代码块。

## 10. 引用
在我们写作的时候经常需要引用他人的文字，这个时候引用这个格式就很有必要了，在 Markdown 中，你只需要在你希望引用的文字前面加上 > 就好了。使用 > 表示引用， >> 表示引用里面再套一层引用，依次类推。


## 11. 表格
示例相关代码：

    | Id            | Name          | Age   |
    | ------------- |:-------------:| -----:|
    | 110           | zs            |   17  |
    | 111           | ls            |   18  |
    | 112           | zw            |   19  |

显示效果：

| Id            | Name          | Age   |
| ------------- |:-------------:| -----:|
| 110           | zs            |   17  |
| 111           | ls            |   18  |
| 112           | zw            |   19  |

其中：

- ------: 为右对齐。
- :------ 为左对齐。
- :------: 为居中对齐。
- ------- 为使用默认居中对齐。

## 12. 其他

- 使用 \ 表示反斜杠。在你不想显示Markdown标记时可以使用反斜杠。
- Markdown语法会忽略首行开头的空格，如果要体现出首行开头空两个的效果，可以使用 全角符号下的空格 ，windows下使用 shift+空格 切换。
- 使用 ~~ 表示删除线。注意``~~``和要添加删除线的文字之间不能有空格。
- 使用``[你好](#jump)`` 将`你好`设置为一单击即跳转到`hehe`所在位置的效果。
- 使用 [TOC] 生成目录。
- 使用 标签: 或者 Tags: 表示标签标记。
- 使用`[^footer]` 可以表示注脚。

## 参考： 

* 以上内容根据[官方文档](http://daringfireball.net/projects/markdown/basics)基本文档进行整理。
* [Markdown官方网站](http://daringfireball.net/projects/markdown/) 
* 推荐一款[在线的Markdown编辑器](https://stackedit.io/)