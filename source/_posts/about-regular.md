---
title: 第1編の中国語ブログ - 正則について
date: 2018-11-18 14:48:50
tags: regular
---

## Introduction

This is an article about regular in chinese, for it is hard to understand, so it is better recorded in
mother language.This was learned from Mount Everest public class and this is to be continued. By the way,please forgive me to say that regular is really fabulous.


## 正则

#### 什么是正则？
 正则就是一个规则，用来处理 `字符串`的规则
> 1、正则匹配
> 编写一个规则，验证某个字符串是否符合这个规则，正则匹配使用的是 test 方法
>
> 2、正则捕获
> 编写一个规则，在一个字符串中把符合规则的内容都获取到，正则捕获使用的方法：正则的exec方法、字符串中的split、replace、match等方法都支持正则；

```javascript
var reg = /^$/; // => 两个斜杠中间包含一些内容就是正则，两个斜杠之间包含的全部内容都是元字符
```

### 正则的元字符和修饰符
>任何一个正则都是由 元字符 和 修饰符 组成的

`修饰符`

g(global); 全局匹配

i(ignoreCase); 忽略大小写

m(multiline); 多行匹配

`元字符`

[量词元字符]

+：让前面的元字符出现一到多次

？：出现零到一次

*：出现零到多次

{n}：出现n次

{n, }：出现n到多次

{n, m}：出现n到m次

[特殊意义的元字符]

\：转义字符（把一个普通字符转变为有特殊意义的字符，或者把一个有意义字符转换为普通的字符）

.：除了\n（换行符）以外的任意字符

\d：匹配一个0~9之间的数字

\D：匹配任意一个非0~9之间的数字（大写字母和小写字母的组合正好是反向的）

\w：匹配一个 `0~9或字母或_`之间的字符

\s：匹配一个任意空白字符

\b：匹配一个边界符

x|y：匹配x或者y中的一个

[a-z]：匹配a-z中的任意一个字符

[^a-z]：和上面相反，匹配任意一个非a-z中的字符

[xyz]：匹配x或者y或者z中的一个字符

[^xyz]：匹配除了xyz以外的任意字符

()：正则的小分组，匹配一个小分组（小分组可以理解为大正则中的一个小正则）

^：以某一个元字符开始

$：以某一个元字符结束

?:：只匹配不捕获

?=：正向预查

?!：负向预查

...

除了以上特殊元字符和量词元字符，其余的都叫做普通元字符；：代表本身意义的元字符

### 元字符详细解读
```javascript
var reg = /\d+/;
var str = '每天2018进步2019';
reg.test(str) => true

reg - /^\d+/;
reg.test(str) => false

reg = /^\d+$/; // => 只能是某某某的，这里说明只能是1到多个数字

reg.test('2018'); => true
reg.test('你90'); => false
reg.test('2'); => true ^或者$只是一个修饰或者声明，不会占据字符串的位置
```

`\`

```javascript
var reg = /^2.3$/;
reg.test('2.3'); => true
reg.test('2+3'); => true 点自爱正则中的意思：匹配除了\n以外的任意字符，而不是单纯的小数点

reg = /^2\.3$/;
reg.test('2.3'); => true
reg.test('2+3'); => false 使用转义字符把点转换为本身小数点的意思

var reg = /^\\d$/;
reg.test('\\d'); => true

var reg = /^\\\d$/;
reg.test('//9'); => true

