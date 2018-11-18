---
layout: '[layout]'
title: Awesome Charles
date: 2018-06-14 22:33:37
tags: software
---


#### Modify request

Today I get another function about Charles,which heard of my colleague.Actually I installed Charles before,but I only used it to fetch request from app,for it can't be opened in browser,we can modify the request params and also the response,steps are:

  1、Find the url you want to modify;
  2、Then right click it, select the option Breakpoint;
  3、Then repeat the url(you can use quick key to execute this: shift + command + R);
  4、Then the process will open another window to the breakpoint you set;
  5、At this time, you can click the tab Edit request or Edit the response option;
  6、After modified, click the button execute to continue;
  7、Finally the modified url completed, the process is done.

  Following give some screenshots to express this:
  {% asset_img screen_one.jpg step one %}
  {% asset_img screen_two.jpg step two %}
  {% asset_img screen_three.jpg step three %}

#### Map Local(get mock data from local file)

Select Tool --> Map local: this allow you to get mock data from your own computer which you discussed with back-end developer when the back-end developer isn't ready to provide the real data.

#### Change the speed of network

You can lower the speed of network for some extreme condition.

#### Over

The three of above is constantly be used by our front-end developer,and is extremely useful,saving a lot of time to communicate with back-end developer.

#### Plus

If we want to modify some request in one page,we should keep in mind that whether the request is called in that page,if not, we should better make breakpoint in domain.
give a screenshot to express this,refer to [this article](https://cloud.tencent.com/developer/article/1147452):
 {% asset_img screenshot_four.png step four %}
