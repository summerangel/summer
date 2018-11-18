---
layout: '[layout]'
title: How to deploy a website on Mac
date: 2018-04-25 18:01:48
tags: deploy
---


#### 一、 Buy a CES（购买一台服务器）
 
  the link is: https://ecs-buy-cn-huhehaote.aliyun.com/wizard/#/prepay/cn-huhehaote
  
#### 二、Connect to Server（连接服务器）

  After you bought a CES, you will have access to login the server they give you,link this
  
  {% asset_img server_one.jpg the page you will find your public ip%}
  
  Open the terminal you usually use, and command following:（打开你常用的终端，输入以下信息）
  
      ssh root@39.104.121.24(the ip should change to your own public ip 这里的ip应该换成你自己的公网ip)
      
      after executing this,the terminal will let you input the password
      
      then you will connect to the server;
      
#### 三、Install Node（安装Node）

   1、The download link: https://nodejs.org/en/download/
   
   we usually choose the source code to install,for it's better.Click right press and copy the download link;
   （我们一般选择source code安装，因为听说更好一点。点击右键复制地址）
   
   
   2、Then we back to the connected server,and to the root directory,and create a empty directory to store all soft we need 
    
   to install.
   
   you can act like this: 1) cd / (this means to the root directory)
                          2) mkdir soft (create a directory named soft)
   
   
   3、exectute this in terminal: wget (here is the link you copied in step 1);
   
   4、decompression the file in step 3: tar -zxvf (here is compressed file name)
   
   5、execute this in terminal: cd (decompressed file name) && ./configure ;
   
   6、execute this in terminal: make && make install;
   
   7、execute this to see if you installed node successfully: node -v or npm -v;
   
   8、if you met a problem link:  g++: Command not found, you could execute this to fix: yum install gcc gcc-c++,then repeat
      step 7;
      
   
#### 四、Install nrm and pm2

   1、execute this in terminal: npm install -g cnpm --registry=https://registry.npm.taobao.org
   
   2、execute this in terminal: npm install -g nrm
   
   3、execute this in terminal: npm install -g pm2
      
   4、start a pm2 process: pm2 start index.js
      restart a pm2 process: pm2 restart id/name;
      delete a pm2 process: pm2 delete id/name;
      review a pm2 process: pm2 moint;
      review all pm2 processes: pm2 list;
      
#### 五、Install Nginx

   1、before install nginx, we should install some nginx dependencies;
   
   2、execute this in terminal: yum install -y pcre pcre-devel
   
   3、execute this in terminal: yum install -y zlib zlib-devel
   
   4、execute this in terminal: yum install -y openssl openssl-devel
   
   5、go to nginx official website to copy the download link: https://nginx.org/en/download.html
   
   6、execute this in terminal: wget (here is the link copied in step 5)
   
   7、execute this in terminal: tar -zxvf (here is the compressed file directory) && cd (here is the decompressed file directory)
   
   9、execute this in terminal: ./configure
   
   10、execute this in terminal: make && make install
   
   11、to see where the nginx is: whereis nginx
   
   12、to go to sbin directory: cd /usr/local/nginx/sbin
   
   13、start nginx: ./nginx
   
      start nginx: ./nginx
      stop nginx: ./nginx -s stop
      quit nginx: ./nginx -s quit
      reload nginx: ./nginx -s reload
      
      
#### 六、Install Git
    
   1、execute this in terminal: yum install git
   
   2、make sure is the git install done: git --version
   
#### 七、repo in git connect to server

   1、cd soft
   
   2、git clone (here is the git repo link)
   
   3、cd (the git repo name)
   
   4、npm i
   
   5、npm start(according to your repo)
   
   6、open the browser with the url: http://39.104.121.24:3000 (replace the ip with your own public ip)
   
   
   
#### 八、Mistake I make

   Because I didn't add port 3000 to the secure group,I can't open the link with port 3000 :http://39.104.121.24:3000。
   
   {% asset_img server_two.jpeg the page you add your port to secure group%}
   
   and may be this article will solve something: https://www.jianshu.com/p/9a0f356f89ca
   
   
   
#### 九、if you want to know more detail describe

  here is the origin website to introduce more: http://gitbook.cn/books/5a561cfca8b23d387720befc/index.html
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   