---
title: "HTML"
date: "2017-08-10"
---

# HTML

## 1.HTML介绍

## 2.HTML结构与语法

### 结构

```html
<!DOCTYPE html>
<html>

<head>
    <meta charset="utf-8">
    <title>
        first page
    </title>
</head>
<h1>标题1</h1>
<h2>标题2</h2>
<h3>标题3</h3>
<p>内容</p>
</html>
```

#### <!DOCTYPE>声明

​	标示当前 HTML 文档的版本信息

#### `<html>`

此标签为 HTML 文档的根元素，只能有**一个**。

#### `<head>`

`<html>`的直接子元素，`<head>`中可以设置文档的元(meta)数据，不会显示在视图中，可以在其中设置如 浏览器标题 等属性

-  `<title>`标签定义了不同文档的标题,在 HTML/XHTML 文档中是必须的,浏览器工具栏的标题。
- `<base>` 标签描述了基本的链接地址/链接目标，该标签作为HTML文档中所有的链接标签的默认链接。

```html
<base href="http://www.mafengshe.com/a/" target="_blank">
```

* `<link>`标签定义了文档与外部资源之间的关系,通常用于链接到样式表

```html
<link rel="stylesheet" type="text/css" href="style.css">
```

* `<style>`标签定义了HTML文档的样式文件引用地址,指定样式文件来渲染HTML文档

```html
<style type="text/css">
  body {background-color:yellow}
  p {color:blue}
</style>
```

 

`<meta>`标签提供了元数据.元数据也不显示在页面上，但会被浏览器解析。META元素通常用于指定网页的描述，关键词，文件的最后修改时间，作者，和其他元数据。元数据可以使用于浏览器（如何显示内容或重新加载页面），搜索引擎（关键词），或其他Web服务。一般放置于`<head>`区域

- 定义文档的字符集

  ```html
  <meta charset="utf-8">
  ```

- 为网页定义描述内容

  ```html
  <meta name="keywords" content="HTML, CSS, JavaScript">
  ```

- 定义网页作者

  ```html
  <meta name="author" content="mafengshe">
  ```

- 定时刷新当前页面（30秒）

  ```html
  <meta http-equiv="refresh" content="30">
  ```



- `<script>`标签用于加载脚本文件，如： JavaScript。在标签内部书写脚本或引入脚本文件位置

  ```html
  <script type="text/javascript">
    document.write("Hello World!")
  </script>
  ```

  ```html
  <script type="text/javascript" src="scripts.js"></script>
  ```

### 语法

1.正确嵌套

2.结束标签

3.属性用引号

4.元素名称和属性必须小写(XHTML 要求)

## 3.标签与属性

[标签大全详见](https://www.runoob.com/html/html-tag-name.html)

[常用标签速查](https://www.runoob.com/html/html-quicklist.html)

几个常用的

`<div>`块标签		`<span>`行内元素 		`<a>`超链接		`ol`有序列表

`<img src="a.jpg" width="100" height="10" alt="alt"/>`

1)**src**：图片地址

2)**alt**： 图片因为网络等原因未成功加载时候的显示文案内容

3)width/height：可以是像素值或者相对于父容器的百分比，两个属性可以只设置一个，另外一个值会按相应等比缩放

## 4.HTML5

### 新增元素

* 结构元素：selection、article、header、footer、nav、address

* 块级元素：aside、figure、figcaption、dialog、datalist

* 行内元素：mark、small、time、meter、progress、details、summary、menu、command

* input新类型：email、tel、url、number、range、search、color、date、month、week、time、datetime、datetime-local

* input新方法：heckValidity()：验证元素，setCustomValidity(errorMsg)：给元素设置错误消息

### 废除的元素

basefont、big、center、font、s、strike、tt、u、frameset、frame、noframes、applet、bgsound、blink、marguee

### 新增的属性

