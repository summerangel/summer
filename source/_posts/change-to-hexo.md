---
title: change-to-hexo
date: 2017-10-22 16:21:25
tags: technique
---


## Steps

This is a blog to record some commands to publish the blog based on hexo to avoid forgetting.

if you want to use hexo too, you could see the doc in hexo's page,it tells you step by step.
the url is 
https://hexo.io/docs/

The main command:

firstly,you should have git and node installed,it is fundamentally for developers.

{% codeblock %}
npm install hexo-cli -g // the command to install hexo-cli

hexo init (folder's name) //init a hexo folder

cd (folder's name) //to the folder's root path

git init //at the folder's root path execute the command

hexo server  //run the project (the url to open it is http://localhost:4000)
{% endcodeblock %}

below are the commands you will used frequently:

{% codeblock %}
hexo new page (folder's name) // this command creates a new folder, usually under the source folder

hexo new [layout] (folder's name) //this command creates a new post which you can edit you blog
{% endcodeblock %}

finally, the deploy commands:

{% codeblock %}
 hexo clean
 hexo generate
 hexo deploy
{% endcodeblock %}

#### node version in my local: v8.4.0 (record here avoid version error for my own business)




