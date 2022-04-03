# 				Math

### 一、Math

>数学函数：但是它不是一个函数，它是一个对象，对象中存储了很多操作数字的属性方法，因此被称为数学函数。

```javascript
console.log(typeof Math);
console.log(Math);
Math ={
    PI:3.141592653589793,
    abs:function(){[native code]},
    ceill:function(){[native code]}
    ...
}
Math.PI
Math.abs()
```

#### 二、Math中常用的属性方法

##### 1.`Math.abs("x")函数返回指定数字"x"的绝对值。`

```javascript
//Math.abs("x")函数返回指定数字"x"的绝对值。
//如果时数字类型就直接转成绝对值，如果是其他类型使用Number先转成数字，不能转成数字的会返回NaN
console.log(Math.abs(12.5)) //12.5
console.log(Math.abs(-12.5)) //12.5
console.log(Math.abs(0)) //0
console.log(Math.abs('1')) //1
console.log(Math.abs('12px')) //NaN
console.log(Math.abs(true)) //1
```

##### 2.`Math.ceill("x"):向上取整`

```javascript
//只要有小数就往整数位 + 1， 负数直接去除小数位
console.log(Math.ceil(12.1)) //=>13
console.log(Math.ceil(12.5)) //=>13
console.log(Math.ceil(12.9)) //=>13
console.log(Math.ceil(-12.1)) //=>-12
console.log(Math.ceil(-12.5)) //=>-12
console.log(Math.ceil(-12.9)) //=>-12
console.log(Math.ceil('12px')) //=>NaN
```



##### 3.`Math.floor("x"):向下取证`

````javascript
// 只要有小数就往整数位+1，正数直接去除小数位
console.log(Math.floor(12.1)) //=>12
console.log(Math.floor(12.5)) //=>12
console.log(Math.floor(12.9)) //=>12
console.log(Math.floor(-12.1)) //=>-13
console.log(Math.floor(-12.5)) //=>-13
console.log(Math.floor(-12.9)) //=>-13
console.log(Math.floor('12px')) //=>NaN
````

##### 4.`Math.round():四舍五入`

```javascript
console.log(Math.round(12.1)) //=>12
console.log(Math.round(12.5)) //=>13  正数中的.5属子
console.log(Math.round(12.9)) //=>13
console.log(Math.round(-12.4)) //=>-12
console.log(Math.round(-12.5)) //=>-12 负数中的.5属于舍
console.log(Math.round(-12.9)) //=>-13
console.log(Math.round('12px')) //=>NaN
```

##### 5.`Math.max/min([value11],[value2]...)：求一组数据的最大/最小值`

```javascript
console.log(Math.max(1, 2, 3, 4, 5, 6)); //6
console.log(Math.min(1, 2, 3, 4, 5, 6)); //1
```

##### 6.`Math:sqrt/pow`

```javascript
console.log(Math.sqrt(9)); //=>3 符号N*N=M 这样的M才能整开平方
console.log(Math.sqrt(-9)); //=>NaN 负数开不了平方

// console.log(Math.pow(底数,指数));
console.log(Math.pow(2, 10)); //=>1024
```

##### 7.`Math.random():获取0-1之间的随机小数`

```js
for (var i = 1; i < 10; i++) {
    console.log(Math.random());
    // 0.36276918928795654
    // 0.47621690474847145
    // 0.25526814369091677
    // 0.11131240651409557
    // 0.6490867114864463
    // 0.6364011879761515
    // 0.5913581343530059
    // 0.827054488563151
    // 0.4886527330428603
}
```

##### `扩展：获取n-m之间的整数`

```js
var n = 5;
var m = 15;
for (var i = 0; i < 10; i++) {
    console.log(Math.floor(Math.random() * (m - n + 1) + n));
}
var number = Math.floor(Math.random() * (m - n + 1) + n);
console.log(number);
```




# Array

### 一、数组

>数组是对象数据类型的，他属于特殊的对象