var reg = /^\$/;
reg.test('\'); => 报错

```

`x|y`

```javascript
var reg = /^0|1$/;
reg.test('0'); => true
reg.test('1'); => true
reg.test('01'); => true

var reg = /^18|19$/;
reg.test('18'); => true
reg.test('19'); => true
reg.test('189'); => true
reg.test('119'); => true
reg.test('181'); => true
reg.test('819'); => true
reg.test('1819'); => true
reg.test('81'); => false
/**
 * 18或者19
 * 以1开头 以9结尾 中间是8或者1
 * 以18开头或者以19结尾即可
 **/

var reg = /^(18|19)$/; // => 此时只有18或者19符合我们的规则了
```

> ()：正则中的分组，也可以理解为一个大正则中的一个正则（包起来的部分是一个整体）：在正则中我们可以使用小括号`改变一些默认的优先级`;  
>小分组还有第二个作用：`分组引用`  
> 小分组的第三个作用：`分组捕获`

```javascript
var reg = /^[a-z]$/;
// => 分组引用：\1 或者 \2 ...出现和第N个分组一模一样的内容
var reg = /^([a-z])([a-z])\2([a-z])$/;
reg.test('food'); => true
reg.test('foad'); => false
reg.test('foot'); => true
reg.test('book'); => true
reg.test('weel'); => true
```

`[]`

>[xyz][^xyz][a-z][^a-z]
```javascript
// => \w：数字字母下划线中的任意一个字符
var reg = /^[a-zA-Z0-9_]$/; // => 等价于 \w

// => 中括号中出现的元字符，一般都代表本身的含义
var reg = /^[.?+&]+&/; // => 里面的四个元字符都是本身含义，例如：点就是小数点了，不是所谓的任意字符
reg.test('您好'); => false
reg.test('...'); => true
reg.test('?+'); => true

var reg = /^[a-z]$/;
reg.test('-'); => false
reg.test('a'); => true

// => 需求：描述样式类名的规则（数字、字母、下划线、-）,并且不能以-开头
var reg =  /^[\w-]+$/;
var reg =  /^[0-9a-zA-Z_--]+$/; // => 没有处理以-开头的情况
reg.test('-bb'); => true

var reg = /^\w[\w-]*$/;
```

```javascript
// => 需求：验证18~65之间的年龄
var reg = /^[18-65]$/; // => 1或者8~6或者5中的任意一个字符，中括号中出现的18不是数字18，而是1或者8，当前正则是非法的：因为不能设置8~6这种范围

// =>分三个阶段处理：
// 18 或者19 /(18|19)/
// 20 ~ 59 /([2-5]\d)/
// 60 ~ 65 /(6[0-5])/
var reg = /^(18|19)|([2-5]\d)|(6[0-5])$/;
```

```javascript
var reg = /^[\]$/; => 报错

```

### 常用的正则表达式编写

`验证是否为有效数字`
```javascript
/**
 * 可能是正数，可能是负数 12 -12
 * 整数或者小数 0 12 0.2 12.5 -12.3 
 * 只要出现小数点，后面至少要跟以为数字
 * 小数点前面必须有数字
 **/
var reg = /^-?\d+(\.\d+)?$/;
var reg = /^-?(\d|([1-9]\d+))(\.\d+)?$/;
/**
 * -? 负号可有可无
 * (\d|([1-9]\d+))
 * \d 一位数可以是任何值
 * ([1-9]\d+) 多位数不能以零开头
 * (\.\d+)? 小数部分可有可无，有的话点后面必须跟一位数字
```

`电话号码`

```javascript
/**
 * 11位数字
 * 1开头
 * 
 **/
var reg = /^1\d{10}$/;
```

`用户名：真实姓名`
```javascript
/**
 * 
 **/
//=> /^[\u4E00-\u9FA5]$/ 中文汉字的正则
var reg = /^[\u4E00-\u9FA5]{2, 5}(·[\u4E00-\u9FA5]{2, 5})?$/;

```

`邮箱`  
```javascript
var reg = /^\w+((-\w+)|(\.\w+))*@[A-Za-z0-9]+((\.|-)[A-Za-z0-9]+)*\.[A-Za-z0-9]+$/;
/**
 * \w+ =>以数字字母下划线开头
 * @前面可以是 数字、字母、下划线、-、. 这些符号
 * ((-\w+)|(\.\w+))* => 不能把 - 和 . 连续出现，出现一次后面必须跟数字字母下划线
 * @ 后面的部分支持
 *   企业邮箱
 *   .com.cn 多域名情况
 * 
 * [A-Za-z0-9]+ => @153.com.cn
 * ((\.|-)[A-Za-z0-9]+)*  => 
 * \.[A-Za-z0-9]+  => 
 **/

@163.com.cn
@test-test-test-test.com.cn

```

`身份证号码`
```javascript
/**
 * 18位
 * 前17位必须是数字
 * 最后一位可以是数字或者X(X代表数字10)
 * 
 * 362202199308018888
 * 前六位：省市县 362202
 * 接下来八位 出生年+月+日
 * 倒数第二位数字 奇数代表男 偶数代表女
 **/
var reg = /^(\d{6})(\d{4})(\d{2})(\d{2})\d{2}(\d)(\d|X)$/;
// => 这样写不仅可以匹配，而且以后再捕获的时候，不仅可以把大正则匹配的结果捕获到，里面每一个小分组（小正则）匹配的结果也可以单独的捕获到"分组捕获"

// => 年 1950~2017
// => 第一段 1950~1999
// => 第二段 2000~2017
// => 00~09
// => 10~17
// => /^((19[5-9]\d)|(20((0\d)|(1[0-7]))))$/
```

### 正则捕获
>把当前字符串中符合正则的字符捕获到  
>RegExp.prototype: `exec`实现正则捕获的方法

```javascript
var str = '';
var reg = /\d+/;

reg.exec(str);
/**
 * 当正则捕获的时候：
 * 1、先去验证当前字符串和正则是否匹配，如果不匹配返回的结果是null（没有捕获到任何的内容）
 * 2、如果匹配，从字符串最左边开始，向右查找到匹配的内容，并且把匹配的内容返回
 * 
 * exec捕获到结果的格式：
 * -> 获取的结果是一个数组
 * -> 数组中得第一项是当前本次大正则在字符串中匹配到的结果
 * -> index: 记录了当前本次捕获到结果的起始索引
 * -> input: 当前正则操作的原始字符串
 * -> 如果当前正则中有分组，获得的数组中，从第二项开始都是每个小分组，本次匹配到的结果（通过exec可以把分组中的内容捕获到）
 * 
 * 执行一次exec只能把符合正则规则条件中的一个内容捕获到，如果还有其他符合规则的，需要再次执行exec才有可能捕获到
 * 
 **、
```

`正则捕获存在懒惰行`
>执行一次exec捕获到第一个符合规则的内容，第二次执行exec，捕获到的依然是第一个匹配的内容，后面匹配的内容不管执行多少次exec都无法捕获到
>
>解决正则捕获的懒惰性；
>在正则的末尾加修饰符g（全局匹配）

```javascript
//=> 正则为什么会存在懒惰性？

/**
 * 正则本身有一个属性：lastIndex(下一次正则在字符串中匹配查找的开始索引)
 * 默认值：0，从字符串第一个字符开始查找匹配的内容
 * 默认不管指定多少遍exec方法，正则的lastIndex值都不会变（也就是第二次以后查找的时候还是从第一个字符找，所以找到的结果永远都是第一个匹配的内容）
 * 而且当我们手动把lastIndex 进行修改的时候，不会起到任何的作用
 * */


//=> 为什么加了g就解决了懒惰性？
/**
 * 加了修饰符g,每一次exec结束后，浏览器默认会把lastIndex值进行修改，下一次从上一次结束的位置开始查找，所以可以得到后面匹配的内容了
 **/

var reg = /\d+/;
var str = '一路2018扬帆起航2019';
console.log(reg.lastIndex); // => 0
console.log(reg.exec(str)[0]); // => '2018'

```

>exec有自己的局限性：执行一次exec只能捕获到一个和正则匹配的结果（即使加了修饰符g）,如果需要都捕获到，我们需要执行N次exec方法才可以
>
>下面封装的myExecAll方法，目的是执行一次这个方法，可以把当前正则匹配到的全部内容都捕获到

```javascript
RegExp.prototype.myExecAll = function myExecAll() {
    //=> this:当前需要处理的正则
    //=> str:当前需要处理的字符串
    var str = arguments[0] || '',
        result = [];

    //=> 首先判断this是否加了全局修饰符g,如果没有加，为了防止下面执行出现死循环，我们只让其执行一次exec即可，把执行一次的结果直接的返回
    if(!this.global) {
        return this.exec(str);
    }

    var ary = this.exec(str);
    while(ary) { /* ary !== null; 还可以捕获到内容，我们继续下一次捕获*/
        result.push(ary[0]); //=> 把当前本次捕获到的结果存放在result数组中
        ary = this.exec(str); //=> 继续执行下一次的捕获
    }
    return result;
}

var reg = /\d+/g; //不要忘记加g
reg.myExecAll('学习2018正则2019');
```

### 使用字符串方法match实现捕获

```javascript
var reg = /\d+/g;
var str = '学习2018正则2019';
str.match(reg);
```

>使用字符串的match捕获：   
>1、如果正则加了修饰符g,执行一次match会把所有正则匹配的内容捕获到；  
>2、如果没有加修饰符g,执行一次match只能把第一个匹配的结果捕获到；
>
>局限性：
>在加了修饰符g的情况下，执行match方法只能把大正则匹配的内容捕获到，对于小分组捕获的内容方法给其自动忽略了

```javascript
var str = 'my name is {0}, i am {1} years old~, 2018';
//=> 需求：把{n}整体捕获到，而且还要把括号中的数字也获取到
var reg = /\{(\d+)\}/g;

str.match(reg); //=> ["{0}", "{1}"]

//=> 想要获取小分组中的内容，我们只能使用exec处理了
function fn(reg, str) {
    var ary = reg.ecec(str),
    result = [];
    while(ary) {
        result.push(ary);
        ary = reg.ecec(str);
    }
    return result;
}
```

### 14、使用test也可以实现正则的捕获
> 不管是正则的匹配还是正则的捕获，在处理时候的原理是没区别的：`从字符串的第一个字符向后查找，找到符合正则规则的字符，如果可以找到，说明正则和字符串匹配（test检测返回true、exec捕获返回捕获的内容），如果找到末尾都没有匹配的，说明正则和字符串不匹配（test检测返回false、exec捕获返回null）`
>
>如果正则设置了修饰符g,不管使用test还是exec中的任何方法，都会修改lastIndex值（下一次查找是基于上一次匹配结果的末尾开始查找的）

```javascript
var reg = /\{(\d+)\}/g;
var str = 'my name is {0}~~';
if (reg.test(str)) {
    console.log(reg.lastIndex); //=>14
    //=> 如果当前字符串和正则是匹配的，我们进行捕获
    console.log(reg.exec(str)); //=> null
}
```
>使用test不仅可以找到匹配的内容，也能像exec一样，把找到的内容获取到
>test返回结果是true/false,所以靠返回结果肯定不行

```javascript
var reg = /\{(\d+)\}/g;
var str = 'my name is {0}~~';
var flag = reg.test(str); //=> true
console.log(RegExp.$1); //=> 获取到当前本次匹配内容中第一个小分组捕获的内容

reg.test(str); //=> true
console.log(RegExp.$1); // => 1 TEST可以实现捕获，但是每一次只能获取到当前本次匹配结果中，第N个分组捕获的内容 $1第一个分组 $2第二个分组

var result = [],
ary = reg.exec(str);
while(ary) {
    result.push(ary[1]);
    ary = reg.exec(str);
}
console.log(result);//=> ["0", "1"]

```

### 15、所有支持正则的方法都可以实现正则的捕获（一般都是字符串方法），
>字符串中常用的支持正则的方法：   
>match   
>split      
>replace
>...

```javascript
var str = '?name=123&age=8&lx=test';
str.split(/&|=/); //=> ["name", "123", "age", "8", "lx", "test"]

str.split(/(&|=)/)); //=> ["name", "=", "123", "&", "age", "=", "8", "&", "lx", "=", "test"]

