---
title: "JavaScript基础笔记"
date: "2017-08-10"
---

# JavaScript基础笔记

## 1.JavaScript简介

一种基于对象和事件驱动并具有相对安全性并广泛用于客户端网页开发的脚本语言；

一种广泛用于客户端Web开发的脚本语言

**ECMAScript**：描述了该语言的语法和基本对象；

文档对象模型**DOM**：描述处理**网页内容**的方法和接口

浏览器对象模型**BOM**：描述与**浏览器**进行交互的方法和接口

## 2.JavaScript数据类型

### 基础类型

特点：存放在栈中，占据空间小，**大小固定，因此不可改变**

五种基本类型：**undefined、null 、number 、string 、boolean**

（1）undefined

在变量被声明，但未被初始化时为 undefined

```js
var a;

console.log(a);
```

判断变量是否为 undefined

```js
console.log(typeof a === ‘undefined’);
```

（2）null

表示一个空对象指针

```js
var b = null;

b = { name: ‘wang’ }
```

typeof 返回 object

```js
console.log(typeof null) // object

null === null // true
```

（3）number

浮点类型计算

（由于实际上是以二进制存在双精度 64 位的存储器里，所以会发生精度丢失的问题，导致小数计算时出现偏差：）

NaN

计算时**返回数值未返回的情况**，比如，除数为 0 的情况。

（4）string

| 符号 | 含义 |
| :--: | :--: |
|  \n  | 换行 |
|  \t  | 制表 |
|  \r  | 回车 |
|  \b  | 退格 |

字符串为不可变类型

```js
var a = ‘today’;

var b = a + ‘is sunday’;
```

（5）boolean

字面值有两个： true false

| 参数类型  | true         | false     |
| --------- | ------------ | --------- |
| Number    | 非  NaN,非 0 | NaN/0     |
| String    | 非空字符串   | 空字符串  |
| Object    | 非空对象     | null      |
| undefined |              | undefined |
| Boolean   | true         | false     |

### 引用类型

特点：存放的是**一个地址**

常用的应用类型：**object、array、Date、RegExp**等

（1）Object

创建方式：

```js
var a = {

 name: 'wang'

}  //  对象字面量
```

对象属性访问

```js
a[’name’];

a.name;
```

（2）array

创建方式：

```js
var a = new Array(10);

var b = new Array(1, 2, 3);  [1,2,3]

var c = [1,2,3];
```

检测类型：

```js
Array.isArray(value);

Object.prototype.toString.call(value);
```

常用数组方法：

```js
var a = [1,2];

var b = a.push(3);  // 3

var c = a.pop()   // 2
```

```js
var a = [1,2];
var b = a.unshift(3)  // return 3  [3,1,2]
var c = a.shift()  // return 2 [1, 2]
```

```js
var a = [1,2,3,4];
var b = a.reverse(); [4,3,2,1,5]
var c = a.sort();
var d = a.sort((n, m) => n >= m ? 1 : -1)
```

```js
var a = [12,3,4];
var c = a.concat(22,33,[12,34]);  // [12,3,4,22,33,12,34]
var d = a.slice(2,4) //  第一个参数起始位（包含）， 第二个参数结束位(不包含)
[…a.slice(0, 3), …a.slice(4)]
var e = c.splice(1, 1);  // [12,4,22,33,12,34] [3]
var e = c.splice(1, 2, ‘123’); // [12,’123’,33,12,34] 
var e = c.splice(2, 0, ‘111’); // 
```

```js
indexOf(value)
lastIndexOf(value);
```

```js
every();
map();
filter();
forEach();
some();
reduce();
reduceRight();
```

（3）Date

```js
var a = new Date()

a.getTime();

a.getMonth();
```

（4）RegExp

```js
var reg = / pattern /flags

// flags:  g  i m
```

常用的正则匹配的方法： exec()、match()、test()

```js
var text = "mom and dad and baby";
var pattern = /mom( and dad( and baby)?)?/gi;
var matches = pattern.exec(text);
alert(matches.index); 
alert(matches.input); 
alert(matches[0]); 
alert(matches[1]); 
alert(matches[2]);
//0
// "mom and dad and baby” 
// "mom and dad and baby” 
// " and dad and baby"
// " and baby”
```

## 3.作用域

### 全局环境

Javascript 中当代码开始执行时，会**首先创建一个全局的执行上下文**，全局环境中的变量都存储在该执行上下文中。同时为了便于管理，这个全局的**执行上下文会被推入执行上下文栈**。在 javascript 运行过程中，**全局执行上下文始终保持在栈底**，直到**程序运行结束，才会被推出并销毁**

