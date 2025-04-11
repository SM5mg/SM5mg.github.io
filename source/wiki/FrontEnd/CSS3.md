---
layout: wiki #layout 的值固定为wiki，与第二项一同作用于侧边栏，如果没有它们侧边栏也会消失
wiki: FrontEnd # wiki 的值写你在source/_data/projects.yml中新增的项目名
title: CSS3 # 文章标题cSS 的全称为：层叠样式表 ( Cascading Style Sheets ) 。

---

## 一、CSS3 简介

### 1.CSS3 概述

- CSS3 是CSS2 的升级版本，它在CSS2 的基础上，新增了很多强大的新功能，从而解决一些实际

- 面临的问题。

- CSS3 在未来会按照模块化的方式去发展： https://www.w3.org/Style/CSS/current-work.html

- CSS3 的新特性如下：

  - 新增了更加实用的选择器，例如：动态伪类选择器、目标伪类选择器、伪元素选择器等等。

  - 新增了更好的视觉效果，例如：圆角、阴影、渐变等。

  - 新增了丰富的背景效果，例如：支持多个背景图片，同时新增了若干个背景相关的属性。

  - 新增了全新的布局方案 —— 弹性盒子。

  - 新增了Web 字体，可以显示用户电脑上没有安装的字体。

  - 增强了颜色，例如： HSL 、HSLA 、RGBA 几种新的颜色模式，新增 opacity 属性来控制透明度。

  - 增加了2D 和3D 变换，例如：旋转、扭曲、缩放、位移等。

  - 增加动画与过渡效果，让效果的变换更具流线性、平滑性。

### 2.CSS3私有前缀

#### 2.1 什么是私有前缀

如下代码中的-webkit- 就是私有前缀

```
div {
  width:400px;
  height:400px;
  -webkit-border-radius: 20px;
}
```

#### 2.2 为什么要有私有前缀

W3C 标准所提出的某个CSS 特性，在被浏览器正式支持之前，浏览器厂商会根据浏览器的内核，
使用私有前缀来测试该CSS 特性，在浏览器正式支持该CSS 特性后，就不需要私有前缀了。
举个例子：

```
-webkit-border-radius: 20px;
-moz-border-radius: 20px;
-ms-border-radius: 20px;
-o-border-radius: 20px;
border-radius: 20px;
```

**查询CSS3 兼容性的网站： https://caniuse.com/**

#### 2.3 常见浏览器私有前缀

- Chrome 浏览器： -webkit-
- Safari 浏览器： -webkit-
- Firefox 浏览器： -moz-
- Edge 浏览器： -webkit-
- 旧 Opera 浏览器： -o-
- 旧 IE 浏览器： -ms-

> **注意：**
> 我们在编码时，不用过于关注浏览器私有前缀，不用绞尽脑汁的去记忆，也不用每个都去查询，因
> 为常用的CSS3 新特性，主流浏览器都是支持的，即便是为了老浏览器而加前缀，我们也可以借助
> 现代的构建工具，去帮我们添加私有前缀。

## 二、CSS3 基本语法

### 1.CSS3 新增长度单位

1. rem **根元素字体大小的倍数**，只与根元素字体大小有关。
2. vw 视口宽度的百分之多少 10vw 就是**视口宽度的10%** 。
3. vh 视口高度的百分之多少 10vh 就是视口高度的10% 。
4. vmax 视口**宽高中大的那个**的百分之多少。（了解即可）
5. vmin 视口**宽高中小的那个**的百分之多少。（了解即可）

### 2.CSS3 新增颜色设置方式

CSS3 新增了三种颜色设置方式，分别是： rgba 、hsl 、hsla ，由于之前已经详细讲解，此处略过。

### 3.CSS3 新增选择器

CSS3 新增的选择器有：动态伪类、目标伪类、语言伪类、UI 伪类、结构伪类、否定伪类、伪元素；**这些在CSS2 中已经详细讲解**，此处略过。

### 4.CSS3 新增盒模型相关属性

#### 4.1. box-sizing 怪异盒模型

**使用box-sizing 属性可以设置盒模型的两种类型**：向内，不改变盒子总大小

{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240131160809.png %}

#### 4.2. resize 调整盒子大小

使用resize 属性可以控制是否允许用户调节元素尺寸。（需添加overflow:hidden,auto等属性)

{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240131160931.png %}

