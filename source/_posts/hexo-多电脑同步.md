---
title: hexo 多电脑同步
date: 2017-07-28 09:55:34
tags: hexo
---

# hexo 多电脑同步问题

## 问题

要迁移主要开发环境，hexo文件得想个优雅的方法挪过来，并且原来就有hexo文件备份的问题，如果source文件夹下的md文件丢失，那可没处哭去，索性研究一下，把这两个问题都解决。

## 思路

参考知乎上各位大神的主要思路，现解决方法如下

在git上部署master和hexo两个分支，master主要用于站点deploy，hexo用于存放md，theme等主要文件

最终测试了下，效果良好，在本人mac上成功迁移

### hexo常用操作

复述下hexo操作

```
#将markdown文件生成为网页文件
hexo g 	
#本地预览生成的网页
hexo server 				
#发布到配置的地方（比如配置到github.io）
hexo d 	
```
### git各分支结构

master 这个分支存放发布后的网页文件，内容来源于hexo d操作，如何让hexo d到github上请参见其他网络教程

hexo 这个分支存放本地hexo目录几乎所有文件，包括source，package.json等，来源于git push origin hexo

## 初始hexo及git环境

### 方法1（不建议）

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
注意：以上操作并不好用，因为hexo会更新，此方法会造成很多merge，很麻烦

### 方法2

```
mkdir myblog
cd myblog
git init
git remote add origin <你的github地址>
git pull origin hexo 
npm i hexo --save
npm install 

```
	
这样不会因为配置文件冲突而报错

## 常用操作

### 发布文章
```
hexo d
```

### 保存md至github
```
#前面操作略过
git push origin hexo
```