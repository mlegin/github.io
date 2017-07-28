---
title: centos to mac
date: 2017-07-28 09:12:04
tags:
---

## centos 转 mac

开发环境还是迁移到mac吧，很多效率更高

需要更改的东西，要在这里记录一下

### brew

首先 类同于centos下的yum，需要安装一下mac下的依赖安装工具homebrew

```
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

一行搞定

### 搭建ss

购买ss

下载mac下ss工具

配置

具体方法百度即可

### 安装proxychains4

为了命令行时候能用着更方便

```
brew install proxychains-ng
```

编辑配置文件 

```
vim /usr/local/etc/proxychains.conf
```
注释掉sock4，添加下句

```
socks5 127.0.0.1 1080
```
#### 使用

举例

```
proxychains4 git push
```
### composer

平常写php composer不能少

```
curl -sS https://getcomposer.org/installer | php
```

```
mv composer.phar /usr/local/bin/composer
```

### npm

好久没在这台mac上写程序了，更新下node

然后发觉原来我没用brew管理npm，造成全局安装会报不少错

两篇文章帮了大忙，删除了半天

http://blog.csdn.net/u010828718/article/details/50488526

http://www.jianshu.com/p/20ea93641bda


然后来个淘宝镜像

```
npm config set registry https://registry.npm.taobao.org
npm info underscore
```

sudo 安装全局不成功
不加sudo 安装才成功

