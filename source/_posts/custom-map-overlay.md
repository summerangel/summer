---
layout: '[layout]'
title: An example to custom baidu map's overlay
date: 2018-05-22 23:25:48
tags: baidu-map
---


#### 一、Your html looks like:

 ```
    <div class="panel">
       <div id="map" class="map">显示地图</div>
    </div>
 ```

#### 二、The core code to realize custom style:

 ```
         const longitude = 121.532419
         const latitude = 31.242774
         const mp = new BMap.Map('map')
         const point = new BMap.Point(longitude, latitude)
         mp.centerAndZoom(point, 15)
         // 红色圆点
         function CustomRedCircle(point) {
           this._point = point
         }
         // 复杂的自定义覆盖物
         function ComplexCustomOverlay(point, text) {
           this._point = point;
           this._text = text;
         }
         CustomRedCircle.prototype = new BMap.Overlay();
         ComplexCustomOverlay.prototype = new BMap.Overlay();
         ComplexCustomOverlay.prototype.initialize = function(map) {
           this._map = map;
           var div = this._div = document.createElement('div');
           div.style.position = 'absolute';
           div.style.zIndex = BMap.Overlay.getZIndex(this._point.lat) + 1;
           div.style.backgroundColor = '#FFFFFF';
           div.style.color = '#333333';
           div.style.padding = '10px 7px 10px 10px';
           div.style.whiteSpace = 'nowrap'
           div.style.MozUserSelect = 'none'
           div.style.fontSize = '14px'
           var span = this._span = document.createElement('span');
           div.appendChild(span);
           span.appendChild(document.createTextNode(this._text));
           var that = this;

           var arrow = this._arrow = document.createElement('div');
           arrow.style.position = 'absolute';
           arrow.style.top = '35px';
           arrow.style.left = '30px';
           arrow.style.overflow = 'hidden';
           arrow.style.borderTop = '13px solid #fff';
           arrow.style.borderLeft = '10px solid transparent';
           arrow.style.borderRight = '10px solid transparent';
           div.appendChild(arrow);

           mp.getPanes().labelPane.appendChild(div);

           return div;
         }
         CustomRedCircle.prototype.initialize = function (map) {
           this._map = map;
           let div = this._div = document.createElement('div');
           div.style.position = 'absolute';
           div.style.zIndex = BMap.Overlay.getZIndex(this._point.lat);
           div.style.backgroundColor = '#C81528';
           div.style.width = '17px';
           div.style.height = '17px';
           div.style.borderRadius = '17px';
           mp.getPanes().labelPane.appendChild(div);
           return div;
         }
         CustomRedCircle.prototype.draw = function () {
           const map = this._map;
           const pixel = map.pointToOverlayPixel(this._point);
           this._div.style.left = pixel.x - 8 + 'px';
           this._div.style.top = pixel.y - 8 + 'px';
         }
         ComplexCustomOverlay.prototype.draw = function() {
           const map = this._map;
           const pixel = map.pointToOverlayPixel(this._point);
           this._div.style.left = pixel.x - parseInt(this._arrow.style.left) - 10 + 'px';
           this._div.style.top = pixel.y - 50 + 'px';
         }

         const myOverlay = new ComplexCustomOverlay(point, '静安区 大宁广场')
         const marker = new CustomRedCircle(point)
         mp.addOverlay(myOverlay)
         mp.addOverlay(marker)
         mp.disableDragging()
         mp.disableDoubleClickZoom()
         mp.disablePinchToZoom()

 ```

#### 三、At the end of the core code is to disable the operation to the map,make the map just the meaning of show

  It tooks time to find all the attributes,if you are the first time to use it, you can refer to the document of
  [baidu's map api](http://lbsyun.baidu.com/cms/jsapi/reference/jsapi_reference.html),it's useful.

  If you are familar with it, forget it.

#### 四、Another way to disable map operation

     You can make a highest priority mask such as an transparent png image to cover it, this is the method I used in wechat mini program.