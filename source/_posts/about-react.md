---
title: about-react
date: 2017-10-22 21:36:07
tags: react
---

## record something happened in react project

#### about div editable

  使用contentEditable属性让div可编辑时，去掉react警告：

  "
  contentEditable="true" suppressContentEditableWarning="true"
  "

####  input焦点自动定位：autoFocus

      reference: https://github.com/erikras/redux-form/issues/1382

####  生成二维码插件

      https://github.com/soldair/node-qrcode

#### care about

      1、元素要有闭合标签，避免提示错误
      2、在react中使用this.变量名（当该变量变动时，不会触发render），
      如要render也更新，需将变量放在this.state里面


#### 使用classnames, 动态加样式，eg: className('card-box', otherStyle, {'show': (this.props.isShow)})

#### Data change without mutation

      eg: var player = {score: 1, name: 'Jeff'};
          
          var newPlayer = Object.assign({}, player, {score: 2});
          // Now player is unchanged, but newPlayer is {score: 2, name: 'Jeff'}
          
          // Or if you are using object spread syntax proposal, you can write:
          // var newPlayer = {...player, score: 2};