---
title: about-svn
date: 2018-01-25 21:30:12
tags: svn
---

open ~/.npmrc
#### just simple use about svn

      1、从线上地址拷贝代码到本地：svn checkout (线上地址);
  
      2、更新本地的svn中的代码：svn up;
    
      3、更改npm的源：打开.npmrc文件：open ~/.npmrc；
  
      4、查看文件：cat package.json
  
      把下列代码复制进.npmrc文件中：
   
       sass_binary_site=https://npm.taobao.org/mirrors/node-sass/
       phantomjs_cdnurl=http://cnpmjs.org/downloads
       electron_mirror=https://npm.taobao.org/mirrors/electron/
       python_mirror=https://npm.taobao.org/mirrors/python
   
   
  以上，安装依赖时会快很多。