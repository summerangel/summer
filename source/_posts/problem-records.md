---
layout: '[layout]'
title: Problems records
date: 2018-05-15 14:48:43
tags: bugs
---


#### error in console: gyp: Call to './util/has_lib.sh freetype' returned exit status 0 while in binding.gyp. while trying to load binding.gyp

solve method: 

    npm install -g node-gyp
    brew install pkg-config cairo libpng jpeg giflib

#### error in console: BOZZMOB-M-T0HZ:rest bozzmob$ node helloz.js 
/Users/bozzmob/Documents/work/nextgennms/rest/helloz.js:1
(function (exports, require, module, __filename, __dirname) { (async function testingAsyncAwait() {
                                                                     ^^^^^^^^
SyntaxError: Unexpected token function
    at Object.exports.runInThisContext (vm.js:53:16)
    at Module._compile (module.js:513:28)
    at Object.Module._extensions..js (module.js:550:10)
    at Module.load (module.js:458:32)
    at tryModuleLoad (module.js:417:12)
    at Function.Module._load (module.js:409:3)
    at Function.Module.runMain (module.js:575:10)
    at startup (node.js:160:18)
    at node.js:456:3


 Solve method:  check your node version   node -v (here used es7's property async)

 #### 安装redis修改权限：
    Attempted to create a lock file on a read-only directory: /data/db, terminating

   sudo chown -R $USER /data/db
    