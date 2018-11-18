---
layout: '[layout]'
title: React Native TextInput cannot transfer to chinese bug
date: 2018-06-27 21:25:19
tags: react-native
---


#### 一、A big bug of React Native

  I was use the rn library version 0.55.4,It has the same problem from version 0.55.0 to 0.55.5,after googling for this issue for almost one day,
  [Here are the mainly Gain](https://github.com/facebook/react-native/issues/18403) where the same problem other developer met, and after thinking
  for all condition,I took the hack method to solve this problem, neither downversion nor upversion of rn.
  Reffer to [this issue](https://github.com/facebook/react-native/pull/18456),and above this smart guy's [demo](https://snack.expo.io/Hkp55vn6G),
  according to following's guy, wrapper it to a component.

{% asset_img smart_guy.jpg method %}


#### 二、Fix method in my project

1、Create a new file to wrapper the hack text input to a component，first you should import some necessary libraries,like: react-native/react;

{% asset_img fix_method.jpg fix_method %}

2、In your TextInput component, import the Platform plugin,and add the following things:

{% asset_img fix_method_parent.jpg fix_method_parent %}

3、In your html,according to the _checkIsNeedHack,display related input,normal one or hack one.

{% asset_img html_like.jpg html_like %}

#### 三、The trick

Here use setTimeout to delay for the display of the props data from parent component.If not, the data from up component will not show in the text input value.