* 表单相关的属性：autocomplete、autofocus、form、list、min、max、step、multiple、novalidate、pattern、placeholder、required

* 表单重写属性：formaction、formenctype、formmethod、formnovalidate、formtarget

* 全局属性：contentEditable、designMode、hidden、spellcheck、tabindex

### 文件与拖放

`<input type="file" />`，multiple：允许选择多个文件，accept：过滤文件类型

* 文件API：

   FileList对象：通过 file.files 获取；

   File对象：name、size、type；

   FileReader：异步读取文件到内存

* 拖放API：

   设置要拖放对象的draggable局长为true；

   监听拖放事件：dragstart、drag、dragenter、dragover、dragleave、drop、dragend

* DataTransfer：

   属性：dropEffect、effectAllowed、types

   方法：void clearData(DOMString format)、void setData(DOMString format, DOMString data)、DOMString getData(DOMString  format)、void setDragImage(Element image, long x, long y)

### 多媒体播放

video：视频播放元素

audio：音频播放元素

### 绘制图形

Canvas

### 本地存储

* localStorage：对象存储的是没有截止日期的数据。当浏览器被关闭时数据不会被删除，在下一天、周或年中，都是可用的

* sessionStorage：针对一个 session 来存储数据（当关闭浏览器标签页时数据会丢失）

支持的属性与方法：

* 大小被建议限制在5M（不同浏览器有不同大小）

* getItem(key)：获取指定key所存储的value值

* key(index)：返回列表中对应对应索引的key值

* length：返回key/value对列表的长度

* removeItem(key)：从storage中删除一个对应的键值对

* setItem(key,value)：将value存储到key指定的字段

* clear()：清除storage中所有key/value 对

### 离线应用

HTML5 引入了应用程序缓存（Application Cache），这意味着可对 web 应用进行缓存，并可在没有因特网连接时进行访问

优势：

 离线浏览 - 用户可在应用离线时使用它们；

 速度 - 已缓存资源加载得更快；

 减少服务器负载 - 浏览器将只从服务器下载更新过或更改过的资源

### Web Worker 处理线程

作用：后台运行线程任务

优势：后台的 JavaScript，独立于其他脚本，不会影响页面的性能

* 使用：

   创建对象：var w = new Worker('w.js')

  监听消息：w.onmessage = function(e){}

  发送消息：w.postMessage(message)

  停止监听：w.terminate()

注意：

由于 web worker 位于外部文件中，它们无法访问下例 JavaScript 对象：

​	 window 对象

​	 document 对象

​	 parent 对象

### 通信 API

跨文档通信：

 消息监听：window.addEventListener('message', function(e){}, false);

 消息发送：window.postMessage(Object data, String targetUrl);

Web Socket（全双工）：

 var ws = new WebSocket('ws://localhost:8888/demo');

 ws.send('hello word');

 监听事件：onopen、onclose、onmessage、onerror

服务端发送事件（单向）：

 EventSource对象：onopen、onmessage、onerror

 Event对象：readyState、data

 服务端响应头设置：Content-Type:text/event-stream; Cache-Control:no-cache;输出的消息必需以 data: 开头

### 地理位置API

navigator.geolocation：

 void getCurrentPosition(onSuccess, onError, options)：获取当前地理位置信息

 int watchPosition(onSuccess, onError, options)：持续监视当前地理位置信息

 void clearWatch(int watchId)：停止监视

## 5.全局属性&URL

### 全局属性