//=> 在使用split进行字符串拆分的时候，如果正则中包含小分组，会把小分组中的内容都捕获到，放在最后的数组中

//=>本案例中的小括号仅仅是为了实现改变      级 问题，但是不想把分组中的内容捕获到 => "只想匹配不想捕获" 我们可以使用(?:)

str.split(/(?:&|=)/); // => ["name", "123", "age", "8", "lx", "test"]

//=>只匹配不捕获：
//在当前一个分组中加了 ?: ，在正则检测匹配的时候，小分组可以起到自己应有的作用（例如：改变优先级...）,但是在捕获的时候，遇到了带?:的小分组，浏览器不会把当前这个分组中匹配的内容，单独去捕获了

var reg = /^(\d{6})(\d{4})(\d{2})(\d{2})(?:\d{2})(\d)(?:\d|X)$/;

var reg = /^-?(?:\d|(?:[1-9]\d+))(?:\.\d+)?$/; //=>计算式第几个分组的时候，我们从左向右找（ 即可；
```

**` replace `**
>replace:字符串中原有字符的替换   
>str.replace(old, new)

```javascript
var str = 'test123you123'
str.replace('test', 'example');
```

>replace原理：   
>1、当replace方法执行，第一项传递一个正则
>正则不加g: 把当前字符串中第一个和正则匹配的结果捕获到，替换成新的字符
>正则加g: 把当前字符串中所有和正则匹配的内容都分别的捕获到,而且每一次捕获，都会把当前捕获的内容替换为新字符


## Words in the end

Here recommands a very good article to make you better understand regular:
 
 [Click me](https://juejin.im/post/5965943ff265da6c30653879)
 
 [Download link](https://github.com/qdlaoyao/js-regex-mini-book)