#### 4.3. box-shadow 盒子阴影

使用 box-shadow 属性为盒子添加阴影。
语法：

```
box-shadow: h-shadow v-shadow blur spread color inset;
```

各个值的含义：

{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240131161000.png %}

默认值： box-shadow:none 表示没有阴影
示例：

```
/* 写两个值，含义：水平位置、垂直位置 */
box-shadow: 10px 10px;

/* 写三个值，含义：水平位置、垂直位置、颜色 */
box-shadow: 10px 10px red;

/* 写三个值，含义：水平位置、垂直位置、模糊值 */
box-shadow: 10px 10px 10px;

/* 写四个值，含义：水平位置、垂直位置、模糊值、颜色 */
box-shadow: 10px 10px 10px red;

/* 写五个值，含义：水平位置、垂直位置、模糊值、外延值、颜色 */
box-shadow: 10px 10px 10px 10px blue;

/* 写六个值，含义：水平位置、垂直位置、模糊值、外延值、颜色、内阴影 */
box-shadow: 10px 10px 20px 3px blue inset;
```

#### 4.4. opacity 不透明度

opacity 属性能为整个元素添加透明效果， 值是 0 到 1 之间的小数， 0 是完全透明， 1 表示完
全不透明。

> **opacity 与 rgba 的区别？**
> opacity 是一个属性，设置的是整个元素（包括元素里的内容）的不透明度。
> rgba 是颜色的设置方式，用于设置颜色，它的透明度，仅仅是调整颜色的透明度。



### 5.CSS3 新增背景属性

#### 5.1. background-origin

作用：设置背景图的原点。
语法

- padding-box ：从padding 区域开始显示背景图像。—— 默认值
- border-box ： 从border 区域开始显示背景图像。
- content-box ： 从content 区域开始显示背景图像。

#### 5.2. background-clip

作用：设置背景图的向外裁剪的区域。
语法

- border-box ： 从border 区域开始向外裁剪背景。 —— 默认值
- padding-box ： 从padding 区域开始向外裁剪背景。
- content-box ： 从content 区域开始向外裁剪背景。
- text ：背景图只呈现在文字上。
  注意：若值为text ，那么backgroun-clip 要加上-webkit- 前缀。

#### 5.3. background-size

作用：设置背景图的尺寸。
语法：

1. 用长度值指定背景图片大小，不允许负值。`background-size: 300px 200px;`
2. 用百分比指定背景图片大小，不允许负值。`background-size: 100% 100%;`
3. auto ： 背景图片的真实大小。 —— 默认值
4. contain ： 将背景图片等比缩放，使背景图片的宽或高，与容器的宽或高相等，再将完整
背景图片包含在容器内，但要注意：可能会造成容器里部分区域没有背景图片。`background-size: contain;`
5. cover ：将背景图片等比缩放，直到完全覆盖容器，图片会尽可能全的显示在元素上，但要
注意：背景图片有可能显示不完整。—— 相对比较好的选择`background-size: cover;`

#### 5.4. backgorund 复合属性

语法：`background: color url repeat position / size origin clip`

> 注意：
> 1. origin 和 clip 的值如果一样，如果只写一个值，则origin 和 clip 都设置；如果设置了两个值，前面的是origin ，后面的clip 。
> 2. size 的值必须写在 position 值的后面，并且用 / 分开。

#### 5.5. 多背景图

CSS3 允许元素设置多个背景图片

```
/* 添加多个背景图 */
background: url(../images/bg-lt.png) no-repeat,
            url(../images/bg-rt.png) no-repeat right top,
            url(../images/bg-lb.png) no-repeat left bottom,
            url(../images/bg-rb.png) no-repeat right bottom;
```

### 6. CSS3新增边框属性

#### 6.1 边框圆角

在 CSS3 中，使用border-radius 属性可以将盒子变为圆角。
同时设置四个角的圆角：`border-radius:10px;`

{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240131161903.png %}

#### 6.2 边框外轮廓（了解）

- outline-width ：外轮廓的宽度。

- outline-color ：外轮廓的颜色。

- outline-style ：外轮廓的风格。

  - none ： 无轮廓
  - dotted ： 点状轮廓
  - dashed ： 虚线轮廓
  - solid ： 实线轮廓
  - double ： 双线轮廓

- outline-offset 设置外轮廓与边框的距离，正负值都可以设置。

  注意： outline-offset 不是outline 的子属性，是一个独立的属性。

