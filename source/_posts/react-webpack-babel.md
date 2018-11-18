---
layout: layout
title: Exploring Webpack4 and Babel7 In React16
date: 2018-09-17 21:32:33
tags: react、webpack、babel
---

### One、Create Project

  1、 Create project in your computer, name the project whatever you want: 
  `mkdir react-webpack-kit && cd react-webpack-kit`;

  2、Init a package.json file: `npm init -y`;

### Two、Dependencies that webpack need

   1、Since you are in the directory you just created, you can exectute the command directly:
    `yarn add -E -D webpack webpack-cli webpack-merge webpack-dev-server autoprefixer css-loader style-loader postcss-loader mini-css-extract-plugin optimize-css-assets-webpack-plugin uglifyjs-webpack-plugin html-webpack-plugin  clean-webpack-plugin file-loader url-loader`

   2、In `webpack4`, `webpack-cli` is required; `webpack-merge` is for different webpack config file merge, for there are two different or may be more environments, we can write different config files to adapt different environments; `webpack-dev-server` is a server set up by webpack, usually we use it in the development environment.

   3、`css-loader style-loader`：is for css file compile, if you use sass, you need to install `node-sass` and `sass-loader` to compile, similarly if you use less, you need `less-loader`; `autoprefixer postcss-loader` is for different browsers compatibility, and also we need to create a postcss config file, you can doing: `touch postcss.config.js`, and add the config in it，likes following:

    ```
    module.exports = {
        plugins: [
            require('autoprefixer')
        ]
    }
    ```

   4、`mini-css-extract-plugin optimize-css-assets-webpack-plugin uglifyjs-webpack-plugin`: although webpack will uglify the code in production environment,it doesn't uglify the css files, we need other plugin to do this.

   5、`html-webpack-plugin`: this plugin help us to copy the html file from our work directory to dist directory after packing, so we don't need to copy it manually; `clean-webpack-plugin` is a plugin that clean the dist directory before webpack begin to pack;

   6、`-E -D`: means install the plugin with fixed version and only install in devDependencies.


### Three、dependencies that babel need

   1、After installing the plugins that webpack need, now we begin to install the plugins babel needs:

    `yarn add -E -D babel-loader @babel/core @babel/plugin-transform-runtime @babel/plugin-proposal-decorators @babel/plugin-proposal-class-properties @babel/preset-env @babel/preset-react`

   2、`babel-loader @babel/core`：no need to explain;

   3、`@babel/plugin-transform-runtime`：is for development environment, and also we should install runtime in production: `yarn add -E @babel/runtime`;

   4、`@babel/plugin-proposal-decorators @babel/plugin-proposal-class-properties`：if we use es6+, then we need these.

   5、`@babel/preset-env @babel/preset-react`：mostly for react environment compile.

   6、Create babel config file: `touch babel.config.js`(here we should create this file instead of `.babelrc` file, for there will be a problem which troubled me a lot), the problem looks like:

  ```
   Support for the experimental syntax 'classProperties' isn't currently enabled (57:10)
       ......
   Add @babel/plugin-proposal-class-properties (https://git.io/vb4Ss) to the 'plugins' section of your Babel config to enable transformation.

   ```
### Four、Mock back-end data

   1、Here I use the packages `mockjs` and `json-server`, it's really awesome:
      `yarn add -E -D mockjs json-server`

### Five、Simple frame is ready

   Now the project dependencies is amost done, you would see the source code by clicking [this](https://github.com/summerangel/react-webpack-kit);
