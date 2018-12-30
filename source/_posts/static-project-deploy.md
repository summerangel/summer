---
title: static-project-deploy
date: 2018-12-12 21:33:34
tags: nginx、linux、server
---

## Introduction

It's easily to forget,so record the steps when deploy a static project which with no server side language node,more easily deployed than node.

## Get your ip provided by server cloud provider

#### how to get ip
I wrote one blog about how to buy and install related environments before,the name is '[How to deploy a website on Mac](https://summerangel.github.io/2018/04/25/about-deploy/)'.

## Steps

### 1、Login your server first
open your terminal(terminal one):
> Use command line(just replace the ip with your own):
`ssh -q -l root -p 22 94.191.27.xxx`
> then it will tip you to input your password

### 2、Copy your local builded project into your server machine
> the file should be with .txt or .zip,otherwise it will cause error.
open another terminal(terminal two),you can open it with the shortcut key `command n`,and the copy command line is:
`scp -p 22 /User/summer/leisure/project/build.zip root@94.191.27.xxx:/root/html/`
you can get the dir of your local project by the command `pwd`

### 3、Back to terminal one, and go to the dir which receive the copied zip with the command
`cd /root/html/`

### 4、unzip

Now we are in the dir of html,unzip the build.zip file with the command line:
`unzip -o -d /root/html/ build.zip`
> this means that unzip build.zip into dir /root/html
> -o means cover the file with no hint
> -d means unzip the file into the dir /root/html


## End

I'm not familiar with nginx, so in the process of deploying, I was referring to the blog of [This one](https://segmentfault.com/a/1190000015685430), and also met the problems mentioned in the article, just do as the author say.
So happy to make project display without running in local environment. 
#### provide the nginx.conf file
```javascript
user root;
worker_processes  1;

events {
    worker_connections  1024;
}

http {
    include       mime.types;
    default_type  application/octet-stream;

    sendfile        on;

    keepalive_timeout  65;

    server {
        listen       80;
        server_name  localhost;

        location / {
            root   html;
            index  index.html index.htm;
        }

        location /card {
            alias /root/html/build;
            index index.html index.htm;
            try_files $uri $uri/ /card/index.html;
        }
        error_page   500 502 503 504  /50x.html;
    }

}
```





