---
title: "windows和macos平台下单屏显示器切换信号源"
date: 2023-05-21T15:37:32+08:00
draft: false
---

# 前言
用了双屏方案，无论是双横屏，还是一横一竖屏，都对我的脖子不友好，对打游戏也不友好，最后忍痛卖掉一块屏幕回归单屏，整个世界都清爽了，而且win和mac下都支持多桌面，但屏也可以很爽。但是win和mac之间的信号输入切换，每次都调显示器太麻烦了，其实可以用简单的快捷键实现，这样两个平台都可以随意切换信号源。
# Windows
用到的工具软件：
1. [ControlMyMonitor](http://www.nirsoft.net/utils/control_my_monitor.html)
2. [WinHotKey](https://www.directedge.us/content/winhotkey/)

## ControlMyMonitor
下载ControlMyMonitor并把它放在一个固定的位置，比如D盘的一个文件夹里，然后打开这个软件，如下图所示，记住Input Select的数值，代表的是当前输入源的数值
![](https://vip2.loli.io/2023/05/21/dR6MNf14uGkKx38.png)

## WinHotKey
第二步打开WinHotKey键位映射软件，新建一个热键。

![](https://vip2.loli.io/2023/05/21/fObx1ryiVCQtsKj.png)
两个小细节：
1. /SetValue Primary 60 15 里面的15是显示器输入源数值，在ControlMyMonitor中显示我当前的输入源是8，最大的数值是14，我通过一个一个数值测试，最终确定7才是我要切换的输入源，最后，我实际的命令也就设置成了/SetValue Primary 60 7
2.  台式机用/SetValue Primary是没问题的，Primary这个指令是主显示器的意思，台式机如果只有一个显示屏当然就是主显示器，用这条指令没毛病。但是笔记本可是自带显示器，外屏扩展使用的，那就是副显示器。所以这条代码就失效了，可以用 /SetValue "\\.\DISPLAY1\Monitor0" 60 7 代替（根据实际情况调整）

# MacOS

安装[BetterDisplay](https://github.com/waydabber/BetterDisplay)，绑定快捷键切换输入源即可



