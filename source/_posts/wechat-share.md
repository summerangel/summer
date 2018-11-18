---
layout: '[layout]'
title: Wechat share config
date: 2018-07-18 22:25:17
tags: wechat
---

# One: Add domain

[Login in the Wechat Official Accounts](https://mp.weixin.qq.com/),find the Setting --> Official Accounts Setting in the left down slide bar,and you will see Official Accounts Setting in the right main area,then switch to the tab Function Setting,and find the JS interface safety domain in this tab,and the click the Setting button after it,you will see a txt file in the popup dialog,download it and put it in the server besides in your online website root,make sure it can be previewed after putting it in,the you add the project's domain in this page you are editting,then save it.
[Click here to see steps with picture](https://jingyan.baidu.com/article/fa4125acfd4cdc28ac7092f4.html)

# Two: Add IP white list

[Login in the Wechat Official Accounts](https://mp.weixin.qq.com/),find the Development --> Basic Config in the left down slide bar,and you will see the Official Accounts Develop Info in the right main area,there exists a title show IP white list: click View button,and click Modify button,add the related IP.
[Click here to see steps with picture](https://jingyan.baidu.com/article/4e5b3e1904fccc91901e241c.html)

# Three: About update

After changing a new Official Accounts,don't forget to update the appId and appSecret in your code.

# Last: Whatever

When you need to share with pretty title and image,above config in Wechat Official Accounts is necessary.This article is written in vscode, the new editor vscode is really awesome.