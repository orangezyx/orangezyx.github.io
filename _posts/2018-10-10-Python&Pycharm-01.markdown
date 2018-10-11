---
layout: post
title:  "正确解锁Python&Pycharm2018的姿势（一）"
date:   2018-10-10 +0800
author: Rogister
categories: Programs
---
躺好了，快点进来Get这些技巧

# 导语

![TIM截图20181011184652.png](https://i.loli.net/2018/10/11/5bbf2a237ac4c.png)
这张图来自2018年10月`Tiobe 编程语言排行榜`，Python 排行第四，仅次于Java和C。可见现在其在业界的影响力，作为一名程序员，如何正确地搭建好开发环境和开发工具是我们必须点满的技能。

# 背景
Python身为一个优秀的跨平台，开源的强大的面向对象的程序设计语言，由于其简洁，可扩展，已被逐渐广泛应用于系统管理任务的处理和Web编程

# 安装Python

很高兴地告诉大家python完全开源，大家可以直接免费下载安装
官网：[Python](https://www.python.org)

![TIM截图20181010230232.png](https://i.loli.net/2018/10/10/5bbe14a595152.png 'Python 官网')

看到这个纯英文的界面，小伙伴们现在表情截图一定是内心恐惧

##### 不要慌！

只需知道 Download 下载这个单词就够了

单击 `Download` 链接下载

![TIM截图20181010230943.png](https://i.loli.net/2018/10/10/5bbe164353516.png)

下拉菜单中选择自己系统版本（以Windows为例）

目前大家常用的版本都是`3.x`  
从`2.7` 开始后，官网已经不再出`2.8`版本，鼓励大家选择`3.0`版本  
2020年开始停止`2.x`版本的使用  
笔者下载的是`3.7`的64位  
文件名为 `python-3.7.0-amd64.exe`   
选择自己的系统版本  
下载完成后运行安装程序

![TIM截图20181010231658.png](https://i.loli.net/2018/10/10/5bbe1802b979f.png)

~~然后选择 Install Now~~（这大概就是笔者的遗言了）

**当然不是！**

**一定要勾选 `Add Python 3.7 to PATH`**

之后选择 `Customize installation`

![TIM截图20181010232321.png](https://i.loli.net/2018/10/10/5bbe19aac787b.png)

默认安装全部功能，单击 `Next`

![TIM截图20181010232352.png](https://i.loli.net/2018/10/10/5bbe19aae7561.png)

选择安装路径，建议在盘的根目录下创建一个文件夹  
文件名为 Python + 版本号。例如笔者为Python37（安装目录尽量不出现中文）  
目录就是 C:\Python37  
点击 `Install` 开始安装  
接下来你在开始菜单就能发现 Python 的程序组了  

按下键盘上的 `Win` + `R` 键，打开运行窗口，输入CMD并单击回车或者点击确定

在弹出的命令行窗口中输入以下代码并单击回车

```
python -V
```

注意 `-V` 的 `V` 是大写

![TIM截图20181010233944.png](https://i.loli.net/2018/10/10/5bbe1d46d586a.png)

出现 Python 版本号，则说明安装成功

若失败，原因则是未把 Python 的安装目录添加到系统的环境变量中

右键计算机，选择属性

![1.png](https://i.loli.net/2018/10/10/5bbe1dbc84611.png)

单击左边的 `高级系统设置`

![TIM截图20181010234218.png](https://i.loli.net/2018/10/10/5bbe1de0c2247.png)

单击 `环境变量 `

![TIM截图20181010234311.png](https://i.loli.net/2018/10/10/5bbe1e1753e4a.png)

弹出的窗口选择 `系统变量` 标签的 `Path`

![TIM截图20181010234400.png](https://i.loli.net/2018/10/10/5bbe1e45ee7d4.png)

单击 `编辑`

![TIM截图20181010234457.png](https://i.loli.net/2018/10/10/5bbe1e816293b.png)

在弹出的窗口中点击 `新建`  
将安装 Python 的根目录写入，按照弹出窗口顺序一直单击确定  

系统环境变量添加完成  
再按照上面查看 Python 版本的步骤看看，是否成功了呢~

本文最后编辑于 2018-10-10 23:46:55