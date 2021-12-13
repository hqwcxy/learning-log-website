---
title: "BOM"
date: "2017-08-10"
---

## BOM

#### 一、BOM介绍：

1、BOM（ Browser Object Model）---> 浏览器对象模型。

2、BOM 作用：主要提供了访问和操作浏览器各组件的方式。

window浏览器窗口对象是js中最大的对象。其他所有的对象，都是window的子对象

document文档对象，代表一个网页

location地址栏对象，对地址栏的操作一些方法

navigatior浏览器软件对象，主要用来判断用户用的是什么浏览器，可以解决兼容性问题

screen屏幕对象，可以获取屏幕相关的信息

history历史记录对象，可以对浏览器的历史记录进行相关的操作

```
注意点：

1、window是全局浏览器内置顶级对象 表示浏览器中打开的窗口（没有应用于window对象的公开标准，不过所有浏览器都支持该对象）Window 对象表示一个浏览器窗口或一个框架。

2、在客户端 JavaScript 中，Window 对象是全局对象，所有的表达式都在当前的环境中计算。也就是说，要引用当前窗口根本不需要特殊的语法，可以把那个窗口的属性作为全局变量来使用。

例如，可以只写 document，而不必写 window.document。

同样，可以把当前窗口对象的方法当作函数来使用，如只写 alert()，而不必写 Window.alert()。

除了上面列出的属性和方法，Window 对象还实现了核心 JavaScript 所定义的所有全局属性和方法。
```

#### 二、window对象常用的方法

```js
1.prompt() 显示可提示用户输入的对话框

2.alert() 显示一个带有提示信息和一个“确定”按钮的警示对话框

3.confirm() 显示一个带有提示信息、“确定”和“取消”按钮的对话框

4.close() 关闭浏览器窗口   close()方法用于关闭浏览器窗口，语法：window.close（）;

5.定时器

a、间隔定时器setInterval（开启）  clearInterval（关闭）

b、超时定时器setTimeout（开启）   clearTimeout（关闭）   
          
6. open()方法   功能：打开一个新的浏览器窗口
```

#### 三、location地址栏对象

```js
1、hostname 设置或返回当前URL的主机名

2、href：获取地址栏中完整的地址。可以实现JS的网页跳转。location.href = “http://www.sina.com.cn”;

3、pathname：文件路径及文件名

4、protocol：协议，如：http://、ftp://

5、hash：锚点名称。如：#top

6、reload([true])：刷新网页。true参数表示强制刷新  

a、是网页浏览后，一般会在本地留下缓存，普通刷新的话，浏览器会优先获取缓存里的资源代替从服务器上请求，以提高访问速度。

b、强制刷新就是告诉浏览器不要获取缓存，重新从服务器请求网页上的所有资源，适用于开发测试或者某些资源更新。

7、注意：所有的属性，重新赋值后，网页将自动刷新。

<meta  http-equiv = “refresh”  content = “5;url=http://www.sina.com.cn” />
```

#### 四、navigator对象

```
1、appName：浏览器软件名称   appCodeName

2、appVersion：浏览器软件的核心版本号。

3、platform：平台

4、userAgent浏览器版本信息
```

