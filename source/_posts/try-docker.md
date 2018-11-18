---
layout: '[layout]'
title: Try docker in Mac
date: 2018-04-27 09:49:06
tags: docker
---

#### 一、Install docker

   Go to docker official website to download the docker app: https://docs.docker.com/docker-for-mac/install/#download-docker-for-mac
   
   We usually choose the stable one to install;
   
   
#### 二、Test your docker

   After you installed your docker, you can test it with the following command:
   
       docker --version
       docker --info
       docker run hello-world
       
#### 三、Public your git repo to docker

  1、Go to git to copy your git repo link;
  
  2、If you want to exclude some files: open your local git repo and create a .dockerignore file in the root directory and put the following info in it;
   
     .git
     node_modules
     npm-debug.log
  
  3、Create a Dockerfile file in root directory and also write the following in it:
  
      FROM node:8.4
      COPY . /app
      WORKDIR /app
      RUN npm install --registry=https://registry.npm.taobao.org
      EXPOSE 3000
  
  4、After above finished, you can create an image like following command:
  
      docker image build -t [here is your repo name] .
      
      Or
      
      docker image build -t [repo name]:0.0.1 .
      
  
  5、Container Generate:
  
      docker container run -p 8000:3000 -it [repo name] /bin/bash
      
      Or
      
      docker container run -p 8000:3000 -it [repo name]:0.0.1 /bin/bash
      
      
   you can start your project in docker(execute your project start command,eg: node app.js), and then open the link:http://127.0.0.1:8000 in browser,your project is running.
    
  6、Ctrl + c: stop node process; Ctrl + d(or input exit): quit the container; also: docker container kill will help;    
  
  7、Register a docker Id in https://hub.docker.com/;
    
  8、After registering open your terminal and execute: docker login (make sure your docker app is open and vpn is closed)
    
  9、After login
  
      docker image tag [imageName] [username]/[repository]:[tag]
      
      #eg: docker image tag summer-album:0.0.1 summaerangel/summer-album:0.0.1
      
  10、Finally, publish the image
  
      docker image push [username]/[repository]:[tag]
      
   then you can see your published image in hub.docker.com
  
#### 四、Commands that may used frequently

    docker version
    docker info
    docker image ls (list all the image)
    docker image rm [here is your imageName] (delete image file)
    docker image pull [here is imageName] (pull image file from docker)
    
    docker container run [imageName] (run the image in docker)
    docker container kill [containerId] (kill the running image file)
    docker container ls (list the running container)
    docker container ls --all (list all the container, including the killed ones)
    docker container rm [containerId] (delete the container in the docker)
    
  
  
  
#### 五、More detail description

   If this is not understandable, you can step into following links:
   
   http://www.ruanyifeng.com/blog/2018/02/docker-tutorial.html
   
   And
   
   https://docs.docker.com/docker-for-mac