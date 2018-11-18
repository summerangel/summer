---
title: about-css
date: 2017-10-22 21:38:09
tags: technique
---

#### 单行显示省略号：
      overflow: hidden;
      text-overflow: ellipsis;
      white-space: nowrap;
     多行显示省略号：
      display: -webkit-box;
      -webkit-line-clamp: 2; （多少行的时候显示）
      -webkit-box-orient: vertical;
      overflow: hidden;

     三角箭头：
     .left_arrow {
           position: relative;
           .arrow_left {
             margin: 5px auto;
             width: 0;
             height: 0;
             position: absolute;
             left: -11px;
             top: -7px;
             .triangle_top {
               border-left: 12px solid transparent;
               border-right: 0px solid transparent;
               border-bottom: 27px solid #FAD961;
             }
             .triangle_bottom {
               border-left: 12px solid transparent;
               border-right: 0 solid transparent;
               border-top: 27px solid #FAD961;
             }
           }
           .count_down {
             padding: 6px 14px 7px 15px;
             height: 51px;
             background: linear-gradient(90deg, #FAD961 0%, #FF8E4E 100%);
           }
         }

#### 在移动端样式中，尽量不要写position: fixed;（eg:弹框：可以换成position: absolute;然后在底下那层加上position: relative;）

#### 垂直居中 (https://segmentfault.com/a/1190000000468431)

    .center-vertical {
      position: relative;
      top: 50%;
      transform: transformY(-50%);
    }
    
    或
    
    .center-vertical {
       position: relative;
       left: 50%;
       transform: transformX(-50%);
    }
    
#### 多重边框

    div {
        box-shadow: 0 0 0 6px rgba(0, 0, 0, 0.2), 0 0 0 12px rgba(0, 0, 0, 0.2), 0 0 0 18px rgba(0, 0, 0, 0.2), 0 0 0 24px rgba(0, 0, 0, 0.2);
        height: 200px;
        margin: 50px auto;
        width: 400px
    }
    
#### 浮点数转成整型：|0和~~或+

    eg: var foo = (12.4 / 4.13) | 0;//结果为3
        var bar = ~~(12.4 / 4.13);//结果为3
        
#### 关于console
 
    var _log = console.log;
    console.log = function() {
      _log.call(console, '%c' + [].slice.call(arguments).join(' '), 'color:transparent;text-shadow:0 0 2px rgba(0,0,0,.5);');
    };
    
#### 半圆角：

    .left_circle {
            left: -2px;
            border: 1px solid #D6D6D6;
            border-radius: 0 100% 100% 0/50%;
            border-left: none;
          }
          .right_circle {
            border: 1px solid #D6D6D6;
            border-radius: 100% 0 0 100%/50%;
            border-right: none;
            right: -2px;
          }