**outline 复合属性**`outline:50px solid blue;`

### 7. CSS3新增文本属性

#### 7.1 文本阴影

在 CSS3 中，我们可以使用 text-shadow 属性给文本添加阴影。
语法：`text-shadow: h-shadow v-shadow blur color;`

{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240201115217.png %}

#### 7.2 文本换行

在 CSS3 中，我们可以使用 white-space 属性设置文本换行方式。
常用值如下：

{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240201115328.png %}

#### 7.3 文本溢出

在 CSS3 中，我们可以使用 text-overflow 属性设置文本内容溢出时的呈现模式。
常用值如下：

{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240201115423.png %}

#### 7.4 文本修饰

CSS3 升级了text-decoration 属性，让其变成了复合属性。

```
text-decoration: text-decoration-line || text-decoration-style || text-decorationcolor
```

子属性及其含义：

- text-decoration-line 设置文本装饰线的位置
  - none ： 指定文字无装饰 （默认值）
  - underline ： 指定文字的装饰是下划线
  - overline ： 指定文字的装饰是上划线
  - line-through ： 指定文字的装饰是贯穿线
- text-decoration-style 文本装饰线条的形状
  - solid ： 实线 （默认）
  - double ： 双线
  - dotted ： 点状线条
  - dashed ： 虚线
  - wavy ： 波浪线
- text-decoration-color 文本装饰线条的颜色

#### 7.5 文本描边

注意：文字描边功能仅 webkit 内核浏览器支持。

- -webkit-text-stroke-width ：设置文字描边的宽度，写长度值。
- -webkit-text-stroke-color ：设置文字描边的颜色，写颜色值。
- -webkit-text-stroke ：复合属性，设置文字描边宽度和颜色。

### 8. CSS3 新增渐变

#### 8.1 线性渐变

**多个颜色之间的渐变， 默认从上到下渐变。**

``` 
background-image: linear-gradient(red,yellow,green);
```

**使用关键词设置线性渐变的方向。**

```
background-image: linear-gradient(to top,red,yellow,green);
background-image: linear-gradient(to right top,red,yellow,green);
```

**使用角度设置线性渐变的方向。**

```
background-image: linear-gradient(30deg,red,yellow,green);
```

**调整开始渐变的位置。**

```
background-image: linear-gradient(red 50px,yellow 100px ,green 150px);
```

#### 8.2 径向渐变

多个颜色之间的渐变， 默认从圆心四散。（注意：不一定是正圆，要看容器本身宽高比）

```
background-image: radial-gradient(red,yellow,green);
```

使用关键词调整渐变圆的圆心位置。

```
background-image: radial-gradient(at right top,red,yellow,green);
```

使用像素值调整渐变圆的圆心位置。

```
background-image: radial-gradient(at 100px 50px,red,yellow,green);
```

调整渐变形状为正圆 。

```
background-image: radial-gradient(circle,red,yellow,green);
```

调整形状的半径 。

```
background-image: radial-gradient(100px,red,yellow,green);
background-image: radial-gradient(50px 100px,red,yellow,green);
```

调整开始渐变的位置。

```
background-image: radial-gradient(red 50px,yellow 100px,green 150px);
```

#### 8.3 重复渐变

无论线性渐变，还是径向渐变，在没有发生渐变的位置，继续进行渐变，就为重复渐变。

- 使用repeating-linear-gradient 进行重复线性渐变，具体参数同linear-gradient 。
- 使用repeating-radial-gradient 进行重复径向渐变，具体参数同radial-gradient 。

> 我们可以利用渐变，做出很多有意思的效果：例如：横格纸、立体球等等。

### 9. 伸缩盒模型

#### 1.伸缩盒模型简介

- 2009 年， W3C 提出了一种新的盒子模型 —— Flexible Box （伸缩盒模型，又称：弹性盒子）。
- 它可以轻松的控制：元素分布方式、元素对齐方式、元素视觉顺序 .......
- 截止目前，除了在部分IE 浏览器不支持，其他浏览器均已全部支持。
- 伸缩盒模型的出现，逐渐演变出了一套新的布局方案 —— flex 布局。

小贴士：

- 传统布局是指：基于传统盒状模型，主要靠： display 属性 + position 属性 + float
  属性。