[浏览器历史](https://zhidao.baidu.com/question/1767408752449075980.html)

#### 五、history对象

```
1、back（）  后退

2、forward（） 前进

3、go（） 

4、history.back（）===  history.go（-1） 浏览器中的  后退

5、history.forward() === history.go  ( 1 )   浏览器中的  前进 

```

#### 六、screen屏幕对象

```js
1、Width：返回屏幕的宽度，只读属性。  window.screen.width 

2、Height：返回屏幕的高度，只读属性。 window.screen.height

3、availWidth：屏幕的有效宽度，不含任务栏。只读属性。

4、availHeight：屏幕的有效高度，不含任务栏。只读属性。
```

#### 七、window对象事件

```
1、window.onload 当网页加载完成，指<body>标记的所有内容全部加载完成，才触发该事件(条件)

2、为窗口添加滚动条事件

onscroll 滚动事件

scrolltop 垂直滚动条滚动的距离
scrollleft 水平滚动条滚动的距离
 
window.innerHeight - 浏览器窗口的可见高度 
window.innerWidth - 浏览器窗口的可见宽度 

兼容写法：var scrolltop = document.documentElement.scrollTop||document.body.scrollTop; 

3、window.onresize 事件会在窗口或框架被调整大小时发生
```

使用JS操作CSS中的各种属性。JS只能操作或修改行内样式，对于类样式，通过className来赋值。

如：imgObj.className=”imgClass”;

1、style对象

每个HTML标记，都有一个style属性。但这个style属性又是一个style对象。  

那么，这个style对象属性有哪些？style对象的属性，与CSS中的属性，一一对应。

因此，style对象用来代替CSS。

如：imgObj.style.border=”1px solid red”;

2、style对象属性与CSS属性的转换

(1)、如果是一个单词，style对象属性，与CSS属性一样。

(2)、如果是多个单词，第一个单词全小写，后面每个单词首字母大写，并去掉中划线。

## DOM

#### 一、DOM对象介绍

1、DOM Document Object Model ，文档对象模型。我们可以把网页中的所有“东西”看成是“对象”。

2、DOM是W3C制定的网页标准或规则，而这个标准，在浏览器中，以“对象”的形式得以实现。

3、DOM的官方定义：DOM可以使脚本，动态的访问或操作，网页的内容、网页外观、网页结构。

#### 二、DOM的分类

1、核心DOM：提供了同时操作HTML文档和XML文档的公共的属性和方法。

2、HTML DOM：针对HTML文档提供的专用的属性方法。

3、XML DOM：针对XML文档提供的专用的属性和方法。(了解)

4、CSS DOM：提供了操作CSS的属性和方法。

5、Event DOM：事件对象模型。如：onclick、 onload等。（讲事件时再说）

#### 四、核心DOM的操作

1、认识DOM中元素节点类型：

```
document文档节点，代表整个网页，不代表任何HTML标记。但它是html节点的父节点

element元素节点，指任何HTML标记。每一个HTML标记就称一个“元素节点”。它可以有文本节点和属性节点

attribute属性节点。指HTML标记的属性

text节点。是节点树的最底节点
```

2、DOM中访问节点

```
firstChild：第1个子节点

lastChild：最后1个子节点

childNodes：子节点列表，是一个数组  childNodes[0]

parentNode：父节点

nodeName：节点名称  返回标签名

nodeValue 属性节点的的属性值

nodeType 节点类型，返回值是数字  

如果节点是元素节点，则 nodeType 属性将返回 1。如果节点是属性节点，则 nodeType 属性将返回 2。返回3是文本节点。如果是注释节点，返回8

查找<html>标记的方法

document.documentElement

查找<body>标记的方法

document.body
```

3、对节点的属性操作

```
setAttribute(name,value)：给某个节点添加一个属性

getAttributeNode(name)：获取某个节点属性的值

removeAttribute(name)：删除某个节点的属性
```

4、创建节点

```
document.createElement(tagName)：创建一个指定的HTML标记，一个节点

tagName：是指不带尖括号的HTML标记名称  

举例：var imgObj = document.createElement(“img”)


parentNode.appendChild(childNode)：将创建的节点，追加到某个父节点下。

parentNode代表父节点，父节点必须存在。

childNode代表子节点。

举例：document.body.appendChild(imgObj)

box.insertBefore() 方法可在已有的子节点前插入一个新的子节点 先放要排在前面的元素， 再写其他元素

参数1表示新建的节点  参数2表示你要插入在哪个节点之前
```

5、删除节点

```
parentNode.removeChild(childNode)：删除某个父节点下的子节点。

parentNode代表父节点。

childNode代表要删除的子节点。

举例：document.body.removeChild(imgObj)

remove()直接删除当前项
```

#### 五、HTML DOM的操作

核心DOM中，提供的属性和方法，已经可以操作网页了。为什么还要有HTMLDOM呢？

如果在核心DOM中，网页中节点层级很深时，访问这个节点时将十分麻烦。

那么，HTMLDOM中就提供了通过id直接找节点的方法，而不用再HTML根节点开始。

```
1、getElementById()

功能：查找网页中指定id的元素对象。

语法：var obj = document.getElementById(id)

2、getElementsByTagName(tagName)

功能：查找指定的HTML标记，返回一个数组

语法：var arrObj = parentNode.getElementsByTagName(tagName)

参数：tagName是要查找的标记名称，不带尖括号。

返回值：返回一个数组。如果只有一个节点，也返回一个数组。


3、 getElementsByName("Name")

功能：通过name值获取元素，返回值是数组，通常用来获取有name的input的值

4.getElementsByClassName()  

功能：通过class名获取元素，返回值是数组

ES5新增选择器：

5.document.querySelectorAll();    //强大到超乎想象，支持IE8+。ECMAScript借鉴了jQuery选择器的

6.document.querySelector();  返回单个元素
```

#### 六、元素属性的对象：

 a、在HTML中叫“标记”  b、 在DOM中叫“节点”    c、在JS中叫“对象”

```js
tagName：标签名称，与核心DOM中nodeName一样

className：CSS类的样式

id：同HTML标记id属性一样

title：同HTML标记的title属性一样

style：同HTML标记的style属性一样

innerHTML：包含HTML标记中的所有的内容，包括HTML标记等
```

#### 七、CSS DOM动态样式

```js
使用JS操作CSS中的各种属性。JS只能操作或修改行内样式，对于类样式，通过className来赋值。

如：imgObj.className=”imgClass”;

1、style对象

每个HTML标记，都有一个style属性。但这个style属性又是一个style对象。  

那么，这个style对象属性有哪些？style对象的属性，与CSS中的属性，一一对应。

因此，style对象用来代替CSS。

如：imgObj.style.border=”1px solid red”;

2、style对象属性与CSS属性的转换

(1)、如果是一个单词，style对象属性，与CSS属性一样。

(2)、如果是多个单词，第一个单词全小写，后面每个单词首字母大写，并去掉中划线。
```

#### 八、节点的操作

父（parent）、子（child）和同胞（sibling）等术语用于描述这些关系。父节点拥有子节点。同级的子节点被称为同胞（兄弟或姐妹）

```
childNodes 获取当前元素节点的所有子节点

firstChild 获取当前元素节点的第一个子节点

lastChild 获取当前元素节点的最后一个子节点

previousSibling 获取当前节点的前一个同级节点 -(678不支持)

nextSibling 获取当前节点的后一个同级节点 -(678不支持)

以上五中方法都包含空白文本节点

firstElementChild   获取当前元素节点的第一个元素子节点

lastElementChild  获取当前元素节点的最后一个元素子节点

previousElementSibling 查找当前元素的上一个元素

nextElementSibling  查找当前元素的下一个元素  都是兄弟关系

parentNode 获取当前节点的父元素

children 获取所有的子节点  不返回其他节点
```

1、获取节点

```javascript
//getAttribute()和getAttributeNode()区别，前者获取到的是属性节点的值，后者获取到的是属性节点
var box = document.querySelector('.box');
console.log(box.getAttribute('class'));
console.log(box.getAttributeNode('class'));
```

2、创建节点

```javascript
//创建一个节点
var div = document.createElement('div');
//添加到body里面
document.body.appendChild(div);
//可以给节点一个内容
div.innerHTML = '这是创建出来的div节点';

//参数1表示要添加的元素  参数2表示在添加的元素的后面元素
box.insertBefore(span, p);
```



3、设置节点

<font color=red>注意点：通过这种方式设置的属性节点，必须要配合提供的方式一起来使用</font>

```javascript
参数1表示节点名称  参数2表示属性节点的值
box.setAttribute('id', 'box');
var pic = document.querySelector('img');
pic.setAttribute('src', 'img/bom.png');
pic.setAttribute('width', '200');
pic.setAttribute('style', 'width:200px;height: 200px;border: 1px solid;');
```

4、删除节点

```JavaScript
pic.removeAttribute('style');

//删除一个节点removeChild()
div.removeChild(p);
//remove()表示删除当前项
p.remove();
```

#### 九、DOM尺寸和位置

```
box.style.width
box.style.height
只能获取到内联style属性的CSS样式中的宽和高，如果有，获取;如果没有，则返回空

box.clientWidth
box.clientHeight
返回了元素大小，但没有单位，默认单位是px，如果设置了其他的单位，比如100em之类，返回出来的结果还会转换为px像素（不含边框） width + padding值

box.clientLeft
box.clientTop    获取左边框和上边框的宽度

box.scrollWidth
box.scrollHeight
获取滚动内容的元素大小（当元素出现滚动条时，此属性指全部滚动内容的宽高）返回了元素大小，默认单位是px。如果没有设置任何CSS的宽和高度，它会得到计算后的宽度和高度  整个内容的

box.offsetWidth
box.offsetHeight
返回了元素大小，默认单位是px。如果没有设置任何CSS的宽和高度，他会得到计算后的宽度和高度
包含盒模型中除margin以外的宽高（包含边框）最稳定，使用最频繁

box.offsetLeft    需要定位参照  

box.offsetTop     获取元素当前相对于offsetParent父元素的位置
```

getComputedStyle().样式名  方法用于获取指定元素的 CSS 样式。获取的样式是元素在浏览器中最终渲染效果的样式。

参数1表示元素， 不能设置引号。 参数2表示伪对象（一般设置为空）

语法：getComputedStyle(元素名称).属性；

currentStyle.样式名  只有IE浏览器支持，其他浏览器都不支持  如果当前元素没有设置样式，则返回它的默认属性

获取非行内样式（兼容问题）

```js
function getStyle(obj, name){
    if(window.getComputedStyle){
        //非IE浏览器
        return getComputedStyle(obj, null)[name];
    }else{
        //针对IE浏览器
        return obj.currentStyle[name];
    }
}
```
