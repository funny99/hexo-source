---
title: Hexo Introduction
date: 2016-04-30 17:00:56
tags: [hexo, 使用入门]
---

# 一 简介
Hexo是一个快速、简洁且高效的博客框架（静态博客生成器）。Hexo使用Markdown解析文章，在几秒内，即可利用靓丽的主题生成静态网页。

# 二 环境配置
#### 安装Node
#### 安装Git
#### 安装Sublime（可选）
#### 安装markdown编辑器（可选）

# 三 GitHub
注册账号、新建仓库（name必须和用户名一致，如funny99.github.io）、添加SSH公钥到『Account settings -> SSH Keys -> Add SSH Key』

# 四 安装hexo
``` bash
npm install -g hexo
```
# 五 初始化hexo
即生成项目代码到blog下
``` bash
hexo init <folder>
```
也可以cd到目标目录，执行 hexo init 
此处我的目录是：d://study/hexo/blog。以下都以这个目录为例 

# 六 生成静态页面
cd到你的init目录（d://study/hexo/blog），执行如下命令，生成静态页面至 public目录下
``` bash
hexo generate
```

# 七 本地启动
``` bash
hexo server
或者 hexo s
```
浏览器输入 http://localhost:4000 就可以看到效果。默认生成的博客文章是 hello-world

# 八 部署
1、与github建立关联
找到配置文件_config.yml,找到最后 deploy，修改成：
``` bash
deploy:
  type: git
  repository: <您的github仓库地址>
  branch: master
```
修改配置文件时注意YAML语法，参数冒号:后一定要留空格 
2、安装：
``` bash
npm install hexo-deployer-git --save
```
3、部署
``` bash
hexo deploy
```
然后在浏览器输入http://<您的github仓库名称>/，就可以看到您的博客了（此处地址必须以github.io结尾？？）
4、每次部署的时候，可以按以下三个步骤来执行
``` bash
hexo clean
hexo generate
hexo deploy
```
hexo clean: 清空public目录
hexo generate：编译生成public目录
hexo deploy: 部署到github
![本地代码结构](https://raw.githubusercontent.com/funny99/funny99_static/master/images/bendi-mulu.png)
![github代码结构](https://raw.githubusercontent.com/funny99/funny99_static/master/images/github-mulu.png)
由上图可见，public即是hexo生成的可在浏览器环境执行的代码

# 九 写博客
``` bash
hexo new [layout] "postName"
```
其中layout是可选参数，默认值为post。有哪些layout呢，请到scaffolds目录下查看，这些文件名称就是layout名称。当然你可以添加自己的layout，方法就是添加一个文件即可，同时你也可以编辑现有的layout，比如post的layout默认是\scaffolds\post.md
postName就是你这篇文章的标题

这里使用的是markdown语法。有关markdown的语法介绍，请看这篇<http://funny99.github.io/2016/04/30/markdown-grammar/>

# 十 切换主题
1、下载主题(这里以modernist为例)
``` bash
git clone https://github.com/heroicyang/hexo-theme-modernist.git themes/modernist
```
2、在配置文件中修改默认主题
打开_config.yml，修改
theme: modernist

# 十一 使用评论系统
以多说为例  
在多说设置你的short_name:  
很多人问short_name是什么，其实就是在http://duoshuo.com/create-site/自己申请的
copy一份通用代码，粘贴到你的/themes/modernist/layout/_partial/comment.ejs里面

# 十 遇到的问题
