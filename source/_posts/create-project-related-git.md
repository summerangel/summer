---
layout: '[layout]'
title: create-project-related-git
date: 2018-04-23 18:16:13
tags: git
---

#### avoid forgetting(every time forgot how to do)


1、 Step One: create a repo on github first, then copy the https's url;

2、 Step Two: under your local project folder's root path execute: git init;

3、 Step Three: then execute: git add .

4、 Step Four: then execute: git commit -m "here is some comment about what will be committed";

5、 Step Five: then execute: git remote add origin (here is the url copied in step one);

6、 Step Six: then execute: git pull origin master

    if you confront this problem: fatal: refusing to merge unrelated histories.
    
    you can execute this command like this: git pull origin master --allow-unrelated-histories

7、 Step Seven: then execute: git push -u origin master



                              