### 函数环境

当一个**被声明的函数被调用**时，会创建**独属于这个函数**的执行上下文，并且将该执行上下文推入执行上下文栈，函数**调用结束后**，函数对应的**执行上下文**被推出并销毁。要注意的是在这个函数中如果调用了另外的函数B，则**又会创建这个函数 B 的执行上下文，并推入栈**。

个人理解，执行上下文**相当于一个函数执行的环境**，javascript 将其存储在执行上下文栈中，在这个环境中**保存了该函数可以访问的变量，以供函数运行时调用**。而如果我们在函数中不断地创建新的函数，调用函数，则执行上下文栈会不断被推入上下文，如果**调用次数过多，超过了堆栈可容纳的大小，则会造成堆栈溢出。这就是为什么有些递归次数过多的程序会发生堆栈溢出的问题。**

### 执行上下文

执行上下文中主要包含

```js
context: {
    VO,      // 变量对象
    scope,  // 函数作用域链
    this,   // 函数 this 指向
}
```

```js
VO = {
   arguments: {},  // 参数
   a,  // 声明的变量
   c: reference to function c,  // 声明的函数
}
```

**注意：**

**JS没有块级作用域(不包括 ES6 let/const）**

```js
if (true) {
  var color = "blue";
}
alert(color); //“blue"

if (true) {
  let color = "blue";
}
alert(color); //“blue"

```

在 HTML 中, 全局变量是 window 对象: 所有数据变量都属于 window 对象。

局部变量在函数执行完毕后销毁。

全局变量在页面关闭后销毁。

## 4.函数（递归、闭包、this 指向）

声明函数的方式有两种： 

函数声明

```js
function getName(){}
```

函数表达式

```js
var getName = function(){}
```

```js
console.log(getName());   // 可执行
function getName(){}

console.log(getName());  // 报错
var getName = function(){}
```

### 递归

```js
function factorial (n) { 
  if (n === 1) { 
   return 1; 
  } 
  return n * factorial (n — 1); 
}
```

#### 闭包：

```js
function getSomething(){
    var a = 12;
    function doSomething(b){
        var c = b + a;
        console.log(c);
    }
    return doSomething
}

const doSome = getSomething();
doSome(2);  // 14
doSome(3);  // 15

```

闭包指函数内部的函数被返回出去之后，在**外侧函数被销毁后仍可以访问外侧函数内部的变量**。



（其实是将这个变量加入到了内部函数的作用域链中：)

[[scope]]: [

  dosthScope:{arg, c}

  getstScope:{a = 12}

  globalScope

]

### this 指向

this 指向，一般按情况分为四种

隐式绑定（普通绑定，在编程过程中较为常见）

显式绑定（使用 call，apply 等方法进行手动绑定）

new 关键字绑定 （创建实例时构造方法中的 this 指向）

”词法“绑定（箭头函数）



**隐式绑定：**

指向调用函数的对象, 对象必须使用 obj.function() 的形势调用方法

```js
const user = {
  name: 'nena',
  get: function() {
    console.log(this.name);
  }
}
user.get(); // nena
var get_1 = user.get;
get_1(); // undefined
```

**显式绑定：**

```js
const user = {
  name: 'nena',
}
function get() {
  console.log(this.name);
get() // undefined
get.call(user);
```

**New 关键字绑定**

（构造器中的 this 执行 new 出的实例）:

```js
function Person(name, age) {
 this.name = name;
 this.age = age;
}
const p = new Person('nena', 0);
console.log(p.name);
```

**词法绑定（箭头函数中）：**

```js
var user =  {
  lang: ['java', 'sql', 'js'],
  getLang: function () {
     return this.lang.reduce ((pre, cur, i) => {
        if(i === this.lang.length - 1){
           return `${pre} and ${cur}.`;
        }else {
           return pre ? `${pre}, ${cur}` : cur;
        }
     }, '')
  }
}
var s = user.getLang();
console.log(s);
```

箭头函数中的 this 指向最近作用域的 this

如果找不到 this，则落于全局，严格模式下为 undefined, 非严格模式下为 window

## 5.原型链，继承

### 原型链

每创建一个函数，就会为这个函数**默认生成prototype的属性**，该属性指向函数的原型对象，

而原型对象中也会默认生成constructor属性，指向这个函数。

通过构造函数可以为原型对象添加属性和方法。

在**创建实例时，实例中将包含一个指针，指向构造函数的原型对象**。

