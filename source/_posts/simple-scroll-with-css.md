---
layout: '[layout]'
title: Simple scroll realized by css
date: 2018-05-25 22:48:20
tags: css
---

#### Before start (why this article come out)

 At before time, I was tend to realize it by the library Swiper, which seems
 too big and bad performance to left-right scroll.Actually we can realize it
 by pure css in some degree,  I was told by my leader, so later I change it to
 pure css.

#### Your html

    ```
        <div class="parent-wrap">
            <div class="child-each-wrap">
            </div>
        </div
    ```

#### Your css

    ```
        .parent-wrap {
            overflow-x: scroll;
            white-space: nowrap;  // here it seems necessary,if not add it, the
            // scroll will take effect in the whole page,not the parent-wrap element
            padding-bottom: 20px; // here it fix the problem the scroll style
            // still show in IOS
        }
         .parent-wrap::-webkit-scrollbar {
            display: none // here is to clear the scroll style
         }
        .child-each-wrap {
             display: inline-block; // here is make sure the children are in the
             // same line
             margin-right: 40px;
             width: 360px; // here you can custom your own style
             height: 272px; // here you can custom your own style
        }
    ```

#### Over

   Though it looks simple enough, it took some time to implement it, just to
 record it for the sake next time to use it.