- flex 布局目前在移动端应用比较广泛，因为传统布局不能很好的呈现在移动设备上。

#### 2.伸缩容器、伸缩项目

**伸缩容器： 开启了 flex 的元素，就是：伸缩容器。**

- 给元素设置： display:flex 或 display:inline-flex ，该元素就变为了伸缩容
  器。
- display:inline-flex 很少使用，因为可以给多个伸缩容器的父容器，也设置为伸缩
  容器。
- 一个元素可以同时是：伸缩容器、伸缩项目。

**伸缩项目：伸缩容器所有子元素自动成为了：伸缩项目。**

- 仅伸缩容器的子元素成为了伸缩项目，孙子元素、重孙子元素等后代，不是伸缩项
  目。
- 无论原来是哪种元素（块、行内块、行内），一旦成为了伸缩项目，全都会“块状化”。

#### 3.主轴与侧轴

- 主轴： 伸缩项目沿着主轴排列，主轴默认是水平的，默认方向是：从左到右（左边是起点，右边是终点）。
- 侧轴： 与主轴垂直的就是侧轴，侧轴默认是垂直的，默认方向是：从上到下（上边是起点，下边是终点）。

#### 4.主轴方向

属性名： flex-direction
常用值如下：

- row ：主轴方向水平从左到右 —— 默认值
- row-reverse ：主轴方向水平从右到左。
- column ：主轴方向垂直从上到下。
- column-reverse ：主轴方向垂直从下到上。

{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240201123834.png %}

**注意：改变了主轴的方向，侧轴方向也随之改变。**

#### 5.主轴换行方式

属性名： flex-wrap
常用值如下：

- nowrap ：默认值，不换行。

{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240201123942.png %}

- wrap ：自动换行，伸缩容器不够自动换行。

{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240201124009.png %}

- wrap-reverse ：反向换行。

{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240201124024.png %}

#### 6.flex-flow

flex-flow 是一个复合属性，复合了 flex-direction 和 flex-wrap 两个属性。 值没有顺序要求。`flex-flow: row wrap;`

#### 7.主轴对齐方式

属性名： justify-content
常用值如下：

- flex-start ：主轴起点对齐。—— 默认值
- flex-end ：主轴终点对齐。
- center ：居中对齐
- space-between ：均匀分布，两端对齐（最常用）。
- space-around ：均匀分布，两端距离是中间距离的一半。
- space-evenly ：均匀分布，两端距离与中间距离一致。

{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240201124132.png %}

#### 8.侧轴对齐方式

##### 8.1 一行的情况

所需属性： align-items
常用值如下：

- flex-start ：侧轴的起点对齐。
- flex-end ：侧轴的终点对齐。
- center ：侧轴的中点对齐。
- baseline : 伸缩项目的第一行文字的基线对齐。
- stretch ：如果伸缩项目未设置高度，将占满整个容器的高度。—— （默认值）

{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240201124239.png %}

##### 8.2 多行的情况

所需属性： align-content
常用值如下：

1. flex-start ：与侧轴的起点对齐。
2. flex-end ：与侧轴的终点对齐。
3. center ：与侧轴的中点对齐。
4. space-between ：与侧轴两端对齐，中间平均分布。
5. space-around ：伸缩项目间的距离相等，比距边缘大一倍。
6. space-evenly : 在侧轴上完全平分。
7. stretch ：占满整个侧轴。—— 默认值

{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240201124345.png %}

#### 9.flex 实现水平垂直居中

方法一：父容器开启flex 布局，随后使用justify-content 和align-items 实现水平垂直居中

```
.outer {
  width: 400px;
  height: 400px;
  background-color: #888;
  display: flex;
  justify-content: center;
  align-items: center;
}
.inner {
  width: 100px;
  height: 100px;
  background-color: orange;
}
```

方法二：父容器开启flex 布局，随后子元素margin: auto

```
.outer {
  width: 400px;
  height: 400px;
  background-color: #888;
  display: flex;
}
.inner {
  width: 100px;
  height: 100px;
  background-color: orange;
  margin: auto;
}
```

#### 10.伸缩性

1. flex-basis
   概念： flex-basis 设置的是主轴方向的基准长度，会让宽度或高度失效。
   备注：主轴横向：宽度失效；主轴纵向：高度失效
   作用：浏览器根据这个属性设置的值，计算主轴上是否有多余空间，默认值auto ，即：伸缩项目
   的宽或高。