这个连接存在于实例和原型对象之间，而不是实例和构造器之间。

以上所说的关系如下图所示。

![image-20210705160819992](C:\Users\CDLX\AppData\Roaming\Typora\typora-user-images\image-20210705160819992.png)

```js
function Person(){}

Person.prototype.name = "nena";
Person.prototype.age = 23;
Person.prototype.get = function () {
    console.log(this.name);
};

var person1 = new Person();
var person2 = new Person();

```

### 原型链继承

将一个原型对象的实例赋给另一个原型对象，那么这个原型对象中将会有指针指向第一个原型对象。关系如下图所示

<img src="C:\Users\CDLX\AppData\Roaming\Typora\typora-user-images\image-20210705161011791.png" alt="image-20210705161011791" style="zoom:100%;" />

代码实现

```js
function Person() {
    this.hasName = true;  
}
Person.prototype.get = function () {
    return this.hasName;
};
function Student(){
    this.hasSalary = false;
}
Student.prototype = new Person();
Student.prototype.getSalary = function(){
    return this.hasSalary;
};
var student = new Student();
console.log(student.get());
```

## 6.DOM与事件处理

### DOM文档对象模型：

**HTML DOM** 模型被构造为**对象**的树：

![image-20210705162207616](C:\Users\CDLX\AppData\Roaming\Typora\typora-user-images\image-20210705162207616.png)

常用的节点操作方法：

```js
var div = document.getElementById("myDiv");
alert(div.id); 
alert(div.className);
alert(div.getAttribute("id")); 
alert(div.getAttribute("class"));
div.setAttribute("id", "someOtherId"); 
div.setAttribute("class", "ft");
div.removeAttribute("class");

```

节点获取

```js
getElementId()
getElementsByClassName()
getElementsByName()
getElementsByTagName()

querySelector()  // 接收 css 选择符

var myDiv = document.querySelector("#myDiv”);
var selected = document.querySelector(".selected”); // 只获取一个
var selecteds = document.querySelectorAll(".selected”); //  获取所有
```

### BOM

BOM： 浏览器对象模型，是 javascript 可以运行在 web 浏览器的基础。

常用 window 属性，方法：

```js
window.innerWidth
window.innerHeight
window.screenTop
window.screenLeft

window.open()

setTimeout()
clearTimeout()

setInterval()
clearInterval()
```

![image-20210705162545357](C:\Users\CDLX\AppData\Roaming\Typora\typora-user-images\image-20210705162545357.png)

| 属性     | 作用             |
| -------- | ---------------- |
| hash     | ‘#contents'      |
| host     | ’21.23.12.34:80' |
| hostname | '21.23.12.34'    |
| href     | 完整  url        |
| pathname | 目录             |
| port     | 端口             |
| protocol | http、https      |
| search   | ?name=xxx        |

History： 记录历史地址

```js
history.go(-1);
history.go(1);
history.back();
history.forward();
```

### 事件处理

（1）事件冒泡

![image-20210705162715919](C:\Users\CDLX\AppData\Roaming\Typora\typora-user-images\image-20210705162715919.png)

（2）事件捕获

![image-20210705162737167](C:\Users\CDLX\AppData\Roaming\Typora\typora-user-images\image-20210705162737167.png)

（3）先捕获后冒泡

![image-20210705162756404](C:\Users\CDLX\AppData\Roaming\Typora\typora-user-images\image-20210705162756404.png)

DOM0 事件处理程序：

```js

var btn = document.getElementById("myBtn"); 
btn.onclick = function(){
   alert("Clicked"); 
   console.log(this.id);
   console.log(this.value);
};
```

DOM2 事件处理程序：

```js
var btn = document.getElementById("myBtn");
var f = function(){
  alert(this.id)
}
btn.addEventListener(‘click’, f, false);
// 将会在事件冒泡阶段被触发
// true, 将会在事件捕获阶段被触发
```

事件处理时事件

![image-20210705162916393](C:\Users\CDLX\AppData\Roaming\Typora\typora-user-images\image-20210705162916393.png)

## 7.json&Ajax

### JSON

JSON数据结构可以方便地解析为javascript对象。

JSON格式的数据中属性名必需且一定要加双引号。

JSON 对象例子：

```js
{
    "name":"nena",
    "age":23,
    "like":["shin","xuan","wan"],
    "get":{
            "music":"rock",
            "book":"gone with the wind"
          }
}
```

stringify()方法用于将javascript对象序列化为JSON对象

stringify() 不传递参数时：

