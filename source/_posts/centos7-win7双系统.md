---
title: centos7-win7双系统
date: 2016-12-23 10:03:16
tags: centos
---

#手记

不是教程，只是本人的实践记录，以便后来再参看回忆。

###原因

因为公司原因，开发的时候一直要在各种系统上写东西。

不胜其烦。

最终决定把家里的电脑改成win+centos双系统，并从各个地方远程centos。

打算一劳永逸。

###开工

实践出真知，坑是不趟不平。

本人是win7 32位电脑，下载的centos 7 iso文件。

####plan a
一开始的想法是在win7上分两个新区，一个10g，一个100g。

10g放centos 7安装iso，100g为安装目录。

#####步骤：
硬盘工具隔离出110g空间。

分区助手 创造出两个盘：k：10g j：100g。（设置为ext3）

然后下载了wingrub eacybcd

参看教程 http://blog.sina.com.cn/s/blog_86e874d30101e3d8.html

最后启动可以识别到centos启动项，看来grub是没什么问题了。

但安装卡在mount:/dev/sr0

按照百度的方法都不起什么作用，无论是改initrd.img的挂载盘还是更改kenerl什么。

It makes no sence 宝贝儿，至少对我是。

开启plan b

####plan b

翻出个U盘，8g的，用ultraiso把centos 7导入

启动项设置为u盘启动

u盘制作网上教程一大把，操作简单坑少，见谅这里不贴了

顺利的一马平川的，进度条似乎在嘲讽我刚才那绞尽脑汁的脸

哥认了，你抓到耗子了，是好猫。

centos 设置成开发机。

看教程建议swap挂载内存2倍，我就挂了8g，多点应该没坏处，反正不差这点空间。

其余全放/了，因为我只开发，不放什么存储。90多g够用了。

安装完毕。

参看教程http://jingyan.baidu.com/article/e75aca856cca69142fdac673.html

###收尾

最后，还需要设置启动项，因为你安装完了win7启动没了呀

得进入centos的grub2里更改配置。

没什么坑，参看教程

http://m.blog.csdn.net/article/details?id=51419354

默认启动看心情设置成win7还是centos，就可以。

##心得

完成了什么小demo，还是记录一下实践流程和参考教程。

当时记录，要不难以复盘。

要不时间久了再做，浪费自己时间。