```js
let ary = [12, 23, 43, 34];
console.log(typeof ary); //=>object
console.log(ary);
/*
ary = {
        0: 12,
        1: 23,
        2: 43,
        3: 34,
        length: 4
    }
    数字作为索引(key 属性名)
    length长度
    ary[0] 根据索引获取指定项的内容
    ary.length 获取数组的长的
    ary.length -1 最后一项的索引
*/
```



#### 二、数组的常用方法

```js
//数组的构造函数Array，我们创建的所有数组都是通过这个构造函数创建出来的对象而构造函数的共有几个方法放到原型对象身上，所以如果你要看数组的方法，需要找到构造函数的原型对象上查看
console.dir(Array.prototype);//=>
/*
at: ƒ at()
concat: ƒ concat()
constructor: ƒ Array()
copyWithin: ƒ copyWithin()
entries: ƒ entries()
every: ƒ every()
fill: ƒ fill()
filter: ƒ filter()
...
*/
```



- 方法的作用和含义
- 方法的实参(类型和含义)
- 方法的返回值
- 原来的数组是否会发生改变

#### 1.实现数组增删改的方法

>这一部分的方法都会修改原有的数组

##### `push`

```js
// push: 向数组末尾增加内容
// @params
// 多个任意类型
// @return
// 新增后数组的长度

let ary = [10, 20];
let res = ary.push(30, 'AA');

//基于原生JS操作键值对的方法，也可以向末尾追加一项新的内容

ary[ary.length] = 40;
console.log(res, ary);
```

##### `unshift`

```js
// unshift: 向数组开始位置增加内容
// @params
// 多个任意类型
// @return
// 新增后数组的长度
let ary = [10, 20];
let res = ary.unshift(30, 'AA');
console.log(res, ary); //=>4 [30,'AA',10,20]
//基于原生ES6展开运算符，把原有的ARY克隆一份,在新的数组中常见第一项，其余的内容使用原始ARY中的信息即可，也算实现了向开始追加的效果
ary = [100, ...ary];
console.log(ary); //=>[100,30,'AA',10,20]
```

##### `pop`

```js
// pop: 删除数组中的最后一项
// @params
// @return
// 删除的哪一项
let ary = [10, 20, 30, 40];
let res = ary.pop();
console.log(res, ary); //=>40 [10, 20, 30]
//基于原生JS让数组长度干掉一位，默认干掉的就是最后一项
//ary[2] =null;//=>假删除
//console.log(ary); //=>[10,20,null]

//delete ary[2];
//console.log(ary); //[10,20,empty]

ary.length--; //=>ary.length =ary.length-1;
console.log(ary);
```

##### `shift`

```js
// shift: 删除数组中的第一项
// @params
// @return
// 删除的哪一项
let ary = [10, 20, 30, 40];
let res = ary.shift();
console.log(res, ary); //=>10 [20, 30，40]

//基于原生JS中的DELETE，把数组当做普通的对象，确实可以删除到某一项内容，但是不会影响数组本身的结构特点(length长度不会跟着修改)，真实项目中杜绝这样的删除使用
delete ary[0];
console.log(ary); //=>{1:30,2:40,length:3}
```

##### `splice`

```js
//splice :实现数组的增加、删除、修改
// @params
// n, m 都是数字 从索引n开始删除m个元素(m不写， 是删除到末尾)
// @return
// 把删除的部分用新数组存储起来返回

let ary = [10, 20, 30, 40, 50, 60, 70, 80, 90];
let res = ary.splice(2, 4);
console.log(res, ary); //=>[30, 40, 50, 60]  [10, 20, 70, 80, 90]

//基于这种方法可以清空一个数组,把原始数组中的内容一新的数组存储起来(有点类似数组的克隆，把原来数组克隆一份一摸一样的给新的数组)
// let res = ary.splice(0);
// console.log(res, ary); //[10, 20, 70, 80, 90]

//删除最后一项和第一项
ary.splice(ary.length - 1);
console.log(ary); //[10, 20, 70, 80]
ary.splice(0, 1);
console.log(ary); //[ 20, 70, 80]
```