```js
var person={
    name:"nena",
    age:23,
    like:["shin","xuan","lizhi”],
    p: { name: “nena” }
}
var JSONarr = JSON.stringify(person, );
    alert(JSONarr);
//{"name":"nena","age":23,"like":["shin","xuan","lizhi"]}
```

传递参数：

第一个参数 可以是数组，也可以是函数（过滤函数）

第二个参数 为数字或者字符串

```js
var person={
    name:"nena",
    age:23,
    like:["shin","xuan","lizhi"]
};

var JSONarr = JSON.stringify(person,["age","like"]);
    alert(JSONarr);   
//{"age":23,"like":["shin","xuan","lizhi"]}
```

当第一个参数做为数组，可以选择JSON中需要的属性值。

当第一个参数作为函数，可以过滤JSON的键值对，也可以对某个键的值做修改

```js
var person={
    name:"nena",
    age:23,
    like:["shin","xuan","lizhi"]
};
var JSONarr = JSON.stringify(person,function (key,value) {
    switch(key){
        case "name":
            return ”nena";
        case "age":
            return undefined;
        default:
            return value;
    }
});
    alert(JSONarr);
     //{"name":”nena","like":["shin","xuan","lizhi"]}

```

第二个参数为数字或者字符串 表示JSON数据中的缩进

```js
var person={
    name:"nena",
    age:23,
    like:["shin","xuan","lizhi"]
};

var JSONarr = JSON.stringify(person,null,4);
    alert(JSONarr);

```

parse()方法将JSON数据解析为javascript对象

```js
var person={
    name:"nena",
    age:23,
    like:["shin","xuan","lizhi"]
};
var JSONarr = JSON.stringify(person);
var person1 = JSON.parse(JSONarr);
    alert(person1.age); //23
```

![image-20210705163530620](C:\Users\CDLX\AppData\Roaming\Typora\typora-user-images\image-20210705163530620.png)

### Ajax

Ajax: JavaScript执行异步网络请求

```js
if (window.XMLHttpRequest) { // Mozilla, Safari, IE7+ ...
    httpRequest = new XMLHttpRequest();
} else if (window.ActiveXObject) { // IE 6 and older
    httpRequest = new ActiveXObject("Microsoft.XMLHTTP");
}
var request = new httpRequest(); // 新建XMLHttpRequest对象
request.onreadystatechange = function () { // 状态发生变化时，函数被回调
    if (request.readyState === 4) { // 成功完成
        // 判断响应结果:
        if (request.status === 200) {
            // 成功，通过responseText拿到响应的文本:
            console.log(request.responseText)
        } else {
            // 失败，根据响应码判断失败原因:
            console.log(request.status);
        }
    }
}
// 发送请求:
request.open('GET', '/api/categories');
request.send();

```

## 8.任务队列和事件循环

js是单线程非阻塞的，为了在浏览器运行，操作 dom 时保持同步性，js 被设计为单线程。

HTML5 web - worker 可以创建子线程，但是子线程无法独立执行，并且没有进行 i/o 操作的权限。

单线程下实现非阻塞的机制就在于 js 中的**事件循环**：

**同步函数的执行过程**： 在 js 开始执行代码时会根据声明的函数创建一个个执行上下文，将其推入执行栈中，在实际执行函数时推出最顶的一个执行上下文激活为当前执行环境，然后依据其中的数据进行执行，执行完毕后销毁该环境。

**异步函数的执行过程**：执行时首先会被挂起（有一种说法时会被异步现成调用执行，具体内容有待查询），将其回调推送到任务队列中，在执行栈的内容后，主线程会去循环事件队列，查看是否有需要执行的回调，有的话执行回调。

![image-20210705163718612](C:\Users\CDLX\AppData\Roaming\Typora\typora-user-images\image-20210705163718612.png)

任务队列分为两种，宏任务队列和微任务队列，在主线程循环查看事件队列时首先执行完主执行栈（也相当于一个宏任务）会首先查看微任务，如果有的话先一次性执行完微任务，然后再执行一个宏任务，执行完以后再看有没有微任务。

微任务有：**new Pomise().then(), Promise.resolve().then(), process.nextTick()**

宏任务有：**setTimeout() setInterval() i/o操作 ui 交互事件 整个script脚本**

```js
console.log('script start');
setTimeout(function() {
  console.log('setTimeout');
}, 0);
Promise.resolve().then(function() {
  console.log('promise1');
}).then(function() {
  console.log('promise2');
});
console.log('script end');

// 最后输出:
// script start、script end、promise1、promise2、setTimeout
```

