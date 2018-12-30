---
title: A general problem caused by the path
date: 2018-12-30 21:44:46
tags: daily backup
---


#### Multilayer routing not refresh

 I was intended to record this in my last blog, but since it is a general problem may be met by every developer, so I wrote this problem in a new blog,hope help someone and remind myself.
 
 In last blog, I deployed a static project successfully by building the project(which use webpack)、copy the builded file to the server and config the nginx to proxy the website(if you install git in your server and git clone the project from your github, this copy steps can be ignored), and the refresh problem was solved in last blog, it seems normal for a time, but later I found a problem, the refresh is only taking effect in the first layer of routing, if multilayer routing, the page will become a white screen, for example to make it clearly:
  
  the first layer routing like this: `/card/card-list`, it is right and refreshable; 
  but multilayer routing like this: `/card/card-detail/123`, is white screen, or maybe right,but
  white screen when you refresh.
  
#### Location the cause

It takes me hours to find the cause, still no result, and almost want to change to the hashroute. I thought the cause is wrong config of nginx, but I'm not good at nginx, just the degree of basic knowledge, so I turn to a niubility guy for help, he soon found the key point.The request is not right,it looks like this,

{% asset_img cause_find.jpeg the requst looks like%}

#### The way to solve it

If you using create-react-app, go to the file: `config -> webpack.config.prod.js`, change 
```javascript
const publicPath = paths.servedPath;
```
to
```javascript
const publicPath = '/card/'; // you should replace the card with your own prefix
```

> Reference

[This blog](http://blog.codingplayboy.com/2017/12/26/react-router-browserhistory-404/) to some extents did help.