2. flex-grow（伸）
   概念： flex-grow 定义伸缩项目的放大比例，默认为0 ，即：纵使主轴存在剩余空间，也不拉伸
   （放大）。
   规则：

- 若所有伸缩项目的 flex-grow 值都为1 ，则：它们将等分剩余空间（如果有空间的话）。
- 若三个伸缩项目的flex-grow 值分别为： 1 、2 、3 ，则：分别瓜分到： 1/6 、2/6 、
  3/6 的空间。

3. flex-shrink（缩）
   概念： flex-shrink 定义了项目的压缩比例，默认为1 ，即：如果空间不足，该项目将会缩小。
   收缩项目的计算，略微复杂一点，我们拿一个场景举例：

> 例如：
> 三个收缩项目，宽度分别为： 200px 、300px 、200px ，它们的flex-shrink 值分别
> 为： 1 、2 、3
> 若想刚好容纳下三个项目，需要总宽度为700px ，但目前容器只有400px ，还差300px
> 所以每个人都要收缩一下才可以放下，具体收缩的值，这样计算：
> 1. 计算分母： (200×1) + (300×2) + (200×3) = 1400
>
> 2. 计算比例：
>     项目一： (200×1) / 1400 = 比例值1
>     项目二： (300×2) / 1400 = 比例值2
>
>   项目三： (200×3) / 1400 = 比例值3
>
> 3. 计算最终收缩大小：
>     项目一需要收缩： 比例值1 × 300
>     项目二需要收缩： 比例值2 × 300
>     项目三需要收缩： 比例值3 × 300

#### 11.flex复合属性

flex 是复合属性，复合了： flex-grow 、 flex-shrink 、flex-basis 三个属性，默认值为 0 1
auto 。

- 如果写 flex:1 1 auto ，则可简写为： flex:auto
- 如果写 flex:1 1 0 ，则可简写为： flex:1
- 如果写 flex:0 0 auto ，则可简写为： flex:none
- 如果写 flex:0 1 auto ，则可简写为： flex:0 auto —— 即 flex 初始值。

#### 12.项目排序

order 属性定义项目的排列顺序。数值越小，排列越靠前，默认为0 。

#### 13.单独对齐

通过align-self 属性，可以单独调整某个伸缩项目的对齐方式
默认值为 auto ，表示继承父元素的 align-items 属性

### 10.BFC

#### 1.什么是BFC

W3C 上对 BFC 的定义：

> 原文：Floats, absolutely positioned elements, block containers (such as inline-blocks, tablecells,
> and table-captions) that are not block boxes, and block boxes with 'overflow' other than
> 'visible' (except when that value has been propagated to the viewport) establish new block
> formatting contexts for their contents.
> 译文：浮动、绝对定位元素、不是块盒子的块容器（如inline-blocks 、table-cells 和
> table-captions ），以及overflow 属性的值除visible 以外的块盒，将为其内容建立新
> 的块格式化上下文。

MDN 上对 BFC 的描述：

> 块格式化上下文（Block Formatting Context，BFC） 是Web 页面的可视CSS 渲染的一部分，
> 是块盒子的布局过程发生的区域，也是浮动元素与其他元素交互的区域。

更加通俗的描述：

1. BFC 是 Block Formatting Context （块级格式上下文），可以理解成元素的一个“特异功能”。
2. 该 “特异功能”，在默认的情况下处于关闭状态；当元素满足了某些条件后，该“特异功能”被激活。
3. 所谓激活“特异功能”，专业点说就是：该元素创建了 BFC （又称：开启了 BFC ）。



#### 2.开启了BFC能解决什么问题

- 元素开启BFC 后，其子元素不会再产生margin 塌陷问题。
- 元素开启BFC 后，自己不会被其他浮动元素所覆盖。
- 元素开启BFC 后，就算其子元素浮动，元素自身高度也不会塌陷。

#### 3.如何开启BFC

- 根元素
- 浮动元素
- 绝对定位、固定定位的元素
- 行内块元素
- 表格单元格： table 、thead 、tbody 、tfoot 、th 、td 、tr 、caption
- overflow 的值不为 visible 的块元素
- 伸缩项目
- 多列容器
- column-span 为 all 的元素（即使该元素没有包裹在多列容器中）
- display 的值，设置为flow-root




### 接下来的学习路径

{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240201165249.png %}