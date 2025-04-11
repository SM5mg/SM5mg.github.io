---
layout: wiki #layout 的值固定为wiki，与第二项一同作用于侧边栏，如果没有它们侧边栏也会消失
wiki: Build_self_networks # wiki 的值写你在source/_data/projects.yml中新增的项目名
title: Hexo-Stellar魔改装修 # 文章标题
---

> Stellar 主题全面的配置文档可参考源码作者：[Xaoxuu](https://xaoxuu.com/wiki/stellar/#start).
> 为了方便记录，博客文件夹路径用[Blog-root]

## 修改站点信息

Stellar 会读取站点根目录`\_config.yml` 文件中的信息来生成网站，直接修改即可：

```js _config.yml
title: 您的网站名称
avatar: 您的头像链接
favicon: 您的网站icon
subtitle: 您的网站副标题
# 多语言
language:
  - zh-CN
  - en
```

## 创建主题配置文件

> 在博客根目录的  `_config.yml`  文件同目录中新建一个文件： `_config.stellar.yml` ；在这个文件中的配置信息优先级高于主题文件夹中的配置文件。

## 字体设置

- 第一步：\_config.yml 文件中，最后一行加入以下指令：

```js _config.yml
inject: head: -(
  <link
    rel="stylesheet"
    href="https://cdn.staticfile.org/lxgw-wenkai-screen-webfont/1.6.0/lxgwwenkaiscreen.css"
    media="all"
  />
);
```

- 第二步：在\_config.stellar.yml 中找到 style.font-family，修改以下内容：

```js _config.stellar.yml
style:
    font-family:
        logo: '"LXGW WenKai Screen", ...
        body: '"LXGW WenKai Screen", ...
```

## 添加运行时间

- 第一步：\_config.stellar.yml 文件下，找到  footer , 在 content: 之后添加代码。
- 第二步：修改 X 部分的时间，改成自己网站成立的年月日即可。

```js _config.stellar.yml
  content: | # 支持 Markdown 格式
    <center>
    </br>
    </br>
    <script type="text/javascript">
    function show_runtime() {
        window.setTimeout("show_runtime()", 1000);
        X = new Date("10/20/2023 00:00:00 ");
        Y = new Date();
        T = (Y.getTime() - X.getTime());
        M = 24 * 60 * 60 * 1000;
        a = T / M;
        A = Math.floor(a);
        b = (a - A) * 24;
        B = Math.floor(b);
        c = (b - B) * 60;
        C = Math.floor((b - B) * 60);
        D = Math.floor((c - C) * 60);
        runtime_span.innerHTML = "⏲️ 本站已运行 " + A + "天|" + B + "小时|" + C + "分|" + D + "秒 ⏲️"
    }
    show_runtime();
    </script>
    <span id="runtime_span"> </span>
    </center>
```

## 代码块复制

在\_config.stellar.yml 修改：

``` js _config.stellar.yml
copycode:
  enable: true
  js: /js/plugins/copycode.js
  default_text: 'Copy' # 按钮显示文字
  success_text: 'Copied' # 复制成功信息
```

## 添加背景动态线条效果

在  `layout.ejs`  的`<body>`里添加代码：
最好用系统自带的记事本打开

``` js /theme/stellar/layout.ejs
<!--动态线条背景-->
< script type = "text/javascript"
  color = "220,220,220" opacity ='0.7' zIndex = "-2" count = "200" src = "//cdn.bootcss.com/canvas-nest.js/1.0.0/canvas-nest.min.js" >
</script>
```
- `color`：线条颜色，三个数字分别为(R, G, B)，默认：（0,0,0）;
- `opacity`：线条透明度（0~1），默认：0.5;
- `count`：表示线条的总数量，默认：150;
- `zIndex`：表示背景的 z-index 属性，css 属性用于控制所在层的位置，默认：-1;


## 主题版本更新

方法一：稳定版

1. 在 package.json 中修改 stellar 的版本号，然后执行：
{% copy npm i prefix:$ %}

2. 阅读 [更新日志](https://github.com/xaoxuu/hexo-theme-stellar/releases) 选择合适版本进行迁移。

方法二：最新版

1. 进入`/blog/themes/`文件，启动 git bash, 执行命令。下载最新版的主题，删除旧版本
{% copy git submodule add https://github.com/xaoxuu/hexo-theme-stellar.git themes/stellar prefix:$ %}
2. 进入主题文件/themes/stellar/, 启动 git bash，执行命令。
{% copy git pull prefix:$ %}

## 文章页顶部导航栏

{% image https://s2.loli.net/2023/12/19/HWlkvSi8sY2G7VX.png %}

修改配置文件`_config.stellar.yml`,添加标题和文件链接：

``` js _config.stellar.yml
// 旧版本：
# 顶部检索栏
post-index: # 近期发布 分类 标签 归档 and ...
  "专栏": /wiki/ 
  "博客搭建": /wiki/Hexo/xx.html 

// 新版本：
  index_blog:
    nav_tabs:  # 近期发布 分类 标签 专栏 归档 and ...
      "留言": /about/#comments #点击到网页复制路径
```

## 侧边栏欢迎语
1.  侧边栏支持使用 markdown 语法，markdown 支持 HTML 语言，可以通过 HTML 自定义各种样式的侧边栏.
2.  在主题文件目录下的\_data/widgets.yml 文件中新增一项侧边栏配置，写下你的网站欢迎语.
3.  可以引用开放接口，如【今日诗词】.

``` js _data/widgets.yml
  welcome:
      layout: markdown
      title: '🎉 欢迎 '
      content: |
          本站托管于 Github, 可能会出现加载缓慢或丢失问题，欢迎在评论区交流技术知识。
          <br> <hr>
          今日诗词:  <span id="jinrishici-sentence"> </span>
          <script src="https://sdk.jinrishici.com/v2/browser/jinrishici.js" charset="utf-8"> </script>
```
4. 修改主题配置\_config.stellar.yml，设置欢迎语出现的具体位置

``` js _config.stellar.yml
  widgets:
    #### 自动生成的页面 ####
    # 主页
    home: search, welcome, recent, tagcloud, timeline # for home
```

## 侧边栏免责声明

主题文件目录下的\_data/wodgets.yml 文件中新增一项侧边栏配置，使用 markdown 布局

``` js _data/wodgets.yml
statement:
    layout: markdown
    title: '<br>'
    content: |
        <hr>
        <center>
        <h4 id="免责声明"> 免责声明 </h4>
        <p> 本站提供的一切软件、教程和内容信息仅限用于学习和研究目的。</p>
        <p> 不得将上述内容用于商业或非法用途，否则一切后果自负。</p>
        <p> 本站信息来自网络收集整理，版权争议与本站无关。</p>
        <p> 如果有侵权之处请第一时间联系站长删除。敬请谅解! </p>
        </center>
```

## 永久链接插件

永久链接指用一串随机字符替代文章名作为网页访问链接，这样即使修改文章名称也不会改变文章访问链接，有助于网站 SEO 优化

1. 在项目根路径下安装永久链接插件
{% copy npm install hexo-abbrlink --save prefix:$ %}

2. 修改`_config.yml`中的配置，启用永久链接

``` js _config.yml
permalink: posts/: abbrlink.html
```

3. 配置文件底部添加如下配置，可以实现更优算法生成永久链接

``` js _config.yml
  # abbrlink 配置
  abbrlink:
    alg: crc32      #算法，支持 crc16(default)和 crc32
    rep: hex        #进制，支持 dec(default)和 hex
    drafts: false   #true：对草稿也进行处理，false：不处理草稿。默认为 false
    # 从目录树生成类别
    # depth: 您想生成的目录树的最大深度, 需要大于 0
    auto_category:
      enable: true  #默认为 true
      depth:        #默认为 3
      over_write: false
    auto_title: false #启用自动标题，它可以按路径自动填充标题
    auto_date: false #启用自动日期，可以按今天的时间自动填写日期
    force: false #启用 Force 模式，在这种模式下插件将忽略缓存，并为每一篇文章计算生成永久链接，即使它已经有了永久链接。这个设置只会更新永久链接，而不是更新其他前置变量。
```

4. 在生成静态页面时，插件会自动在 Markdown 文件头部生成永久链接参数

```
  ---
  title: Hello World
  abbrlink: 4a17b156
  ---
```

5. 重新生成网页发布后，网页访问链接就变成了 `../posts/4a17b156.html` 的格式。

## 创建自定义 CSS

1. `source`目录下新建文件夹`css`，在 CSS 目录下新建我们自定义文件 `my.css`

2. 博客配置文件`_config.yml`中引入 CSS 文件，CSS 文件一般在`head`引入，JS 文件一般在`script`里引入

``` js _config.yml
inject:
  head:
    # 自定义 css，静态文件后面加个 "?任意内容"，可以在每次更新之后用户自动重新请求，避免用户使用本地缓存
    - <link rel="stylesheet" href="/css/my.css?1">
  script:
    # 自定义 js
    - <script type="text/javascript" src="/js/script.js?1"> </script>
    - <script src="/js/script.js?1"> </script>

```

## 添加评论功能

目前 Staller 主题集成多种评论功能插件，包括 beaudar、utterances、giscus、twikoo、waline、artalk。今日来探讨 twikoo.

1. 配置 twikoo 云函数，参考如下链接。
- 教程过长，参考我的另一篇文章：[Hexo-Stellar配置TWIKOO评论系统](301Twikoo-deployment.html)
- [Twikoo 官网参考 ](https://twikoo.js.org/)

2. 在博客配置文件`_config.stellar.yml`中启用 twikoo 评论

``` js _config.stellar.yml
  ######## Comments ########
  comments:
    service: twikoo

    # Twikoo
    # https://twikoo.js.org/
    twikoo:
      js: https://gcore.jsdelivr.net/npm/twikoo@1.6.8/dist/twikoo.all.min.js # 建议锁定版本
      envId: https://xx.xx.com # twikoo 云函数
```

3. 评论功能目前已配置成功。如果需要在 page 或 post 文件头部显示，可以添加`comments`字段指定该页面启用评论。
  
```
  ---
  comments: true
  ---
```

4. 在 twikoo 管理面板中通过`DEFAULT_GRAVATAR`参数可以设置评论默认使用的头像类型，具体有如下几类:

{% image https://s2.loli.net/2023/12/19/ErteBbA3iRkHzXI.png %}

5. 给评论添加输入提示框，在我们前面创建的自定义 CSS 文件中插入如下代码:

```
/* 设置文字内容 : nth-child(1)的作用是选择第几个 */
.el-input.el-input--small.el-input-group.el-input-group--prepend: nth-child(1): before {
    content: '输入 QQ 号会自动获取昵称和头像 🐧';
}

.el-input.el-input--small.el-input-group.el-input-group--prepend: nth-child(2): before {
    content: '收到回复将会发送到您的邮箱 📧';
}

.el-input.el-input--small.el-input-group.el-input-group--prepend: nth-child(3): before {
    content: '可以通过昵称访问您的网站 🔗';
}

/* 当用户点击输入框时显示 */
.el-input.el-input--small.el-input-group.el-input-group--prepend:focus-within:: before,
.el-input.el-input--small.el-input-group.el-input-group--prepend:focus-within:: after {
    display: block;
}

/* 主内容区 */
.el-input.el-input--small.el-input-group.el-input-group--prepend:: before {
    /* 先隐藏起来 */
    display: none;
    /* 绝对定位 */
    position: absolute;
    /* 向上移动 60 像素 */
    top: -60px;
    /* 文字强制不换行，防止 left: 50%导致的文字换行 */
    white-space: nowrap;
    /* 圆角 */
    border-radius: 10px;
    /* 距离左边 50% */
    left: 50%;
    /* 然后再向左边挪动自身的一半，即可实现居中 */
    transform: translate(-50%);
    /* 填充 */
    padding: 14px 18px;
    background: #444;
    color: #fff;
}

/* 小角标 */
.el-input.el-input--small.el-input-group.el-input-group--prepend:: after {
    display: none;
    content: '';
    position: absolute;
    /* 内容大小（宽高）为 0 且边框大小不为 0 的情况下，每一条边（4 个边）都是一个三角形，组成一个正方形。
    我们先将所有边框透明，再给其中的一条边添加颜色就可以实现小三角图标 */
    border: 12px solid transparent;
    border-top-color: #444;
    left: 50%;
    transform: translate(-50%, -48px);
}

/* 带链接的用户名显示为红色 */
.tk-nick.tk-nick-link {
    color: #f56c6c! important;
}

```

## 项目标签彩色更改

进入\_config.stellar.yml 文件，更改 article 中的 category 标签：

``` js _config.stellar.yml
article:
  # 分类颜色
  category_color:
    "探索号": "#4CB9E7"
    "博客搭建": "#4CB9E7"
    "Hexo": "#FF004D"
    "ChatGPT": "#43766C"
    "绘画": "#11009E"
    "前端": "#F08A5D"
```
{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240112144930.png %}

## 侧边栏时间线新增

假设我们需要在主页和专栏的文章内页侧边栏处，分别新增`主题更新进度`的时间线，需要三步。

 1. 在`/source/data/widgets.yml`中新增`主题进度`时间线标签
 2. 将新增的时间线标签，填写于`/source/wiki/项目名.yml`的配置中
 3. 将新增的时间线标签，填写至`_config.stellar.yml`的配置中
{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240112160736.png width:300px %}

```js /source/data/widgets.yml
  release_update:
    layout: timeline
    title: 主题更新
    api: https://api.github.xaox.cc/repos/xaoxuu/hexo-theme-stellar/releases?per_page = 1
    user: xaoxuu
```

``` js /source/wiki/项目名.yml
  widgets:
    #### 自动生成的页面 ####
    # 主页-文章
    home: search, welcome-other, recent, tagcloud, release_update
```

``` js _config.stellar.yml
sidebar: -search - toc - release_update;
```

## 新增 memos 说说功能

想要实现 memos 功能，首先需要注册一个账号。注册账号可以使用别人已经搭建好的 memos，也可以自行搭建 memos（需要有服务器，我就不折腾了）。这里直接采用的[杜老师](https://dusays.com/561/)的 memos。

1. 点击进入[dusys.com[(https://dusays.com/561/) 查看教程，注册一个自己的账号。

2. 登录账号，个人资料点击 RSS，[s.dusays.com](https://s.dusays.com/u/87/rss.xml)，网址中U后面的数字就是自己的ID。
{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240116143217.png width:300px %}

3. 如果需要在 hexo-stellar 的侧边栏 sidebar 中展示 memos，首先在/source/\_data/widgets.yml 中新增一条记录，然后在相应页面的 sidebar 部分新增配置。

``` js /source/_data/widgets.yml
   memos-du:
     layout: timeline
     title: 说说
     api: https://s.dusays.com/api/v1/memo?creatorId = 87
     type: memos
     hide: user, footer
```

4. 如果需要在 hexo-stellar 的文章正文展示 memos，在正文任意位置新增以下代码。

``` js ***.md
{% timeline api:https://s.dusays.com/api/v1/memo?creatorId = 87&limit = 10 type: memos  avatar:https://s2.loli.net/2023/10/20/7okY5AhfK6LCn8q.jpg %}
{% endtimeline %}
```

## 修改 "开始使用" 按钮颜色

找到`themes/stellar/css/common/button.styl` 文件。修改其中的`a.button.start的backgroud`颜色。


## 二级标题去除“：”

md.styl文件中，配置h2    `a.headerlink:before content: ''`


##  随机文章跳转

1. 创建 `themes/stellar/scripts/helpers/random.js` ，增加以下代码：

```js themes/stellar/scripts/helpers/random.js
hexo.extend.filter.register('after_render: html', function (data) {
  const posts = []
  hexo.locals.get('posts').map(function (post) {
    if (post.random !== false) posts.push(post.path)
  })
  data += `<script>var posts=${JSON.stringify(posts)};function toRandomPost(){ window.pjax ? pjax.loadUrl('/'+posts[Math.floor(Math.random()*posts.length)]) : window.open('/'+posts[Math.floor(Math.random()*posts.length)], "_self"); };</script>`
  return data
})

```

2. _config.yml文件中引入 js文件 ，增加以下代码：

```js _config.yml
- <script src="/js/"> </script> # 随机文章
```

3. 需要时调用，2种执行方法，均`toRandomPost ()` 函数。

```
#使用按钮实现跳转：
<button onclick="toRandomPost()"> 随机阅读一篇文章 </button>

#使用链接实现跳转：
<a href="#" onclick="toRandomPost(); return false;"> 随机阅读一篇文章 </a>
```



## 字数统计：“发表了x篇文章，共计x字”

1. 安装 `hexo-wordcount` 插件：
{% copy npm i hexo-wordcount --save prefix:$ %}

2. 在 `themes/stellar/layout/_partial/main/footer.ejs` 中，找到以下部分：

``` js themes/stellar/layout/_partial/main/footer.ejs
// footer
  el += '<div class="text">'
  if (content) {
    el += markdown(content)
  }
```

在以上代码后面添加以下代码：

```
el += '<span class="totalcount"> 发表了 ' + site.posts.length + ' 篇文章 · </span> <span class="post-count"> 总计 ' + totalcount(site) + ' 字 </span>'
```

最后代码：

```
...
  // footer
  el += '<div class="text">'
  if (content) {
    el += markdown(content)
  }
  // 在这里添加帖子总数
  el += '<span class="totalcount"> 发表了 ' + site.posts.length + ' 篇文章 · </span> <span class="post-count"> 总计 ' + totalcount(site) + ' 字 </span>'
  el += '</div> </footer>'
  return el
}
%>
<%- layoutDiv() %>
```

3. 在自定义 css 里，增加以下代码修改风格：

```
.post-count {
    scrollbar-width: none;
    color: var(--text-p4);
  }

.totalcount {
    color: var(--text-p4);
  }
```



## 文章卡新增字数统计

1. 找到 `\themes\stellar\layout\_partial\main\post_list\post_card.ejs` 文件

2. 找到 `//meta` 处,代码修改后如下：

``` js themes\stellar\layout\_partial\main\post_list\post_card.ejs
  // meta
  el += '<div class="meta cap">';
  el += '<span class="cap" id="post-meta">';
  el += icon('default: calendar')
  // time
  el += `<time datetime="${date_xml(post.date)}">${date(post.date, config.date_format)}</time>`
  <!-- 新增字数统计 新增一行-->
  el += '<span class="post-count">&nbsp;'+ wordcount(post.content) +' 字 </span>';
  el += '</span>';
```

## Hexo-Stellar+Twikoo评论展示在侧边栏
  1. 新建 `twikoo_new.js` ,在 `theme/source/js/services/` 下

``` js /_twikoo_new.js
utils.jq(() => {
  const el = document.querySelector('.ds-twikoo');
  utils.onLoading(el); // 加载动画

  const api = el.getAttribute('api');
  const limit = parseInt(el.getAttribute('limit')) || 10;
  const reply = el.getAttribute('hide') !== 'reply';
  if (! api) return;

  fetch(api, {
    method: "POST",
    body: JSON.stringify({
      "event": "GET_RECENT_COMMENTS",
      "envId": api,
      "pageSize": limit,
      "includeReply": reply
    }),
    headers: { 'Content-Type': 'application/json' }
  })
  .then(res => res.json())
  .then(({ data }) => {
    utils.onLoadSuccess(el); // 移除动画
    data.forEach((comment, j) => {
      let commentText = comment.commentText;
      if (! commentText || commentText.trim() === '') return; // 跳过空评论
      // 转义字符
      commentText = commentText.replace(/&/g, "&amp;").replace(/</g, "&lt;").replace(/>/g, "&gt;").replace(/"/g, "&quot; ").replace(/'/g, "&#039;");
      commentText = commentText.length > 50 ? commentText.substring(0, 50) + '...' : commentText;
      var cell = '<div class="timenode" index="' + j + '">';
      cell += '<div class="header">';
      cell += '<div class="user-info">';
      cell += '<span>' + comment.nick + '</span>';
      cell += '</div>';
      cell += '<span>' + new Date(comment.created).toLocaleString('zh-CN', {month: '2-digit', day: '2-digit', hour: '2-digit', minute: '2-digit', hour12: false}) + '</span>';
      cell += '</div>';
      cell += '<a class="body" href="' + comment.url + '#' + comment.id + '">';
      cell += commentText;
      cell += '</a>';
      cell += '</div>';
      $(el).append(cell);
    });
  })
  .catch(() => utils.onLoadFailure(el));
});
```

2. `_config.stellar.yml`主题配置文件的 data_services 下引入脚本:

``` js _config.stellar.yml
 data_services:
  ...
  twikoo:
    js: /js/services/twikoo_new.js
```

3. 在 `_data/widgets.yml` 中创建小组件，使用:

``` js _data/widgets.yml
  new_comment:
    layout: timeline
    title: 最新评论
    api: https://comment.weekdaycare.cn # 此处为 Twikoo 函数，末尾不要加 /
    type: twikoo
    limit: 16 # 限制获取数量，默认为 10
    hide: reply # 是否隐藏回复，不填默认不隐藏
```


## 随机跳转文章

1. 在`themes/stellar/scripts/helpers/random.js`创建文件。

``` js themes/stellar/scripts/helpers/random.js
hexo.extend.filter.register('after_render: html', function (data) {
  const posts = []
  hexo.locals.get('posts').map(function (post) {
    if (post.random !== false) posts.push(post.path)
  })
  data += `<script>var posts=${JSON.stringify(posts)};function toRandomPost(){ window.pjax ? pjax.loadUrl('/'+posts[Math.floor(Math.random()*posts.length)]) : window.open('/'+posts[Math.floor(Math.random()*posts.length)], "_self"); };</script>`
  return data
})
```

2. 在主题配置文件 `_config.stellar.yml`的inject中添加代码引入：

``` js _config.stellar.yml
inject:
  head:
  script:
    - <script src="/js/random.js"> </script> # 随机文章
```

3. 在需要调用的位置执行 toRandomPost () 函数即可。示例2种方式：
  - 添加按钮并随机跳转：`<button onclick="toRandomPost()">随机阅读一篇文章</button>`
  - 添加链接并随机跳转：`<a href="#" onclick="toRandomPost(); return false;">随机阅读一篇文章</a>`

4. 也可以`widgets.yml`中调用：

``` js /source/_data/widgets.yml
welcome-info:
  layout: markdown
  title: 'hello！'
  linklist:
    columns: 1
    items:
      - icon: 图片链接
        title: 随机文章
        url: 'javascript: toRandomPost()'
  content: |
    <span id="welcome-info" style="font-family: LXGW WenKai Screen;"> </span>
```


## 页面底部字数统计

1. 安装 `hexo-wordcount` 插件：`npm i hexo-wordcount --save`

2. `themes/stellar/layout/_partial/main/footer.ejs` 文件中，找到`//footer`:

``` js themes/stellar/layout/_partial/main/footer.ejs
   // footer
     el += '<div class="text">'
     if (content) {
       el += markdown(content)
     }
```

   在这一段代码后加上如下：

``` js themes/stellar/layout/_partial/main/footer.ejs
   
   el += '<span class="totalcount"> 共发表 ' + site.posts.length + ' 篇 Blog · </span> <span class="post-count"> 总计 ' + totalcount(site) + ' 字 </span>'
   
```

3. 新建自定义css，可以放在`/hexo/source/custom/css/self.css`，加入css代码：

```
   .post-count {
       scrollbar-width: none;
       color: var(--text-p4);
     }
   
   .totalcount {
       color: var(--text-p4);
     }
   
   .page-footer {
       text-align: center; 
       margin: 0 auto; 
       width: 100%; 
   }
```

4. 在主题文件`_config.ym`l中引入css文件，才能生效：

```
   inject:
     head:
       - <link rel="stylesheet" href="/custom/css/self.css"> 
```

   教程来源:[宇宙尽头的餐馆](https://www.flyalready.cn/Hexo%20Stellar%20%E4%B8%BB%E9%A2%98%E8%A3%85%E4%BF%AE%E7%AC%94%E8%AE%B0/#%E9%9A%8F%E6%9C%BA%E6%96%87%E7%AB%A0%E8%B7%B3%E8%BD%AC)

## 文章面包屑显示字数|阅读时长|标签

1. 找到`themes\stellar\layout\_partial\main\footer.ejs`文件的`// 3.left.bottom`处，新增代码：

``` js themes\stellar\layout\_partial\main\footer.ejs
  // 3.left.bottom
  el += partial('dateinfo')
  //新增：字数显示|阅读时长显示
  el += '<div class="flex-row" id="page-words"> <span style="padding: 4px;"> 本文：' + wordcount(page.content) + '字 </span> <span class="sep updated" style="padding: 4px;"> </span> <span class="text updated" style="padding: 4px;"> 阅读时长：' + min2read(page.content) + '分 </span> </div>';
  //新增：标签显示
  if (page.layout == "post" && page.tags && page.tags.length > 0) {
    el += '<div class="flex-row" id="tag">'; // 将标签容器的创建移动到条件内部
    el += ' <span>&nbsp 标签：</span>';
    el += list_categories(page.tags, {
      class: "cap breadcrumb",
      show_count: false,
      separator: '&nbsp; ',
      style: "none"
    });
    el += '&nbsp </div>';
  }
```

2.在自定义css中新增代码，`/hexo/source/custom/css/self.css`，加入css代码：

``` js /hexo/source/custom/css/self.css
.bread-nav div#page-words span.sep: before {
  content: '|';
}
.bread-nav div#page-words span.updated {
  visibility: hidden;
}
.bread-nav: hover div#page-words span.updated {
  visibility: visible;
}

```

教程来源:[Thun888](https://blog.hzchu.top/2024/%E4%B8%BB%E9%A2%98%E6%94%B9%E5%8A%A8%E5%B0%8F%E8%AE%B0/#%E5%AD%97%E6%95%B0%E7%BB%9F%E8%AE%A1)



##  fontawesome 动态图标

在配置文件中引入新增的CSS：

``` js _config.yml
inject:
  head:
    - <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.2/css/all.min.css">

```

引入后就可以使用动态图标了，类似左下角的图标跳动部分。

比如，在组件中加入动态图标：

``` js \blog\source\_data\widgets.yml
"朋友圈":
  layout: timeline
  title: '<i class="fa-solid fa-snowflake fa-spin" style="color: #08D9D6;"> </i> 朋友文章'                                
  api: https://api.vlts.cc/output_data/v1/Sumorio/hexo-circle-of-friends # 你的朋友圈数据文件地址
  # api: https://raw.githubusercontent.com/Sumorio/hexo-circle-of-friends/output/data.json # 你的朋友圈数据文件地址
  type: fcircle
  limit: 5 # 可通过这个限制最大数量
```



## jsDelivr 加速 GitHub 文件访问

使用[jsdelivr转换工具](https://www.jsdelivr.com/github)，将 Github 链接转 Jsdelivr，将原链接替换为转化后的链接，实现国内访问加速。





## 捐赠码功能

博主建站、申请域名、网站维护都需要耗费很大精力，赏个鸡腿全速起飞。

找到代码倒数第五行，将下面代码放置在` el += '</div>';`上一行：

```js \themes\stellar\layout\_partial\main\article\article_footer.ejs
  if (theme.article.donate) {
    const donateImage = () => {
      if (theme.article.donate.wechat) {
        return `
        <div class="donate-image" id="donate-wechat" style="display:none; position:absolute; z-index:1000; transform: translateY(-100%); left: 50%; transform: translateX(-50%) translateY(-100%);">
          <img src="${theme.article.donate.wechat}" alt="Donate with WeChat" style="width: 150px; height: auto;" />
        </div>
        `;
      } else {
        return '';
      }
    };
    el += `
    <section id="donate">
      <div class="header"><span>${__('meta.donate')}</span></div>
      <div class="body">
        <p>${__('点击爱心给作者加鸡腿~ ')}
          <span class="donate-icon" onclick="showQRCode()" style="display: inline-block;">
            <i class="fas fa-heart fa-flip" style="font-size: 20px; color:#fe8f8f;"></i>
          </span>
        </p>
        ${donateImage()}
      </div>
    </section>
    `;
    el += `
    <script>
      const showQRCode = () => {
        const qrCode = document.getElementById('donate-wechat');
        qrCode.style.display = 'block';

        document.addEventListener('click', hideQRCode);
      };

      const hideQRCode = (event) => {
        const qrCode = document.getElementById('donate-wechat');
        const donateIcon = document.querySelector('.donate-icon');

        if (!qrCode.contains(event.target) && !donateIcon.contains(event.target)) {
          qrCode.style.display = 'none';

          document.removeEventListener('click', hideQRCode);
        }
      };
    </script>
    `;
  }
  el += '</div>';
  return el;
}
```
在`_config.stellar.yml`中新增`donate`板块。
```js _config.stellar.yml
######## Article ########
article:
  donate:
    wechat: '收款二维码图片地址'
```
在`\themes\stellar\languages\zh-CN.yml`文件中新增该板块显示的名称，可任意取名。
```js \themes\stellar\languages\zh-CN.yml
meta:
  donate: 捐赠处
```

## friends友链卡片样式微调
```styl /themes/stellar/source/css/_components/tag-plugins/friends.styl
// transform 角度
.users-wrap .user-card .card-link
    img
      transform: scale(1.5) rotate(360deg) /* rotate旋转角度修改 */


.users-wrap .user-card
    img
      border-radius: 8px /* 图片的圆角设置 */
```