```js
//splice :实现数组的增加、修改
// @params
// n, m ,x 从索引n开始删除m个元素，用x占用删除的部分
// n, 0 ,x 从索引n开始，一个都不删，把x放到索引n的前面
// @return
// 把删除的部分用新数组存储起来返回

// 基本功能，用插入的元素替代的删除元素
// let ary = [10, 20, 30, 40, 50, 60, 70, 80, 90];
// let res = ary.splice(1, 3, 40, 50, 60);
// console.log(res, ary); //=> [20, 30, 40] (9) [10, 40, 50, 60, 50, 60, 70, 80, 90]

//实现增加
// let ary = [10, 20, 30, 40, 50, 60, 70, 80, 90];
// let res = ary.splice(3, 0, 100);
// console.log(res, ary); //[]  [10, 20, 30, 100, 40, 50, 60, 70, 80, 90]

//向数组末尾追加
// let ary = [10, 20, 30, 40, 50, 60, 70, 80, 90];
// let res = ary.splice(ary.length, 100);
// console.log(res, ary); //[]  [10, 20, 30, 40, 50, 60, 70, 80, 90]

// 向数组开头追加
let ary = [10, 20, 30, 40, 50, 60, 70, 80, 90];
let res = ary.splice(0, 0, 100);
console.log(res, ary); //[]  [100, 10, 20, 30, 40, 50, 60, 70, 80, 90]
```

#### 2.数组的查询和拼接

>此组学习的方法，原来数组不会改变

##### `slice`

```js
//slice:实现数组的查询
// @params
// n, m 都是数字 从索引n开始，找到索引为m的地方(不包含m这一项,含头不含尾)
// @return
// 把找到的内容以一个新数组的形式返回
// 原数组不会被改变

// 基础用法，获取数组中的某一段切片
let ary = [10, 20, 30, 40, 50];
let res = ary.slice(0, 3);
console.log(res, ary); // [10, 20, 30]  [10, 20, 30, 40, 50]

//m不写是找到末尾
res = ary.slice(1);
console.log(res); //=>[20,30,40,50]
//数组的克隆，参数0不写也可以
res = ary.slice(0);
console.log(res); //=>[10,20,30,40,50]

//m不写是找到末尾
// res = ary.slice(1);
// console.log(res); //=>[20,30,40,50]

//数组的克隆，参数0不写也可以
// res = ary.slice(0);
// console.log(res); //=>[10,20,30,40,50]

//如果n/m为负数会怎么样，如果n>m又会怎样，如果是小数会怎样，如果是非有效数字会咋样，如果m或者n的值比最大索引都大会怎样？
// let ary = [10, 20, 30, 40, 50];
// console.log(ary[-2]); //undefined
// res = ary.slice(-3, -1); //slice方法会将你传入的负数，转换成从右往左数的元素个数
// console.log(res); //=>[30,40]

// let ary = [10, 20, 30, 40, 50];
// res = ary.slice(3, 1); //slice默认从左往右，起始下标大于了结束下标，返回空数组
// console.log(res); //=>[]

// let ary = [10, 20, 30, 40, 50];
// res = ary.slice(1.4, 3.6); //slice如果传下小数，会将小数向下取整，在使用
// console.log(res); //=>[20,30]

// let ary = [10, 20, 30, 40, 50];
// res = ary.slice('AA', 'BB'); //slice传入非有效数字，返回空数组
// console.log(res); //=>[]

// let ary = [10, 20, 30, 40, 50];
// res = ary.slice(5, 6); //slice中的m和n如果超出最大下标，返回空数组
// console.log(res); //=>[]
```

##### `concat`

```js
// concat: 实现数组拼接
// @params
// 多个任意类型值
// @return
// 拼接后的新数组
// 原数组不会被改变


// let ary1 = [10, 20, 30];
// let ary2 = [40, 50, 60];
// let res = ary1.concat();
// console.log(ary1, res); //=>如果不加参数，可以将元素克隆
       
let ary1 = [10, 20, 30];
let ary2 = [40, 50, 60];
let res = ary1.concat(ary2);
console.log(ary1, res); // [10, 20, 30]  [10, 20, 30, 40, 50, 60]
```

#### 3.把数组转换为字符串

##### `toString`

