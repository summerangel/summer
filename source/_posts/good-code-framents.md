---
title: good-code-framents
date: 2017-10-22 21:30:12
tags: javascript
---
{% asset_img sun.jpg A lot need to learn,I'm such stupid%}
#### 1、将一维数组转为二维数组：

     var arr=[1,2,3,4,5,6,7],ar=[];
                    while(arr.length)ar.push(arr.splice(0,3));

#### 2、手机号校验：

      if ((mobile.length === 0) || !/^0?(13|15|18|14|17)[0-9]{9}$/.test(phone)) {
          alert('请输入正确的手机号码');
          return false;
          }

#### 3、密码长度只能为8~20位:

      if (!/^[0-9a-zA-Z]{8,20}$/.test(password)) {
          alert('密码长度只能为8~20位');
          return false;
      }

#### 4、验证6位验证码：

      checkPayPassword(val) {
          return /^\d{6}$/.test(val)
          }

####  5、手机每四位空格隔开

      phoneNoSplit (phone) {
          let reg = /^(\d{4})(\d{4})(\d{3})$/;
          let matches = reg.exec(phone);
          return matches[1] + ' ' + matches[2] + ' ' + matches[3];
        }

#### 6、只输入数字带两位小数点

      const numberOnly = /^[1-9]+([.]{1}[0-9]{0,2}){0,1}$/;
      numberOnly.test(value);

#### 6、头像处理

    html:
        <input id="fileBtn" type="file" onchange="upload('#fileBtn', '#img');" accept="image/*" />
        # 解析
        # accept 属性（允许上传两种文件类型：gif 和 jpeg）
        # capture 捕获到系统默认的设备，有三个参数可设置  camera--照相机； camcorder--摄像机； microphone--录音
        # 参数一表示 "选择文件" 的 id，参数二表示 "显示图片" 的 id，

    js:
        var upload = function(c, d){
            "use strict";
            var $c = document.querySelector(c),
                $d = document.querySelector(d),
                file = $c.files[0],
                reader = new FileReader();
            reader.readAsDataURL(file);
            reader.onload = function(e){
                $d.setAttribute("src", e.target.result);
            };
        };
        # 解析
        # 参数在上面 HTML 就已经讲解了，
        # file 表示你选中的那个图片，然后它里面有几个属性 name、size、type、slice等，也都非常实用，

        # FileReader作为文件API的重要成员用于读取文件，根据W3C的定义，FileReader接口提供了读取文件的方法和包含读取结果的事件模型。
        # 调用 FileReader 的 readAsDataURL 接口，将启动异步加载文件内容，通过给 reader 监听一个 onload 事件，
        # 将数据加载完毕后，在onload事件处理中，通过 event 的 result 属性即可获得文件内容，然后扔进 img 的 src 即可 打开图片并预览。

        reference: https://www.idaima.com/article/12159

#### 7、将一个数组加入到另外一个数组中：

       Array.prototype.push.apply(updateNavListData[1].types,techList);

#### 8、删除对象中值为空或者null的属性：

       for (var p in params) {
               if (!params[p]) {
                 delete params[p];
               }
             }

#### 9、动态给a标签加电话号码：
              <a href={"tel:" + this.state.orderDetailData.storePhone}  className="contact-shop">联系门店</a>


#### 10、左右圆角：
        .br-left {
          border-top-left-radius: 20px;
          border-bottom-left-radius: 20px;
        }
        .br-right {
          border-top-right-radius: 20px;
          border-bottom-right-radius: 20px;
        }

#### 11、根据生日带出星座：

          // 根据生日的月份和日期，计算星座。
          function getAstro(month,day){
            var s="魔羯水瓶双鱼牡羊金牛双子巨蟹狮子处女天秤天蝎射手魔羯";
            var arr=[20,19,21,21,21,22,23,23,23,23,22,22];
            return s.substr(month*2-(day<arr[month-1]?2:0),2);
          }

          reference: http://m.jb51.net/article/98208.htm
          
          