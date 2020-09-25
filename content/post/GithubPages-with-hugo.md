+++
title = "Github Page with hugo"
date = 2020-09-09T00:00:00+08:00
description = "Github Pages with hugo"
tags = ["github", "hugo"]
+++

Github Page with hugo

<!--more-->


```bash

$ brew install hugo
$ hugo new site blog
$ cd blog
$ git init
$ git remote add origin https://github.com/your-name/blog.git
$ git submodule add https://github.com/amzrk2/hugo-theme-fuji.git themes/fuji
$ hugo server -D
# 浏览器访问 http://localhost:1313/
$ git add -A
$ git commit -m 'init commit'
$ git push origin master
$ hugo			# 生成 public 目录

$ cd 
$ git clone https://github.com/wangyaoxu/wangyaoxu.github.io.git
$ cd wangyaoxu.github.io/
$ cp -R ~/blog/public/* .
$ git add -A
$ git commit -m 'init commit'
$ git push origin master


```


### Links
- http://chungwei.github.io/2016/04/25/blog-hugo-github/