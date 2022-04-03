# DOM及其基础操作

>DOM:document object model 文档对象模型，提供一些属性和方法供我们操作页面中的元素

### 获取DOM元素的方法

- document.getElementById() 指定
- [context].getElementsByTagName() 在指定上下文(容器)，通过标签名获取一组元素集合
- [context].getElementsByClassName() 在指定上下文中，通过样式类名获取一组元素集合(不兼容IE6-8)
- document.getElementsByName() 在整个文档中，通过标签的NAME属性值获取一组元素集合(在IE中只有表单元素的NAME才能识别，所以我们一般只有应用于表单元素处理)
- document.head/document.body/document.documentElement 获取页面中的 HEAD/BODY/HTML 三个元素
- [context].querySeletor([selector]) 在指定上下文中，通过选择器获取到指定的元素对象
- [context].querySeletorAll([selector]) 在指定上下文中，通过选择器获取到指定的元素对象集合

JS中的节点和描述节点之间关系的属性

>节点：Node(页面中所有的东西都是节点)
>
>节点集合：NodeList(getElementsByName/querySelectorAll 获取的都是节点集合)

- 元素节点
  - nodeType:1
  - nodeName:大写的标签名
  - nodeValue:null
- 文本节点
  - nodeType:3
  - nodeName:'#text'
  - nodeValue:文本内容
- 注释节点
  - nodeType:8
  - nodeName:'#commen'
  - nodeValue:null
- 文档节点
  - nodeType:9
  - nodeName:'#document'
  - nodeValue:null

描述这些节点之间关系的属性

- childNodes:获取所有的子节点
- children:获取所有元素的子节点(子元素标签集合)
- firstChild:获取第一个子节点
- lastChild:获取最后一个子节点
- firstElementChild/lastElementChil:获取第一个和最后一个元素子节点(不兼容IE6-8)
- previousSibling:获取上一个哥哥节点
- nextSibling:获取下一个弟弟节点
- parentNode:获取父亲节点
- previousElementSibling/nextElementSibling:获取上一个哥哥元素节点和获取下一个弟弟元素节点
- ......

#### jQuery小例子

```js
function children(context) {
    var resAry = [];
    //1.获取到所有元素的子节点
    var allNodeChild = context.childNodes;
    //2.遍历所有的子节点,判断nodeType====1,就是元素节点,添加到返回的数组中
    for (var i = 0; i < allNodeChild.length; i++) {
        var item = allNodeChild[i];
        item.nodeType === 1 ? resAry.push(item) : null;
    }
    return resAry;
}
console.log(children(box));



//获取上一个哥哥元素节点
// var fanqi = document.getElementById('fanqi');

// function previ(context) {
//     var ele = context.previousSibling;
//     while (ele.nodeType !== 1) {
//         ele = ele.previousSibling;
//     }
//     return ele;
// }
// console.log(previ(fanqi));
```

#### 在JS中动态增删改元素

`createElement 创建元素对象`

`createNodeElement 创建文本节点`

`appendChild 把节点添加到容器的末尾`

`insert 把节点添加到指定容器中指定元素前面`

```js
  //创建box节点
        var box = document.createElement('div');
        box.style.width = '200px';
        box.style.height = '200px';
        box.style.backgroundColor = 'red';

        var text = document.createTextNode('俺是红筛滴');
        box.append(text);
        //放到父元素的末尾，类似push
        document.body.appendChild(box);
        //插入到指定元素前面
        //父节点.insertBefore(需要插入的节点，beforeElement);
        document.body.insertBefore(box, span);
```



`cloneNode(reue/false) 克隆元素或节点`

`removeChild 移除容器中的某个元素`

```js
var box = document.getElementById('box');
        var li = box.querySelector('li:nth-child(3)');
        var ol = li.querySelector('ol');
        var text = ol.previousSibling;
        console.log(text);
        // // clongNode()的参数为false时，浅克隆，为true时，深克隆
        // var liClone = li.cloneNode(true);
        // console.log(liClone);
        // var liClone = li.cloneNode(true);
        // console.log(liClone);
        li.removeChild(text);
```

`setAttribute/getAttribute/removeAttribute 设置获取移出元素`

`自定义属性信息(这种方式是把自定义属性放到元素结构上)`

```js
<button>1</button>
    <button>2</button>
    <button>3</button>
    <script>
        var btn = document.querySelectorAll('button');
        for (var i = 0; i < btn.length; i++) {
            //实现原理1：通过给对象(堆内存)添加一个新的属性的方式，来将每一个i的值，进行保存在使用的时候去对象的身上寻找属性
            //实现原理2：给相对应的标签添加自身有属性并保存相应的值，在需要的时候，通过标签的属性去获取这个值

            //注意：通过给对象添加属性的方式，只能用对象的获取方式(obj.属性名)，设置在元素结构上的内容只能通过相对应的方式类获取(getAttribute)
            var btns = btn[i];
            btns.setAttribute('myIndex', i);
            btn[i].onclick = function() {
                alert(this.getAttribute('myindex'));
            }
        }
        var btn = document.querySelector('button');
        btn.removeAttribute('myindex');
```



#### 



