---
layout: '[layout]'
title: issue-record
date: 2018-08-10 00:57:45
tags: react-native
---

#### No complex redux to realise logout when token is expired

I was using a way found in github which not took effect at the end,I don't know why.but the way found is a good way to some extends. 
[here is the github address](https://github.com/mrarronz/react-native-blog-examples/blob/master/Chapter5-Navigation/ReactNavigationExample/src/screen/LoginScreen.js),may help someone.

tonight I found a really simply and good way to complete the function,which use the method of event,we listen the callback result of the interface,when gave us the code of token expired, then emit the event,and we add an listener in our my page(which usually the place of the logout button),this is the point,when the my page found the event, we call the logout function which we usually put it in the logout button,over, tested,it works.




