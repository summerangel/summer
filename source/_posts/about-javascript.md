---
title: about-javascript
date: 2017-10-22 21:37:34
tags: javascript
---

#### 1、1) Use computed property names when creating objects with dynamic property names.

          eg: function getKey(k) {
                return `a key named ${k}`;
              }
              const obj = {
                id: 5,
                name: 'San Francisco',
                [getKey('enabled')]: true,
              };

         2) Use array spreads ... to copy arrays.

            eg: const len = items.length;
                const itemsCopy = [];
                const itemsCopy = [...items];

         3) To convert an array-like object to an array, use Array.from.

            eg: const foo = document.querySelectorAll('.foo');
                const nodes = Array.from(foo);

         4) Brilliant Array.prototype.reduce()

            eg: // friends - an array of objects
                // where object field "books" - list of favorite books
                var friends = [{
                  name: 'Anna',
                  books: ['Bible', 'Harry Potter'],
                  age: 21
                }, {
                  name: 'Bob',
                  books: ['War and peace', 'Romeo and Juliet'],
                  age: 26
                }, {
                  name: 'Alice',
                  books: ['The Lord of the Rings', 'The Shining'],
                  age: 18
                }];

                // allbooks - list which will contain all friends' books +
                // additional list contained in initialValue
                var allbooks = friends.reduce(function(prev, curr) {
                  return [...prev, ...curr.books];
                }, ['Alphabet']);

                // allbooks = [
                //   'Alphabet', 'Bible', 'Harry Potter', 'War and peace',
                //   'Romeo and Juliet', 'The Lord of the Rings',
                //   'The Shining'
                // ]

         5) Use object destructuring when accessing and using multiple properties of an object. jscs:

            eg: // good
                function getFullName(user) {
                  const { firstName, lastName } = user;
                  return `${firstName} ${lastName}`;
                }

                // best
                function getFullName({ firstName, lastName }) {
                  return `${firstName} ${lastName}`;
                }

         6) Never use arguments, opt to use rest syntax ... instead

            eg: // bad
                function concatenateAll() {
                  const args = Array.prototype.slice.call(arguments);
                  return args.join('');
                }

                // good
                function concatenateAll(...args) {
                  return args.join('');
                }

         7) Never mutate parameters

            eg: // bad
                function f1(obj) {
                  obj.key = 1;
                };

                // good
                function f2(obj) {
                  const key = Object.prototype.hasOwnProperty.call(obj, 'key') ? obj.key : 1;
                };

#### Check is weixin or is alipay:

      function IsWeixinOrAlipay(){
          var ua = window.navigator.userAgent.toLowerCase();
          //判断是不是微信
          if (ua.indexOf('micromessenger') >= 0) {
              return "WeiXIN";
          }
          //判断是不是支付宝
          if (ua.indexOf('alipayclient') >= 0) {
              return "Alipay";
          }
          //哪个都不是
          return "false";
      }

#### 初始化一个所有元素都相同的数组

    eg:Array(8).fill(1) //初始化一个数组，元素都为1
    
#### We call .slice() to copy the squares array instead of mutating the existing array

    eg: const squares = this.state.squares.slice();
            squares[i] = 'X';
            this.setState({squares: squares});
            
            
#### 转义字符：
          eg:  JSON.parse(cashier.replace(/&quot;/gi,'"'));
