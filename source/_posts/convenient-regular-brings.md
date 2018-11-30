---
title: convenient that regular brings
date: 2018-11-30 10:22:19
tags: regular
---

## Introduction

Lately I was learning regular, as you know, I have recorded the note about regular in last blog, I'm crazy about regular in some extends,for every function I met in the project,the first solution I come out is using regular, and the time is coming.

## The exciting moment

Since we front end developers in my company is cooperating with the developer of Android and Ios, they provide us with the webview and we develop the pages of h5, which is so called hybrid. Ok, no more useless words,the function is we need to decrypt the data fetched from backend interface,some fields in the data is encrypted for the security's sake. Having known this, I suddenly think of regular, it can perfectly solve this problem, considering it for a moment, I consult with the backend developer, letting them create the fields expression special, so I can easily use regular.

## Show the code

```javascript
export const decrypt = {
  decryptData(encryptedData, privateKey = PRIVATE_KEY) {
    var decrypt = new JSEncrypt();
    decrypt.setPrivateKey(privateKey);

    var str = 'var ';
    for (var key in encryptedData) {
      str = str + key + '=' + decrypt.decrypt(encryptedData[key]) + ',';
    }
    return str.replace(/,$/, ';');
  },

  getDecryptedDataFromNative(secretData, callback) {
    if (isAndroid(USR_AGENT)) {
      getDecryptedDataFromAndroid(secretData, callback);
    } else if (isIOS(USR_AGENT)) {
      getDecryptedDataFromIOS(secretData, callback);
    }
  },

  packExpression(expressData) {
    var str = JSON.stringify(expressData);
    return str.replace(/"#/g, 'eval(').replace(/#"/g, ')');
  },

  /**
   * 使用的时候直接调用这个方法，会返回加密后的数据，但是赋值的时候需要 数值.toFixed(2),这里没有处理；
   * @param data
   * @returns {*}
   */
  executeExpression(data) {
    // 本地使用自己的解密方法
    if (window.location.hostname === 'localhost') {
      return new Promise((resolve, reject) => {
        const secretData = data.secretData || data.encryptMap;
        if (!!secretData) {
          let decryptData = this.decryptData(secretData, PRIVATE_KEY);
          // 解密后将加密数据去掉，防止干扰后面的表达式封装
          data['secretData'] = undefined;
          let expression = this.packExpression(data);
          var temp = {};
          // 执行
          eval(decryptData + 'temp = ' + expression + ';');
          resolve(temp);
        } else {
          resolve(data);
        }
      });
    } else {
      return new Promise((resolve, reject) => {
        if (!isEmpty(data.secretData)) {
          try {
            var str = JSON.stringify(data);
            let expression = str.replace(/"#/g, 'eval(').replace(/#"/g, ')');
            this.getDecryptedDataFromNative(data.secretData, function(response) {
              let decryptData = response; // 接收原生返回的解密后数据
              data['secretData'] = undefined;
              var temp = {};
              eval(decryptData + 'temp = ' + expression + ';');
              // 执行
              resolve(temp);
            });
          } catch (e) {
            reject(e);
          }
        } else {
          resolve(data);
        }
      });
    }
  },
};
```

## Thanks

At first, it is running smoothly in my local environment, but put it into the webview, a lot of problems come out, the tough one is, it is asynchronous to get the decrypted data from ios, I know it should be using Promise, but I don't know where to put it in, it's really sucks,furtunately, another colleague is good at it,helping me solved it.Here give my thanks to scopeWu and I really need to put some strength to understand promise deeply.

## In the end

Without complex loop and check, the regular makes it more convenient to achieve the goal.A little happy successfuly to made it. And there is a long way to go to be good at regular.