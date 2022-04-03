# String的常用方法

>所有用单引号和双引号、反引号(`)括起来的都是字符串

```js
// 每个字符串都是由零个到多个字符串组成
string.length //=>字符串长度
str[0] //=>获取索引为零(第一个)字符
str[str.length - 1] //获取最后一个索引
str[10000] //=>undefined 不在这个索引

//字符串遍历
for (let i = 0; i < str.length; i++) {
    let char = str[i];
    console.log(char);
}
```

#### charAt/charCodeAt

```js
// charAt: 根据索引获取指定位置的字符
// charCodeAt: 获取指定字符的ASII码值(Unicode编码值)
// @params
// n[Number] 获取字符串指定索引
// @return
// 返回查找到的字符
// 找不到返回的是空字符串不是undefined， 或者对应的编码值

let str = 'zhenaiwujiadaobachuiyangliu';
console.log(str.charAt(3)); // n
console.log(str.charCodeAt(3)); // 110

console.log(str.charAt(0)); // z
console.log(str[0]); // z
console.log(str.charAt(10000)); // ''
console.log(str[100000]); //undefinde
console.log(str.charCodeAt(0)); //122
console.log(String.fromCharCode(12)); //''
```

#### substr/substring/slice

```js
// 都是为了实现字符串的截取(在原来字符串中查找到自己想要的)
// substr(n, m): 从索引n开始截取m个字符， m不写截取到末尾(后面方法也是)
// substring(n, m)： 从索引n开始找到索引为m处(不含m)
// slice(n,m):和substring一样，都是找到索引为m处，但是slice可以支持负数作为索引，其余两个方法是不可以

let str = 'zhenaiwujiadaobachuiyangliu';
console.log(str.substr(3, 7)); //=> naiw
console.log(str.substring(3, 7)); //=> naiw

console.log(str.substr(3)); //=> naiwujiadaobachuiyangliu
console.log(str.substring(3, 100000)); //=> naiwujiadaobachuiyangliu

//截取到末尾(超过索引的也只截取到末尾)
console.log(str.substring(3, 7)); //=>naiw
console.log(str.slice(3, 7)); //=> naiw
console.log(str.substring(-7, -3)); //=> 
console.log(str.slice(-7, -3)); //=> yang
// 找：负数索引，我们可以按照STR.length+负数索引的方式找=>slice(26-7,26-3)=>slice(19,23)
```

#### indexOf/lastindexOf/includes 

```js
//验证字符是否存在
// indexOf(x,y):获取x第一次出现位置的索引，y是控制查找的起始位置索引
// lastIndexOf(x):最后一次出现位置的索引
// =>没有这个字符，返回值的结果是-1

let str = 'zhenaiwujiadaobachuiyangliu';
console.log(str.indexOf('n')); //=>3
console.log(str.lastIndexOf('n')); //=>22
console.log(str.indexOf('@')); //=>-1

console.log(str.indexOf('dao')); //=>11 验证整体第一次出现的位置，返回的索引是第一个字符串所在位置的索引值
console.log(str.indexOf('dap')); //=>-1 验证整体第一次出现的位置，有任何不匹配都找不到，返回-1
console.log(str.indexOf('n', 20)); //=>22 查找字符串索引20及之后的字符串中，n第一次出现的位置
//如何判断一个字符串是否包含某个字符？
if (str.indexOf('@') === -1) {
    //不存在
}
//数组中的includes不接荣IE6-8,而字符串中的includes是兼容的
if (!str.includes('@') === -1) {
    //不存在
}
```

#### toUpperCase/toLowerCase

```js
let str = 'zhenaiwujiadaobachuiyangliu';
// str = str.toUpperCase();
// console.log(str); //=> ZHENAIWUJIADAOBACHUIYANGLIU

// str = str.toLowerCase();
// console.log(str); //=> zhenaiwujiadaobachuiyangliu

//实现字符串首字母大写
str = str[0].toUpperCase() + str.substring(1, str.length);
console.log(str);
```

#### split

```js
// split([分隔符])： 把字符串按照指定的分隔符拆分成数组(和数组中的join对应)
// split支持传递正则表达式
// @params
// 分隔符或者正则表达式
// @return
// 用分隔符分割开的字符串组成的数组
//需求：把|分隔符变成,分隔符
let str = 'music|movie|eat|sport';
let ary = str.split('|'); //=>['music', 'movie', 'eat', 'sport']
ary = ary.join(','); //=>music,movie,eat,sport
console.log(ary);
```

#### replace

```js
// replace(老字符,新字符):实现字符串的替换(经常伴随着正则的使用)
//返回替换后的新字符串
// let str = 'zhenaiwujiadaobachuiyangliu';
// let res = str.replace('z', 'a');
// console.log(res, str); //=>ahenaiwujiadaobachuiyangliu zhenaiwujiadaobachuiyangliu

// let str = '真爱@无价@刀疤@垂杨柳';
// str = str.replace('@', '-'); //=>在不使用正则表达式的情况下，执行一次replace只能替换一次字符
// console.log(str); //=> 真爱-无价@刀疤@垂杨柳

// str = str.replace(/@/g, '-');
// console.log(str); //=>0 真爱-无价-刀疤-垂杨柳
```

`match`

`localCompare`

`trim / trimLeft / trimRight`

 ...

 控制台输出String.protoytpe查看所有字符串提供的方法

### 实现一些常用的需求

>时间字符串的处理

```js
// let time = '2022-3-22 12:6:23';
// "2022年3月22日 12时6分23秒"
// 方案一
// time = time.replace('-', '年').replace('-', '月').replace(' ', '日 ').replace(':', '时').replace(':', '分') + '秒';
// console.log(time); //=>2022年3月20日 12时6分23秒

// 方案二
// time = time.split(' ');
// let dat = time[0].split('-');
// time = time[1].split(':');
// let year = dat[0];
// let month = dat[1];
// let day = dat[2];
// let hour = time[0];
// let min = time[1];
// let second = time[2];
// console.log(year + '年' + month + '月' + day + '日 ' + hour + '时' + min + '分' + second + '秒'); //=>2022年3月20日 12时6分23秒

// let ary = time.split(/(?: |-|:)/g);
// console.log(buling(ary[0]) + '年' + buling(ary[1]) + '月' + buling(ary[2]) + '日 ' + buling(ary[3]) + '时' + buling(ary[4]) + '分' + buling(ary[5]) + '秒'); //=>2022年3月20日 12时6分23秒

// function buling(value) {
//     if (value < 10) {
//         value = "0" + value;
//     }
//     return value;
// }
```

##### 实现一个方法queryURLParmeter获取一个URL地址问号后面传递的参数信息

```js
// 实现一个方法queryURLParameter:获取URL地址中问好传参的信息和哈希值
let url = 'https://www.baidu.com/?lx=1&name=aaa&teacher=bbb#box';

//结果{
//     lx:1,
//     name:'aaa',
//     teacher:'bbb',
//     HASH:'box'
// }

//1.获取问好后面的值
// let askIndex = url.indexOf('?');
// let wellIndex = url.indexOf('#');
// let askText = url.substring(askIndex + 1, wellIndex);
// let wellText = url.substring(wellIndex + 1);
// let askAry = askText.split('&');
// let askObj = {};
// askAry.forEach(function(item) {
//     let ary = item.split('=');
//     askObj[ary[0]] = ary[1];
// });
// askObj.HASH = wellText;
// console.log(askObj, wellText);


// queryURLParams:获取URL地址中问号传参的信息和哈希值
// @params
// url[string] 要解析的URL字符串
// @return
// [object] 包含参数和哈希值信息的对象
// let url = 'https://www.baidu.com/s?wd=%E4%B9%A0%E8%BF%91%E5%B9%B3%E5%AF%B9%E4%B8%9C%E8%88%AA%E5%AE%A2%E6%9C%BA%E5%9D%A0%E6%AF%81%E4%BD%9C%E5%87%BA%E9%87%8D%E8%A6%81%E6%8C%87%E7%A4%BA&sa=fyb_n_homepage&rsv_dl=fyb_n_homepage&from=super&cl=3&tn=baidutop10&fr=top1000&rsv_idx=2&hisfilter=1';

function queryURLParams(url) {
    //1.获取问号后面的值
    if (!url.includes('?')) {
        return {};
    }
    let askIndex = url.indexOf('?');
    let wellIndex = url.indexOf('#');
    let askText = url.substring(askIndex + 1, wellIndex === -1 ? url.length : wellIndex);
    let wellText = url.substring(wellIndex + 1);
    //2.获取到的值详细处理
    let askAry = askText.split('&');
    let askObj = {};
    if (askAry.toString()) {
        askAry.forEach(function(item) {
            let items = item.split('=');
            askObj[items[0]] = items[1];
        });
    }
    //哈希
    if (wellIndex !== -1) {
        askObj['HASH'] = wellText;
    }
    return askObj;
}
console.log(queryURLParams(url));
```

```js
function queryURLParams(url) {
    let result = {},
        reg1 = /([^?=&#]+)=([^?=&#]+)/g,
        reg2 = /#([^?=&#]+)/g;
    url.replace(reg1, (n, x, y) => result[x] = y);
    url.replace(reg2, (n, x) => result['HASH'] = x);
    return result;

}
console.log(queryURLParams(url));
```

##### 验证码

```js
var random = document.querySelector('.random');
        var next = document.querySelector('a');
        var shuru = document.querySelector('.shuru');
        var submit = document.querySelector('.submit');

        function getRandom(min, max) {
            return Math.floor(Math.random() * (max - min + 1)) + min;
        }
        var arr = ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p', 'q', 'r', 's', 't', 'u', 'v', 'w', 'x', 'y', 'z'];
        // console.log(getRandom(1, 9) + arr[getRandom(0, arr.length - 1)] + getRandom(1, 9) + arr[getRandom(0, arr.length - 1)]);
        random.innerHTML = getRandom(1, 9) + arr[getRandom(0, arr.length - 1)] + getRandom(1, 9) + arr[getRandom(0, arr.length - 1)];
        next.onclick = function() {
            random.innerHTML = codeStr1 = getRandom(1, 9) + arr[getRandom(0, arr.length - 1)] + getRandom(1, 9) + arr[getRandom(0, arr.length - 1)];
        };
        submit.onclick = function() {
            if (shuru.value.toUpperCase() === codeStr1.toUpperCase()) {
                alert('验证成功！');
            } else {
                alert('验证失败！');
            }
        }
        let ary = [];
        for (let j = 48; j <= 57; j++) {
            ary.push(String.fromCharCode(j));
        }
        for (let j = 65; j <= 90; j++) {
            ary.push(String.fromCharCode(j));
        }
        for (let j = 97; j <= 122; j++) {
            ary.push(String.fromCharCode(j));
        }
        console.log(ary);
```