```js
// toString: 把数组转换为字符串
// @params
// @return
// 转换后的字符串，每一项用逗号隔开
// 原数组不会被改变

let ary = [10, 20, 30];
let res = ary.toString();
console.log(res); //=>"10,20,30"
console.log([].toString()); //=>""
console.log([12].toString()); //=>"12"
```

##### `join`

```js
// join:把数组转换为字符串
// @params
// 指定的分隔符(字符串格式)
// @return 
// 转换后的字符串(原来数组不变)
//原数组不变

// let ary1 = [10, 20, 30];
// let res = ary1.join(); //=>默认用逗号隔开
// console.log(res); //=>10,20,30

// let ary1 = [10, 20, 30];
// let res = ary1.join('+');
// console.log(res);//10+20+30
// console.log(eval(res)); //eval 将字符串格式的代码执行，60
```

##### `indexOf/lastIndexOf `

```js
// indexOf/lastIndexOf:检测当前项在数组中第一次或者最后一次穿线位置的索引值(在IE6-8不兼容)
// @params
// 要检测的这项内容
// @return 
// 这一项出现的位置索引值(数字)，如果数组中没有这一项，返回的结果是-1
//原数组不变

// let ary = [10, 20, 30];
// let res = ary.indexOf(10);
// console.log(res); //=>0;

// let ary = [10, 20, 30];
// let res = ary.indexOf(40);
// console.log(res); //=>-1

// let ary = [10, 20, 30];
// let res = ary.lastIndexOf(40);
// console.log(res); //=>-1

let ary = [10, 20, 30];
let res = ary.lastIndexOf(30);
console.log(res); //=>2

let ary1 = [10, 20, 30];
if (ary1.indexOf('AA' < 0)) {
    //不包含
}
console.log(ary1.includes(10)) //true
if (ary1.includes('AA')) {
    //false
}
```

#### 4.数组的排序或者排列

##### `reverse`

```js
// reverse: 把数组倒过来排序
// @params
//排序后的新数组
// @return
// 排序后的新数组
// 原数组会被改变

 let ary = [12, 15, 9, 28, 10, 22];
 let res = ary.reverse();
 console.log(res, ary); //[22, 10, 28, 9, 15, 12]  [22, 10, 28, 9, 15, 12]
```

##### `sort`

```js
// sort: 实现数组的排序
// @params
//可以没有，也可以是个函数
// @return
// 排序后的新数组
// 原数组会被改变

// let ary = [2, 3, 8, 6, 4, 5];
// let res = ary.sort(); //=>不传参的时候，无法排序2位数以上的数字(个位数默认从小到大排序)
// console.log(res); //=>[2, 3, 4, 5, 6, 8]

// let ary = [12, 15, 9, 28, 10, 22];
// ary.sort(function(n, m) {
//     return n - m; //从小到大排序
// }); //如果进行多位的排序，需要传入一个回调函数
// console.log(ary);

 let ary = [12, 15, 9, 28, 10, 22];
 ary.sort(function(n, m) {
   	   return m - n; //从大到小排序
 }); //如果进行多位的排序，需要传入一个回调函数
 console.log(ary);
```

#### 5.遍历数组中每一项方法

##### `forEach`

```
// forEach:遍历数组中的每一项内容
// @params
// 回调函数
// @return
// 没有返回值
// 原数组会被改变

let ary = [12, 15, 9, 28, 10, 22];
//基于原生JS实现数组遍历
// for (var i = 0; i < ary.length; i++) {
//     console.log('索引：' + i, '值' + ary[i]);
// }

let res = ary.forEach((item, index) => console.log('索引：' + index, '值' + item));
console.log(res); //=>没有返回值
```



`map`

`filter`

`find`

`reduce`

`some`

`every`

...

#### 6.数组去重

