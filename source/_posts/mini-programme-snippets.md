---
title: Some simple snippets about mini-programme
date: 2018-05-07 22:54:50
tags: mini-programme
---

#### 一、Remove the scroll bar in scroll-view

     ```
     ::-webkit-scrollbar {
          width: 0;
          height: 0;
          color: transparent;
     }

     ```

#### 二、Enable scroll in scroll-view

  the following css are needed to let the scroll-view to scroll:

   ```
   width: 100%;
   white-space: nowrap;

   ```

#### 三、Change the background-color of the whole page

   Add following to your css file:

   ```
   Page {
     display: block;
     min-height: 100%;
     background-color: (here is the color you want);
   }

   ```


#### 四、Using the unit of rpx to adjust different phone size

  The formula of transfer like following, use iphone6 as example:

  ```
    1px = 2rpx;
    1rem = 750/20;

  ```

   if you want to know more about this, you can step into [this article](http://www.cnblogs.com/fayin/p/6346754.html)


#### 五、May be a bug

   Don't add auto-focus to the element input,it will cause the death of your project(the situation I confronted was:
   I can't go back nor scroll the page)

#### 六、Something I always forget

   Dynamically give a class to an element:

   ```
   class="shopcart {{ cartShow ? 'show' : '' }}"

   ```
   Add key to a recycle:

   ```
   wx:key="unique"

   ```

   All above are which I met after completing an static mini-project.