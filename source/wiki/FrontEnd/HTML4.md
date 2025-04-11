---
layout: wiki #layout 的值固定为wiki，与第二项一同作用于侧边栏，如果没有它们侧边栏也会消失
wiki: FrontEnd # wiki 的值写你在source/_data/projects.yml中新增的项目名
title: HTML4 # 文章标题
# breadcrumb: false
---

## HTML 简介

### 开发者文档

**W3C 官网**： [www.w3c.org](www.w3c.org)
**W3School**： [www.w3school.com.cn](www.w3school.com.cn)
**MDN**： [developer.mozilla.org](developer.mozilla.org) —— 平时用的最多。

### 什么是 HTML

全称：HyperText Markup Language（超文本标记语言）。
**超文本**：是一种组织信息的方式，通过超链接将不同空间的文字，图片等各种信息组合到一起。
**标记**：文本要变成超文本，就需要用到各种特定的标记符号。
**语言**：每一个标记的写法、使用规则，组成了一个标记语言。

### 相关国际组织

- **IETF**：Internet Engineering Task Force（国际互联网工程任务组），成立于 1985 年底，是一个权威
  的互联网技术标准化组织，主要负责互联网相关技术规范的研发和制定，当前绝大多数国际互联网
  技术标准均出自 IETF。官网： https://www.ietf.org
- **W3C**：World Wide Web Consortium（万维网联盟），创建于 1994 年，是目前 Web 技术领域，最具影
  响力的技术标准机构。共计发布了 200 多项技术标准和实施指南，对互联网技术的发展和应用起到
  了基础性和根本性的支撑作用，官网： https://www.w3.org
- **WHATWF**：Web Hypertext Application Technology Working Group（网页超文本应用技术工作小组）成立
  于 2004 年，是一个以推动网络 HTML 5 标准为目的而成立的组织。由 Opera、Mozilla 基金会、苹果，
  等这些浏览器厂商组成。官网： https://whatwg.org/

## HTML 入门

### HTML 标签

1. **标签 又称 元素**，是 HTML 的**基本组成单位**。

2. 标签分为：**双标签** 与 **单标签** （绝大多数都是双标签）。

3. 标签名不区分大小写，但推荐小写，因为小写更规范。

4. 双标签：`<起始标签>标签体</结束标签>`

   ```
   <marquee>标签</marquee>
   ```

5. 单标签：`<起始名/>标签体` （/斜杠可以省略）

   ```
   <input>
   <br/>
   ```

6. 标签之间的关系：并列关系、嵌套关系，可以使用 tab 键进行缩进：

### HTML 标签属性

1. 用于给标签提供 **附加信息**。

2. 可以写在：起始标签 或 单标签中，形式如下：

   ```
   <标签名 属性名1=‘属性值1’ 属性名2=‘属性值2’>
   
   <marquee loop="1" bgcolor="orange"> sumorio的标签测试 </marquee> 
   #循环次数：1次，背景：橘色
   
   <input type="password">
   ```

3. 有些特殊的属性，没有属性名，只有属性值，例如：

   ```
   <input disabled>
   ```

4. 双引号，也可以写成单引号，甚至不写都行，但还是推荐写双引号。

5. 标签中不要出现同名属性，否则后写的会失效，例如：

   ```
   <input type="text" type="password">
   ```

### HTML 基本结构

1.在网页中，查看网页代码可以点击鼠标右键，选择“检查”。

2.【检查】 和 【查看网页源代码】的区别：

> 【查看网页源代码】看到的是：程序员编写的源代码。
> 【检查】看到的是：经过浏览器 “处理” 后的源代码。
> 备注：日常开发中，【检查】用的最多。

3. 网页的 基本结构 如下：

> 想要呈现在网页中的内容写在 `body` 标签中。
> `head` 标签中的内容不会出现在网页中。
> `head` 标签中的 title 标签可以指定网页的标题。

```
<html>
	<head>
		<title>网页标题</title>
	</head>
	<body>
		...
	</body>
</html>
```

### HTML 注释

1. 特点：注释的内容会被浏览器所忽略，不会呈现到页面中，但源代码中依然可见。
2. 作用：对代码进行解释和说明。
3. 写法：`<!-- 注释 -->`
4. 注释不可以嵌套。

### HTML 文档声明

