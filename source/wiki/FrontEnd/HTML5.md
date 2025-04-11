---
layout: wiki #layout 的值固定为wiki，与第二项一同作用于侧边栏，如果没有它们侧边栏也会消失
wiki: FrontEnd # wiki 的值写你在source/_data/projects.yml中新增的项目名
title: HTML5  # 文章标题
# breadcrumb: false
---

## 一、HTML5简介

### 什么是HTML5

HTML5 是新一代的 HTML 标准，2014年10月由万维网联盟（ W3C ）完成标准制定。

**官网地址：**

- W3C 提供： https://www.w3.org/TR/html/index.html
- WHTWG 提供： https://whatwg-cn.github.io/html/multipage

HTML5 在狭义上是指新一代的 HTML 标准，在广义上是指：整个前端。

### HTML5 优势

1. 针对JavaScript ，新增了很多可操作的接口。
2. 新增了一些语义化标签、全局属性。
3. 新增了多媒体标签，可以很好的替代flash 。
4. 更加侧重语义化，对于SEO 更友好。
5. 可移植性好，可以大量应用在移动设备上。

### HTML5兼容性

支持： Chrome 、Safari 、Opera 、Firefox 等主流浏览器。
IE 浏览器必须是9 及以上版本才支持HTML5 ，且IE9 仅支持部分HTML5 新特性。

## 二、新增语义化标签

### 1.  新增布局标签

{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240118153114.png %}

**关于article 和section ：**

> 1. artical 里面可以有多个section 。
> 2. section 强调的是分段或分块，如果你想将一块内容分成几段的时候，可使用section 元素。
> 3. article 比section 更强调独立性，一块内容如果比较独立、比较完整，应该使用article 元素。

### 2. 新增状态标签

#### 2.1 meter 标签

语义：定义已知范围内的标量测量。也被称为 gauge （尺度），双标签，例如：电量、磁盘用量
等。

常用属性如下：

{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240131154217.png %}

#### 2.2 progress 标签

语义：显示某个任务完成的进度的指示器，一般用于表示进度条，双标签，例如：工作完成进度
等。
属性值描述：

{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240131154604.png %}

### 3. 新增列表标签

{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240131154730.png %}



### 4. 新增文本标签

#### 4.1 文本注音

{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240131155037.png %}

#### 4.2 文本标记

{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240131155103.png %}

## 三、新增表单功能

### 1. 表单控件新增属性

{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240131155208.png %}

### 2. input 新增属性值

{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240131155242.png %}

### 3. form 标签新增属性

{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240131155311.png %}

## 四、新增多媒体标签

### 1. 视频标签

`<video> `标签用来定义视频，它是双标签。

{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240131155405.png %}

### 2. 音频标签

`<audio> `标签用来定义音频，它是双标签。

{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240131155443.png %}

## 五、新增全局属性（了解）

{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240131155520.png %}

## 六、HTML5兼容性处理

**添加元信息，让浏览器处于最优渲染模式。**

```
<!--设置IE总是使用最新的文档模式进行渲染-->
<meta http-equiv="X-UA-Compatible" content="IE=Edge">

<!--优先使用 webkit ( Chromium ) 内核进行渲染, 针对360等壳浏览器-->
<meta name="renderer" content="webkit">
```

**使用html5shiv 让低版本浏览器认识H5 的语义化标签。**

```
<!--[if lt ie 9]>
<script src="../sources/js/html5shiv.js"></script>
<![endif]-->
```

**扩展**

```
lt 小于
lte 小于等于
gt 大于
gte 大于等于
! 逻辑非
```

**示例：**

```
<!--[if IE 8]>仅IE8可见<![endif]-->
<!--[if gt IE 8]>仅IE8以上可见<![endif]—>
<!--[if lt IE 8]>仅IE8以下可见<![endif]—>
<!--[if gte IE 8]>IE8及以上可见<![endif]—>
<!--[if lte IE 8]>IE8及以下可见<![endif]—>
<!--[if !IE 8]>非IE8的IE可见<![endif]-->
```