| 属性                                                         | 描述                                                       |
| :----------------------------------------------------------- | :--------------------------------------------------------- |
| [accesskey](https://www.runoob.com/tags/att-global-accesskey.html) | 设置访问元素的键盘快捷键。                                 |
| [class](https://www.runoob.com/tags/att-global-class.html)   | 规定元素的类名（classname）                                |
| [contenteditable](https://www.runoob.com/tags/att-global-contenteditable.html)**New** | 规定是否可编辑元素的内容。                                 |
| [contextmenu](https://www.runoob.com/tags/att-global-contextmenu.html)**New** | 指定一个元素的上下文菜单。当用户右击该元素，出现上下文菜单 |
| [data-*](https://www.runoob.com/tags/att-global-data.html)**New** | 用于存储页面的自定义数据                                   |
| [dir](https://www.runoob.com/tags/att-global-dir.html)       | 设置元素中内容的文本方向。                                 |
| [draggable](https://www.runoob.com/tags/att-global-draggable.html)**New** | 指定某个元素是否可以拖动                                   |
| [dropzone](https://www.runoob.com/tags/att-global-dropzone.html)**New** | 指定是否将数据复制，移动，或链接，或删除                   |
| [hidden](https://www.runoob.com/tags/att-global-hidden.html)**New** | hidden 属性规定对元素进行隐藏。                            |
| [id](https://www.runoob.com/tags/att-global-id.html)         | 规定元素的唯一 id                                          |
| [lang](https://www.runoob.com/tags/att-global-lang.html)     | 设置元素中内容的语言代码。                                 |
| [spellcheck](https://www.runoob.com/tags/att-global-spellcheck.html)**New** | 检测元素是否拼写错误                                       |
| [style](https://www.runoob.com/tags/att-global-style.html)   | 规定元素的行内样式（inline style）                         |
| [tabindex](https://www.runoob.com/tags/att-global-tabindex.html) | 设置元素的 Tab 键控制次序。                                |
| [title](https://www.runoob.com/tags/att-global-title.html)   | 规定元素的额外信息（可在工具提示中显示）                   |
| [translate](https://www.runoob.com/tags/att-global-translate.html)**New** | 指定是否一个元素的值在页面载入时是否需要翻译               |

### URL

#### 定义

URL - 统一资源定位器（Uniform Resource Locator）

Web 浏览器使用 URL 从 Web 服务器请求页面

URL 是网页的地址，比如：https://www.w3school.com.cn

URL可以由字母组成，如"runoob.com"，或互联网协议（IP）地址： 192.68.20.50。大多数人进入网站使用网站域名来访问，因为 名字比数字更容易记住。

#### URL 编码

URL 编码将字符转换为可通过因特网传输的格式

URL 只能使用 ASCII 字符集 通过因特网进行发送

由于 URL 通常包含 ASCII 集之外的字符，因此必须将 URL 转换为有效的 ASCII 格式

URL 编码使用后跟十六进制数字的 "%" 替代不安全的 ASCII 字符

URL 不能包含空格。URL 编码通常使用加号（+）或 %20 替代空格

#### URL 编码/解码函数

encodeURI 和 decodeURI 函数操作的是完整的 URL；这俩函数假定 URL 中的任何保留字符都有特殊意义，所有不会编码它们

encodeURIComponent 和 decodeURIComponent 函数操作的是URL的参数；这俩函数假定任何保留字符都代表普通文本，所以必须编码它们，所以它们（保留字符）出现在一个完整 URL 的参数里面时不会被解释成保留字符了

encodeURI方法**不会**对下列字符编码 **ASCII****字母 数字** **~!@#$&\*()=:/,;?+‘**

encodeURIComponent方法**不会**对下列字符编码 **ASCII****字母 数字** **~!\*()'**

#### URL结构

`scheme://host.domain:port/path/filename`

说明:

- - scheme - 定义因特网服务的类型。最常见的类型是 http
  - host - 定义域主机（http 的默认主机是 www）
  - domain - 定义因特网域名，比如 runoob.com
  - :port - 定义主机上的端口号（http 的默认端口号是 80）
  - path - 定义服务器上的路径（如果省略，则文档必须位于网站的根目录中）。
  - filename - 定义文档/资源的名称

## 6.HTML事件

[事件详见](https://www.runoob.com/tags/ref-eventattributes.html)

使 HTML 事件触发浏览器中的行为