1. 作用：告诉浏览器当前网页的版本。
2. 写法：请参考官网：[W3C](https://www.w3.org/QA/2002/04/valid-dtd-list.html)
3. 注意：文档声明，必须在网页的第一行，且在 html 标签的外侧。
4. Html类型的文件，在VsCode 中输入`!` ，随后回车即可快速生成标准结构。

### HTML 字符编码

1. 计算机对数据的操作：
   存储时，对数据进行：编码。
   读取时，对数据进行：解码。

2. 编码、解码，会遵循一定的规范 —— 字符集。

3. 字符集有很多中，常见有：

> 1. **ASCII** ：**大写字母、小写字母、数字、一些符号**，共计 128 个。
> 2. **ISO 8859-1** ：在 ASCII 基础上，扩充了一些**希腊字符**等，共计是 256 个。
> 3. **GB2312** ：继续扩充，收录了 6763 个**常用汉字**、682 个字符。
> 4. **GBK** ：收录了的**汉字和符号**达到 20000+ ，支持繁体中文。
> 5. **UTF-8** ：包含**世界上所有语言的：所有文字与符号**。—— 很常用。

4. 平时编写代码时，**统一采用 UTF-8 编码**（最稳妥）。

5. 为了让浏览器在渲染 html 文件时，不犯错误，可以通过 meta 标签配合 charset 属性指
   定字符编码。

   ```
   <head>
       <meta charset="UTF-8"/>
   </head>
   ```

## HTML 基础

### 排版标签

| 标签名 |            标签含义            | 单 / 双 标签 |
| :----: | :----------------------------: | :----------: |
| h1~h6  |              标题              |      双      |
|   p    |              段落              |      双      |
|  div   | 块级元素，用于布局，无实际意义 |      双      |

1. h1 最好写一个， h2~h6 能适当多写。
2. h1~h6 不能互相嵌套，例如： h1 标签中最好不要写 h2 标签。
3. **p 标签很特殊！它里面不能有： h1~h6 、p 、div 。**

### 语义化标签

概念：用特定的标签，去表达特定的含义。
原则：标签的默认效果不重要（后期可以通过 CSS 随便控制效果），**语义最重要！**
举例：对于 h1 标签，效果是文字很大（不重要），语义是网页主要内容（很重要）。
优势：

> 1. 代码结构清晰可读性强。
> 2. 有利于 SEO（搜索引擎优化）。
> 3. 方便设备解析（如屏幕阅读器、盲人阅读器等）。

### 块级元素 与 行内元素

1. **块级元素：独占一行**（排版标签都是块级元素）。
2. **行内元素：不独占一行**
3. 使用原则：

> 1. **块级元素 中能写 行内元素 和 块级元素。**
> 2. **行内元素 中能写 行内元素，但不能写 块级元素。**
>
> 3. 一些特殊的规则：
>
> 	- **h1~h6 不能互相嵌套。**
>
> 	- **p 中不要写块级元素。**

### 文本标签

1. 用**于包裹：词汇、短语等**。通常写在排版标签里面。
2. 相比排版标签更宏观（大段的文字），文本标签一般用于更微观（词汇、短语）。
3. 文本标签通常都是行内元素，除了blockquote 与 address 是块级元素。

> 1. **em**：要着重阅读的内容
> 2. **strong**：十分重要的内容（语气比em要强） 
> 3. **span**：没有语义，用于包裹短语的通用容器。（div 可看作是大包装袋， span 是小包装袋。）
> 4. **sub / sup** ：上下角标

### 图片标签

**img 图片：**

> - src ：图片路径—— 图片的具体位置
> - alt ：图片描述（搜索引擎增加曝光率，图片无法显示是使用，盲人阅读器会使用alt进行提示）
> - width ：图片宽度，单位是像素
> - height：图片高度， 单位是像素
>

**常见图片格式：**

1. jpg：有损压缩，颜色丰富，占用空间小。适用于对细节没要求的场景，宣传图等。
2. png：无损压缩。支持透明背景，颜色丰富，注重细节。适用于要求高质量细节场景，公司logo等。
3. bmp：无损压缩，占用空间极大，细节优秀。大型游戏场景等，网页较少使用。
4. gif：仅支持256种颜色，支持简单透明背景，支持动图。
5. webp：谷歌推出，专门用于网页呈现图片。兼容性可能差点
6. base64：一串特殊文本，需要通过浏览器打开，传统看图应用大概率打不开。可以直接作为img和src属性的值且不受文件位置的影响。适用于小图片，或者和网页一起加载的图片。

### 超链接

**a 超链接：**

> - href ： 指定要跳转到的具体目标。
>
> - target ： 控制跳转时如何打开页面，常用值如下:
>
> 	- _self ：在本窗口打开。
>
> 	- _blank ：在新窗口打开。
>
> - id ： 元素的唯一 标识，可用于设置锚点。
>
> - name ： 元素的名字，写在a 标签中，也能设置**锚点**。
>
>   ***name 和id 都是区分大小写的，id 最好不要数字开头。***

#### **1. 跳转到页面**

```
<!-- 跳转其他网页 -->
<a href="https://www.sumorio.com/" target="_blank">去苏末了的主页</a>

<!-- 跳转本地网页 -->
<a href="./10_HTML排版标签.html" target="_self">去看排版标签</a>
```

注意点：

- 代码中的多个空格、多个回车，都会被浏览器解析成一个空格！

- **虽然a 是行内元素，但a 元素可以包裹除它自身外的任何元素！**

#### **2. 跳转到文件**

```
<!-- 浏览器能直接打开的文件 -->
<a href="./resource/自拍.jpg">看自拍</a>
<a href="./resource/电影.mp4">看电影</a>
<a href="./resource/图片.gif">看图片</a>
<a href="./resource/看文件.pdf">看文件</a>

<!-- 浏览器不能打开的文件，会自动触发下载 -->
<a href="./resource/内部资源.zip">内部资源</a>

<!-- 强制触发下载 -->
<a href="./resource/电影.mp4" download="电影片段.mp4">下载电影</a>
```

#### 3. 跳转到锚点

**什么是锚点？—— 网页中的一个标记点。**

具体使用方式：设置锚点的时候不用写#，在href中跳转时需要写#。id是通用属性，可以和任意标签搭配使用用作锚点，但是name只能和a标签配合才是锚点性质。

- **第一步：设置锚点**

```
<!-- 第一种方式：a标签配合name属性 -->
<a name="test1"></a>

<!-- 第二种方式：其他标签配合id属性 -->
<h2 id="test2">我是一个位置</h2>
```

**注意点：**

1. 具有 `href `属性的` a` 标签是超链接，具有` name` 属性的` a `标签是锚点。
2. `name `和`id `都是区分大小写的，且`id `最好别是数字开头。

- **第二步：跳转锚点**

```
<!-- 跳转到test1锚点-->
<a href="#test1">去test1锚点</a>

<!-- 跳到本页面顶部 -->
<a href="#">回到顶部</a>

<!-- 跳转到其他页面锚点 -->
<a href="demo.html#test1">去demo.html页面的test1锚点</a>

<!-- 刷新本页面 -->
<a href="">刷新本页面</a>

<!-- 执行一段js,如果还不知道执行什么，可以留空，javascript:; -->
<a href="javascript:alert(1);">点我弹窗</a>
```

#### 4. 唤起指定应用

通过a 标签，可以唤起设备应用程序。

```
<!-- 唤起设备拨号 -->
<a href="tel:10010">电话联系</a>

<!-- 唤起设备发送邮件 -->
<a href="mailto:10010@qq.com">邮件联系</a>

<!-- 唤起设备发送短信 -->
<a href="sms:10086">短信联系</a>
```

### 列表

1. 有序列表ordered list：有顺序或侧重顺序的列表。

```
<h2>要把大象放冰箱总共分几步</h2>
<ol>
    <li>把冰箱门打开</li> # list item =li
    <li>把大象放进去</li>
    <li>把冰箱门关上</li>
</ol>
```

2. 无序列表unordered list：无顺序或不侧重顺序的列表。

```
<h2>我想去的几个城市</h2>
<ul>
    <li>成都</li>
    <li>上海</li>
    <li>西安</li>
    <li>武汉</li>
</ul>
```

3. 列表嵌套：列表中的某项内容，又包含一个列表。 li 标签最好写在 ul 或 ol 中，不要单独使用。

4. 自定义列表definition list：
	- 一个包含**术语名称**以及**术语描述**的列表。
	- 一个dl 就是一个自定义列表，一个dt 就是一个术语名称，一个dd 就是术语描述（可以有多个）。


```
<h2>如何高效的学习？</h2>
<dl>
    <dt>做好笔记</dt> # defination title
    <dd>笔记是我们以后复习的一个抓手</dd> # defination description 
    <dd>笔记可以是电子版，也可以是纸质版</dd>
    <dt>多加练习</dt>
    <dd>只有敲出来的代码，才是自己的</dd>
    <dt>别怕出错</dt>
    <dd>错很正常，改正后并记住，就是经验</dd>
</dl>
```

### 表格

#### 1. **基本结构**

{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240118151805.png %}

1. 一个完整的表格table有四部分：表格标题caption、表格头部thead、表格主体tbody、表格脚注tfoot。

2. 表格涉及到的标签：

> - table ：表格
> - caption ：表格标题
> - thead ：表格头部
> - tbody ：表格主体
> - tfoot ：表格注脚(可选)
> - tr ：每一行(table row)
> - th/td ：每一个单元格（表格头部用th-thead ，表格主体/表格脚注用： td-tdata ）

```
#先给出框架caption,thead,tbody,tfood四部分;再分别看每个部分的行数；最后补充每行数据。（不容易乱）
<body>
    <table border="5">
        <caption>学生信息表</caption>
        <thead>
          <tr>
            <th>姓名</th>
            <th>年龄</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>张三</td>
            <td>15</td>
          </tr>
          <tr>
            <td>李四</td>
            <td>16</td>
          </tr>
        </tbody>
        <tfoot>
          <tr>
            <td></td>
            <td>31</td>
          </tr>
        </tfoot>
    </table>
</body>
```

#### 2. 常用属性

{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240118110908.png %}

**注意点：**

1. <table> 元素的border 属性可以控制表格边框，但border 值的大小，并不控制单元格
边框的宽度，
只能控制表格最外侧边框的宽度，这个问题如何解决？—— 后期靠CSS 控制。
2. 默认情况下，每列的宽度，得看这一列单元格最长的那个文字。
3. 给某个th 或td 设置了宽度之后，他们所在的那一列的宽度就确定了。
4. 给某个th 或td 设置了高度之后，他们所在的那一行的高度就确定了。

#### 3. 跨行跨列（合并单元格）

1. rowspan ：指定要跨的行数。
2. colspan ：指定要跨的列数。

### 常用标签补充

1. br 换行。单( 不要用br增加文本行间隔，应该用`<p>`想要增加间距最好用css )
2. hr 分隔。单( 想要增加分割使用hr,想要分割线使用css )
3. pre 按原文显示。双（一般用于在页面中嵌入大段代码）

### 表单

概念：一个包含交互的区域，用于收集用户提供的数据。

#### 基本结构

{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240118144034.png %}

示例代码：

```
<form action="https://www.baidu.com/s" target="_blank" method="get">
    <input type="text" name="wd">
    <button>去搜索</button>
</form>
```

#### 常用表单控件

##### ①文本输入框：

`<input type="text">`

**常用属性如下：**
name 属性：数据的名称。
value 属性：输入框的默认输入值。
maxlength 属性：输入框最大可输入长度。

##### ② 密码输入框

`<input type="password">`

**常用属性如下：**

name 属性：数据的名称。
value 属性：输入框的默认输入值（一般不用，无意义）。
maxlength 属性：输入框最大可输入长度。

##### ③ 单选框

`<input type="radio" name="sex" value="female">`女
`<input type="radio" name="sex" value="male">`男

**常用属性如下：**
name 属性：数据的名称，注意：想要单选效果，多个radio 的 name 属性值要保持一致。
value 属性：提交的数据值。
checked 属性：让该单选按钮默认选中。

##### ④ 复选框

`<input type="checkbox" name="hobby" value="smoke">`抽烟
`<input type="checkbox" name="hobby" value="drink">`喝酒
`<input type="checkbox" name="hobby" value="perm">`烫头

**常用属性如下：**
name 属性：数据的名称。
value 属性：提交的数据值。
checked 属性：让该复选框默认选中。

##### ⑥ 提交按钮

`<input type="hidden" name="tag" value="100">`

用户不可见的一个输入区域，作用是： 提交表单的时候，携带一些固定的数据。
name 属性：指定数据的名称。
value 属性：指定的是真正提交的数据。

##### ⑥ 提交按钮

`<input type="submit" value="点我提交表单">`
`<button> 点我提交表单</button>`

**注意：**

1. button 标签 type 属性的默认值是 submit 。
2. button 不要指定name 属性
3. input 标签编写的按钮，使用value 属性指定按钮文字。

##### ⑦ 重置按钮

```<input type="reset" value="点我重置">```
```<button type="reset">点我重置</button>```

**注意：**

1. button 不要指定name 属性
2. input 标签编写的按钮，使用value 属性指定按钮文字。

##### ⑧ 普通按钮

`<input type="button" value="普通按钮">`
```<button type="button">普通按钮</button>```

**注意：**

普通按钮的type 值为button ，若不写type 值是submit 会引起表单的提交。

确认按钮可以有button和input的两种写法，submit作为按钮的时候不要写name带值，

##### ⑨文本域

```<textarea name="msg" rows="22" cols="3">我是文本域</textarea>```

**常用属性如下：**

1. rows 属性：指定默认显示的行数，会影响文本域的高度。
2. cols 属性：指定默认显示的列数，会影响文本域的宽度。
3. 不能编写type 属性，其他属性，与普通文本输入框一致。

##### ⑩ 下拉框

```
<select name="from">
    <option value="黑">黑龙江</option>
    <option value="辽">辽宁</option>
    <option value="吉">吉林</option>
    <option value="粤" selected>广东</option> #被选中，selected
</select>
```

**常用属性及注意事项：**

1. name 属性：指定数据的名称。
2. option 标签设置value 属性， 如果没有value 属性，提交的数据是option 中间的文
    字；如果设置了value 属性，提交的数据就是value 的值（建议设置 value 属性）
3. option 标签设置了 selected 属性，表示默认选中。

####  禁用表单控件(前端不可改)

给表单控件的标签设置 disabled 既可禁用表单控件。

input 、textarea 、button 、select 、option 都可以设置 disabled 属性

#### label 标签

label 标签可与表单控件相关联，关联之后点击文字，与之对应的表单控件就会获取焦点。
两种与label 关联方式如下：
1. 让label 标签的for 属性的值等于表单控件的id 。
2. 把表单控件套在 label 标签的里面。

#### fieldset 与 legend 的使用（了解）
fieldset 可以为表单控件分组、legend 标签是分组的标题。

```
<fieldset>
    <legend>主要信息</legend>
    <label for="zhanghu">账户：</label>
    <input id="zhanghu" type="text" name="account" maxlength="10"><br>
    <label>
        密码：
        <input id="mima" type="password" name="pwd" maxlength="6">
    </label>
    <br>
    性别：
    <input type="radio" name="gender" value="male" id="nan">
    <label for="nan">男</label>
    <label>
        <input type="radio" name="gender" value="female" id="nv">女
    </label>
    </fieldset>
```

### 框架标签

**iframe框架（在网页中生成有一个框架方块，可嵌入其他文件）**

- name ：框架名字，可以与 target 属性配合。
- width ： 框架的宽。
- height ： 框架的高度。
- frameborder ：是否显示边框，值：0或者1。

**iframe 标签的实际应用：**

1. **在网页中嵌入广告。**
2. 与超链接或表单的 target 配合，展示不同的内容。

### HTML实体

在HTML 中我们可以用一种**特殊的形式**的内容，来表示**某个符号**，这种特殊形式的内容，就是HTML 实
体。比如小于号 < 用于定义 HTML 标签的开始。如果我们希望浏览器正确地显示这些字符，我们必须
在HTML 源码中插入字符实体。

> 字符实体由三部分组成：一个& 和 一个实体名称（或者一个# 和 一个实体编号），最后加上一
> 个分号; 。

{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240118144843.png %}

### HTML全局属性

**常用的全局属性：**

{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240118151238.png %}

### meta 元信息
```
<meta charset="utf-8"> 
#配置字符编码

<meta http-equiv="X-UA-Compatible" content="IE=edge"> 
#针对IE 浏览器的兼容性配置。

<meta name="viewport" content="width=device-width, initial-scale=1.0"> 
#针对移动端的配置

<meta name="keywords" content="8-12个以英文逗号隔开的单词/词语">
#配置网页关键字

<meta name="description" content="80字以内的一段话，与网站内容相关"> 
#配置网页描述信息

<meta name="robots" content="此处可选值见下表"> 
#针对搜索引擎爬虫配置

<meta name="author" content="tony">
#配置网页作者

<meta name="generator" content="Visual Studio Code">
#配置网页生成工具

<meta name="copyright" content="2023-2027©版权所有"> 
#配置定义网页版权信息

<meta http-equiv="refresh" content="10;url=http://www.baidu.com">
#配置网页自动刷新
```

## 重点记忆

{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240118152909.png %}