```js
//方案一：
// 1.循环原有数组中的每一项，没拿到一项都往新数组中添加
// 2.添加之前验证新数组中是否存在这一项，不存在就添加，存在就不添加

// 方法一
// let ary = [1, 2, 3, 1, 2, 1, 2, 3, 2, 1, 2, 3];
// //=>[1,2,3]
// let res = [];
// for (var i = 0; i < ary.length; i++) {
//     //1.拿到数组中的每一项值
//     var item = ary[i];
//     //2.添加之前验证新数组是否存在着一项
//     if (res.indexOf(item) >= 0) { //考虑兼容性
//         //如果新数组中存在item，就跳过本轮循环，不往新数组中添加item
//         continue;
//     }
//     //3.当新数组中存在item，则往新数组中添加
//     res.push(item);
// }
// console.log(res);


// 方法二
let ary = [1, 2, 3, 1, 2, 1, 2, 3, 2, 1, 2, 3];
//=>[1,2,3]
let res = [];
for (var i = 0; i < ary.length; i++) {
    let swt = 1;
    //1.拿到数组中的每一项值
    var item = ary[i];
    //2.添加之前验证新数组是否存在着一项
    for (var j = 0; j < res.length; j++) {
        if (res[j] === item) {
            swt = 0;
            continue;
        }
    }
    if (swt) {
        res.push(item);
    }
}
console.log(res);
```

```js
// 方案二、
// 先分别拿出数组中的每一项A
// 用这一项A和“他后面的每项”依次进行比较，如果遇到和当前项A相同的，则在原来数组中把这一项移除掉
// 不用includes/indexOf(这样保证兼容性)

let ary = [1, 3, 3, 1, 2, 1, 2, 3, 2, 1, 2, 3];
let res = ary.sort();
for (var i = 0; i < res.length; i++) {
    let item = res[i];
    for (var j = i + 1; j < res.length; j++) {
        if (item === res[j]) {
            res.splice(j, 1);
            j--; //=>因为数组塌陷问题的产生，所以需要j本轮不增加
        }
    }
}
console.log(res);
```

```js
// 方案三、
// 1.先分别拿出数组中的每一项A,以item:item的形式存入到对象当中
// 2.判断每一次存入的键值对是否存在，如果存在，则将当前数组中的元素删除
// 3.同样会产生'数组塌陷'问题(笔试题)
let ary = [1, 3, 3, 1, 2, 1, 2, 3, 2, 1, 2, 3];
// 1.创建对象
let obj = {};
// 2.循环数组中的每项，把每一项对象中进行存储=>item:item
for (var i = 0; i < ary.length; i++) {
    let item = ary[i];
    // 3.每一次存储之前进行判断：验证obj中是否存在这一项
    if (obj[item] != undefined) {
        //已经存在这一项
        ary.splice(i, 1);
        i--;
        continue;
    }
    obj[item] = item;
}
console.log(ary);
```

```js
//基于slice实现删除性能不好：当前项被删后，后面每一项的索引都要向前提一位，如果后面内容过多，一定影响性能
//方案三(优化版)
//1.把最后一项的值获取到替换当前这一项
//2.删除最后一项

let ary = [1, 3, 3, 1, 2, 1, 2, 3, 2, 1, 2, 3];
let obj = {};
for (var i = 0; i < ary.length; i++) {
    let item = ary[i];
    if (obj[item] != undefined) {
        ary[i] = ary[ary.length - 1];
        ary.length--;
        i--;
        continue;
    }
    obj[item] = item;
}
console.log(ary);
```

#### 7.封装函数

```js
// 封装函数
// 封装能实现某一项功能的函数

// unique:实现数组去重
// @params
//     ary[Array] 要去重的数组
// @return
//     [Array] 去重的新数组

let ary = [1, 3, 3, 1, 2, 1, 2, 3, 2, 1, 2, 3];

function unique(ary) {
    let obj = {};
    for (var i = 0; i < ary.length; i++) {
        let item = ary[i];
        if (obj[item] !== undefined) {
            ary[i] = ary[ary.length - 1];
            ary.length--;
            i--;
            continue;
        }
        obj[item] = item;
    }
    return ary;
}
console.log(unique(res));



// 基于ES6的Set(对应的Map)实现去重
// Set中的元素只会出现一次
let ary = [12, 23, 12, 15, 25, 23, 25, 14, 16];
ary = new Set(ary); //=>{12, 23, 15,25,14,...}
console.log(ary);
```



