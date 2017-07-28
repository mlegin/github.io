---
title: hexo 多电脑同步
date: 2017-07-28 09:55:34
tags: hexo
---

# hexo 多电脑同步问题

## 问题

要迁移主要开发环境，hexo文件得想个优雅的方法挪过来，并且原来就有hexo文件的备份问题也浮出水面，如果source文件夹下的md文件丢失，那可没处哭去，索性研究一下，把这两个问题都解决。

## 思路

参考知乎上各位大神的主要思路，现解决方法如下

在git上部署master和hexo两个分支，master主要用于站点deploy，hexo用于存放md，theme等主要文件

最终测试了下，效果良好，在本人mac上成功迁移

## 操作

在git上master分支存放deploy，hexo分支存放目录下git的push提交

旧电脑中把hexo文件push到git不再赘述，在新电脑上操作如下

```
hexo init myblog
cd myblog
rm _config.yml
rm package.json #我在github中的hexo分支有这两个rm了的文件
git remote add origin <你的github地址>
git add .
git commit -m "init"
git pull origin hexo
hexo g
npm install hexo-deployer-git --save
hexo d
```
遇到 ERROR Deployer not found: git ，记得

```
npm install hexo-deployer-git --save
```
