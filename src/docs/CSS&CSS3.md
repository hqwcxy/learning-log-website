---
title: "CSS"
date: "2017-08-10"
---

# CSS

## 1.css简介

CSS 指层叠样式表 (Cascading Style Sheets)

它可以

- 定义如何**显示** HTML 元素
- 解决内容与表现**分离**的问题
- 极大提高工作效率
- 将多重样式将层叠为一个

一般而言，所有的样式会根据下面的规则层叠于一个新的虚拟样式表中，其中数字 4 拥有最高的优先权。

1. 浏览器缺省设置
2. 外部样式表`<link rel="stylesheet" type="text/css" href="sheet1.css" media="all" />`
3. 内部样式表/嵌入式（位于 `<head>` 标签内部）``
4. 内联样式（在 HTML 元素内部）`<p style="color:red">这里文字是红色。</p>`

即

**内联式>嵌入式>外部式>浏览器缺省设置**

## 2.CSS属性

### 1.css文本属性

[文本属性](https://www.runoob.com/css/css-text.html)

### 2.背景属性

[背景属性](https://www.runoob.com/css/css-background.html)

### 3.列表属性

[列表属性](https://www.runoob.com/css/css-list.html)

### 4.显示属性

[显示属性](https://www.runoob.com/css/css-display-visibility.html)

### 5.盒模型

[盒模型](https://www.runoob.com/css/css-boxmodel.html)

### 6.浮动属性

[浮动属性](https://www.runoob.com/css/css-float.html)

### 7.定位属性

[定位属性](https://www.runoob.com/css/css-positioning.html)

## 3.选择器（重点）

### 1.基础选择器

| 选择器                 | 例子           | 含义                                           |
| ---------------------- | -------------- | ---------------------------------------------- |
| **通配符选择器** *     | *              | 匹配所有元素。（匹配范围太广，很少用到）       |
| **id选择器** #id       | #element-id    | 匹配id为`element-id`元素                       |
| **class选择器** .class | .element-class | 匹配class**包含**(不是等于)`element-class`元素 |
| **标签选择器** element | p              | ****匹配标签类型为`p`的所有元素                |

### 2.组合选择器

| 选择器                                    | 例子           | 含义                                                         |
| :---------------------------------------- | -------------- | ------------------------------------------------------------ |
| 多元素选择器               E,F            | div,p          | 同时匹配元素E或元素F，例子中的含义为匹配所有的`<div>`和`<p>` |
| 后代选择器            E F                 | div p          | 用**空格**分隔，匹配E元素所有的**后代**（不只是子元素、子元素向下递归）符合 F 的元素，例子中的含义为匹配所有的在`<div>`下的`<p>` |
| 直接子元素选择器                      E>F | div>p          | 用`>`分隔，匹配E元素的所有**直接子元素**，例子中的含义为匹配所有`<div>`的直接子元素且是`<p>` |
| 毗邻选择器       E+F                      | div+p          | 匹配E元素之后的**相邻**的同级元素F，例子中的含义为匹配**紧接**在 `<div>` 之后的所有 `<p>` 元素 |
| 兄弟选择器        E~F                     | div~p          | 匹配E元素之后的同级元素F（无论直接相邻与否），例子中的含义为匹配紧`<div>` 之后的所有 `<p>` 元素 |
| 同时满足选择器 EF                         | .class1.class2 | EF 连写，匹配同时满足 E 和 F 的元素，例子中的含义为匹配 `class` 中同时有 `class1` 和 `class2` 的元素 |

### 3.属性选择器

| 选择器          | 例子            | 含义                                                         |
| --------------- | --------------- | ------------------------------------------------------------ |
| [attr]          | input[disabled] | 匹配所有具有属性attr的元素，例子中的含义为选择所有有`disabled`属性的`<input>` |
| [attr = value]  | [id=did]        | 匹配属性attr值为value的元素，例子等价于`#did`                |
| [attr ~= value] | [class~=dclass] | 匹配所有属性attr具有多个空格分隔、其中一个值等于value的元素，例子等价于`.dclass` |
| [attr ^= value] | div[class^=d]   | 匹配属性attr的值以value**开头**的元素，例子可以匹配`<div class="dclass">` |
| [attr $= value] | div[class$=d]   | 匹配属性attr的值以value**结尾**的元素，例子可以匹配`<div class="classd">` |
| [attr *= value] | div[class*=d]   | 匹配属性attr的值**包含**value的元素，例子可以匹配`<div class="somedsome">` |

### 4.伪类选择器

| 选择器                | 含义                                                         |
| --------------------- | ------------------------------------------------------------ |
| E:first-child         | 匹配元素E的第一个子元素                                      |
| E:link                | 匹配所有未被点击的链接                                       |
| E:visited             | 匹配所有已被点击的链接                                       |
| E:active              | 匹配鼠标已经其上按下、还没有释放的E元素                      |
| E:hover               | 匹配鼠标悬停其上的E元素                                      |
| E:focus               | 匹配获得当前焦点的E元素                                      |
| E:enabled             | 匹配表单中可用的元素                                         |
| E:disabled            | 匹配表单中禁用的元素                                         |
| E:checked             | 匹配表单中被选中的radio或checkbox元素                        |
| E:nth-child(n)        | 匹配其父元素的第n个子元素，第一个编号为1                     |
| E:nth-last-child(n)   | 匹配其父元素的倒数第n个子元素，第一个编号为1                 |
| E:nth-of-type(n)      | 与:nth-child()作用类似，但是仅匹配使用同种标签的元素         |
| E:nth-last-of-type(n) | 与:nth-last-child() 作用类似，但是仅匹配使用同种标签的元素   |
| E:last-child          | 匹配父元素的最后一个子元素，等同于:nth-last-child(1)         |
| E:first-of-type       | 匹配父元素下使用同种标签的第一个子元素，等同于:nth-of-type(1) |
| E:last-of-type        | 匹配父元素下使用同种标签的最后一个子元素，等同于:nth-last-of-type(1) |
| E:only-child          | 匹配父元素下仅有的一个子元素，等同于:first-child:last-child或 :nth-child(1):nth-last-child(1) |
| E:only-of-type        | 匹配父元素下使用同种标签的唯一一个子元素，等同于:first-of-type:last-of-type或 :nth-of-type(1):nth-last-of-type(1) |
| E:empty               | 匹配一个不包含任何子元素的元素，文本节点也被看作子元素       |
| E:not(selector)       | 匹配不符合当前选择器的任何元素                               |

### 5.伪元素选择器

| 选择器         | 含义                      |
| -------------- | ------------------------- |
| E:first-line   | 匹配E元素内容的第一行     |
| E:first-letter | 匹配E元素内容的第一个字母 |
| E:before       | 在E元素之前插入生成的内容 |
| E:after        | 在E元素之后插入生成的内容 |

### 6.选择器优先级

css的继承：指应用在一个标签上的那些 CSS 属性被传到其子标签上

优先规则：



最近的祖先样式比其他祖先样式优先级高

"直接样式"比"祖先样式"优先级高

内联样式 > ID 选择器 > 类选择器 = 属性选择器 = 伪类选择器 > 标签选择器 = 伪元素选择器

权重：标签:1；class:10；id:100；style:1000；!important：有!important声明的规则高于一切



CSS 优先级**从高到低分别是**

1. 在属性后面使用 `!important` 会覆盖页面内任何位置定义的元素样式
2. 作为style属性写在元素标签上的**内联**样式
3. id选择器
4. 类选择器=伪类选择器=属性选择器
5. 标签选择器=伪元素选择器
6. 通配符选择器
7. 浏览器自定义

## 4.常用布局

### 1.布局基础

基于盒模型，依赖 display 属性 + position属性 + float属性实现的

### 2.浮动



### 3.清除浮动（重点）

#### 1.概念

容器的高度不能自动伸长以适应内容的高度，使得内容溢出到容器外面而影响（甚至破坏）布局的现象，这个现象叫浮 动溢出，

#### 2.方法

共有2个方向：一是利用 clear 属性，二是触 发浮动元素父元素的 BFC (Block Formatting Contexts, 块级格式化上下文)，使到该父元素可以包含浮动元素

具体方法：

* 使用带clear属性的空元素（优点：简单，代码少，浏览器兼容性好。缺点：需添加无语义的html元素，代码不够优 雅， 后期不容易维护）

* 使用CSS的overflow属性

* 给浮动的元素的容器添加浮动

* 使用邻接元素处理：给浮动元素后面的元素添加clear属性

* 使用CSS的:after伪元素

  ```js
  .clearfix::after{
      content:"";
      display:block;
      clear:both;
      height:0;
  }
  ```

  

### 4.弹性布局（重点）

[弹性布局](https://www.runoob.com/css3/css3-flexbox.html)

### 5.响应式布局

> 响应式布局：根据不同屏幕的分辨率来浏览网页的不同展示方式。
>
> 自适应：不同屏幕尺寸大小的多套代码。



## 5.函数&动画

### 1.css常用函数汇总

* 属性函数：attr()；

* 背景图片函数：linear-gradient()、radial-gradient()、conic-gradient()、repeating-linear-gradient()、repeating-radial-gradient()、repeating-conic-gradient()、image-set()、image()、url()、element()；

* 颜色函数：rgb()、rgba()、hsl()、hsla()、hwb()、color-mod()；

* 图形函数：circle()、ellipse()、inset()、polygon()、path()

* 滤镜函数：blur()、brightness()、contrast()、drop-shadow()、grayscale()、hue-rotate()、invert()、opacity()、saturate()、sepia()；

* 转换函数：matrix()、matrix3d()、perspective()、rotate()、rotate3d()、rotateX()、rotateY()、rotateZ()、scale()、scale3d()、scaleX()、scaleY()、scaleZ()、skew()、skewX()、skewY()、translate()、translateX()、translateY()、translateZ()、translate3d()；

* 数学函数：calc()、min()、max()、mixmax()、repeat()；

* 缓动函数：cubic-bezier()、steps()；

* 其他函数：counter()、counters()、toggle()、var()、 symbols()

注意：由于`<gradient>`数据类型系`<image>`的子数据类型，`<gradient>`只能被用于`<image>`可以使用的地方。因此，linear-gradient() 并不适用于background-color以及类似的使用 color数据类型的属性中

### 2.动画

#### 1.keyframes

`@keyframes animationname {keyframes-selector {css-styles;}}`

**animationname**，必需，定义动画的名称

 **keyframes-selector**，必需，动画时长的百分比，合法的值： 0-100% from（与 0% 相同） to（与 100% 相同

 **css-styles**，必需，一个或多个合法的 CSS 样式属性

#### 2.animation 属性

一个简写属性，用于设置六个动画属性 (animation: name duration timing-function delay iteration-count direction)

​	 **animation-name**，规定需要绑定到选择器的keyframes的animationname名称

​	 **animation-duration**，设置动画的持续时间，单位为s，默认值为0

​	 **animation-timing-function**，设置过渡效果的速率，它有6种形式的速率

 	**animation-delay**，设置动画的开始时间，单位是s或者ms，默认值为0

​	 **animation-iteration-count**，设置动画循环的次数，默认为1，infinite为无限次数的循环

​	 **animation-direction**，设置动画播放的方向，默认值为normal表示向前播放，alternate代表动画播放在第偶数次向 前播放，第奇数次向反方向播放

​	 **animation-play-state**，控制动画的播放状态：running代表播放，而paused代表停止播放，running为默认值

​	 **animation**，它是animation-name、animation-duration、animation-timing-function、animation-delay、 animation-iteration-count、animation-direction的简写

#### 3.transform(转换)

用来设置元素的形状改变，**不改变**元素原先在文档流中的位置，主要有以下几种变形：**rotate（旋转）**、scale（缩放）、skew（扭曲）、**translate（移动）**和matrix（矩阵变形）

**transform-origin** **基点，**所有的变形都是基于基点，基点默认为元素的中心点

**1.translate**

translate()方法，根据左(X轴)和顶部(Y轴)位置给定的参数，从当前元素位置移动。

如下代码可以将一个 `div` 向右平移 `50px`，向下平移 `100px`

```css
div {
  transform: translate(50px,100px)
}
```

**2.rotate**

rotate()方法，在一个给定度数顺时针旋转的元素。负值是允许的，这样是元素逆时针旋转。

如下代码可以将一个 `div` 旋转30度

```css
div {
  transform: rotate(30deg);
}
```

**3.scale**

scale()方法，该元素增加或减少的大小，取决于宽度（X轴）和高度（Y轴）的参数；

如下代码可以将一个 `div` 水平拉升到原来的 2 倍，垂直拉升到原来的 3 倍

```css
div {
  transform:scale(2,3)
}
```

#### 4.transition（渐变）

用来设置样式的属性值是如何从从一种状态变平滑过渡到另外一种状态，它有四个属性

 **transition-property**（变换的属性，即那种形式的变换：大小、位置、扭曲等）

 **transition-duration**（变换延续的时间）

 **transition-timing-function**（变换的速率）

 **transition-delay**（变换的延时）

 **transition**：它是transition-property、transition-duration、transition-timing-function、transition-delay的简写

| 属性                       | 描述                                         |
| :------------------------- | :------------------------------------------- |
| transition                 | 简写属性，用于在一个属性中设置四个过渡属性。 |
| transition-property        | 规定应用过渡的 CSS 属性的名称。              |
| transition-duration        | 定义过渡效果花费的时间。默认是 0。           |
| transition-timing-function | 规定过渡效果的时间曲线。默认是 "ease"。      |
| transition-delay           | 规定过渡效果何时开始。默认是 0。             |

其中，`transition-timing-function` 可选值如下：

| 值                    | 描述                                                         |
| :-------------------- | :----------------------------------------------------------- |
| linear                | 规定以相同速度开始至结束的过渡效果（等于 cubic-bezier(0,0,1,1)）。 |
| ease                  | 规定慢速开始，然后变快，然后慢速结束的过渡效果（cubic-bezier(0.25,0.1,0.25,1)）。 |
| ease-in               | 规定以慢速开始的过渡效果（等于 cubic-bezier(0.42,0,1,1)）。  |
| ease-out              | 规定以慢速结束的过渡效果（等于 cubic-bezier(0,0,0.58,1)）。  |
| ease-in-out           | 规定以慢速开始和结束的过渡效果（等于 cubic-bezier(0.42,0,0.58,1)）。 |
| cubic-bezier(n,n,n,n) | 在 cubic-bezier 函数中定义自己的值。可能的值是 0 至 1 之间的数值。 |

## 6.预处理&工程化（重要）

CSS预处理器提供CSS缺失的样式层复用机制，减少冗余代码，提高样式代码的可维护性

文件切分：把一个大的 CSS 文件在切分成多个小文件，实现初步模块化

### 1.less

less是一门向后兼容的 CSS 扩展语言，包含了 Less 语言以及利用 JavaScript 开发的用于将 Less 样式转换成 CSS 样式的 Less.js 工具

**变量：**@变量名: 值;

 作为css属性值：width: @len;

 作为属性名：@{bg}: @basecolor;

 作为选择器：#@{activeclass} {}

**变量作用域：**第一步： 使用变量，在本作用域里找, 找到了， 使用最后面的定义；第二步： 本作用域找不到，去上级作用域找

**导入：**导入混合 如果导入的是less文件，可以省略 后缀，@import "mixins/mixins"; @import "variables"; @import "base"; @import "style.css";

运算：两个不同单位参与运算以第一个为准，颜色可以参与运算

### 2.BEM 命名规范

块（block）、元素（element）、修饰符（modifier）

* 块即是通常所说的 Web 应用开发中的组件或模块。每个块在逻辑上和功能上都是相互独立的，.block { }

* 元素是块中的组成部分。元素不能离开块来使用。BEM 不推荐在元素中嵌套其他元素，.block__element { }

* 修饰符用来定义块或元素的外观和行为。同样的块在应用不同的修饰符之后，会有不同的外观，.block--modifier { }

### 3.CSS Modules 

代码中的每一个类名都是引入对象的一个属性, 编译时会将 css 类名 加上唯一 hash，解决css命名冲突问题

* css module 作用域：作用域默认为 local 即只在当前模块生效

* global 被 :global 包裹起来的类名，不会被模块化

使用方式如下：

1. 定义 css 文件： style.css

2. 在 js 模块中导入 css 文件：import styles from "./style.css"; 

3.  配置 css-loader 打包：CSS Modules 不能直接使用，而是需要进行打包，一般通过配置 css-loader 中的 modules 属性即可完成  css modules 的配置

 最终打包出来的 css 类名就是由一长串 hash 值生成

### 4.CSS In JS

所有的 css 代码全部放在组件内部，以实现 css 的模块化

```css
import React from "react";
import styled from "styled-components"; 
// 创建一个带样式的 h1 标签
const Title = styled.h1`font-size:1.5em;text-align:center;color:palevioletred;`;
```

![image-20210706125913798](C:\Users\CDLX\AppData\Roaming\Typora\typora-user-images\image-20210706125913798.png)

