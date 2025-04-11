---
layout: wiki #layout 的值固定为wiki，与第二项一同作用于侧边栏，如果没有它们侧边栏也会消失
wiki: Build_self_networks # wiki 的值写你在source/_data/projects.yml中新增的项目名
title: Stellar主题黑白模式切换 # 文章标题

---
仅适用于旧版主题，新版不适用，留存。

## 修改思路

1. 抽离夜间样式
2. 增加 CSS 文件优先级
3. 网页添加主题按钮

### 1）抽离夜间样式

- 前提 1：原主题配置文件控制昼夜是通过`style.darkmode: false # auto / always / false`来控制 stylus 生成整个网站`main.css；`
- 前提 2：主题样式代码中`if hexo-config('style.darkmode') == 'always'`包裹的就是夜间主题代码；
- 结论：我们把它抽离出一个单独的`ZYDark.css`文件。

### 2）增加 CSS 文件优先级

- 通过给 html 标签一个 ID 来取得优先级, 抽离的`ZYDark.css`都赋予这个 ID.
  比如`:root{--site-bg: #1c1e21;}`变成`#ZYDark:root{--site-bg: #1c1e21;}`

### 3）网页添加主题按钮

想了很多种方案都达不到主题样式一致原则.

最后发现 stellar 左下角页脚部分有 7 个位置。

就拿他来当切换按钮吧!

### 4）储存与功能实现

用户变量就扔到`localStorage`储存,反正不清空浏览器缓存就是永久储存.

功能实现函数操作全都是一个 JS 执行, 包括给 html 标签一个 ID.

### 5）黑夜闪白优化

因为一些渲染顺序原因这个 js 只能放到网页靠末尾地方, 可能不是控制主题功能我还有其它功能方法, 所以结果是黑暗模式下刷新有点闪白色.

解决办法是在 head 引入一个提前 js,即判断`localStorage`是黑暗就马上给 html 加黑色 ID, 后续渲染就没问题了!!!

## 代码

### 样式

复制以下代码并重命名为 ZYDark.css，放至本地路径/blog/source/custom/css 下。

```python
#ZYDark:root {
  --site-bg: #1c1e21;
  --card: #373d43;
  --block: #26292c;
  --block-border: #383d42;
  --block-hover: #2f3337;
  --text-p0: #fff;
  --text-p1: #ccc;
  --text-p2: #b3b3b3;
  --text-p3: #858585;
  --text-p4: #707070;
  --text-meta: #4d4d4d;
  --text-code: #ff6333;
}
@media screen and (max-width: 667px) {
  #ZYDark:root {
    --site-bg: #000;
  }
}
#ZYDark:root {
  --blur-bg: rgba(0,0,0,0.5);
}
#ZYDark .float-panel {
  --blur-bg: rgba(0,0,0,0.4);
}
#ZYDark .tag-plugin.tag {
  --theme: #ff6333;
  --theme-bg1: #3d1e14;
  --theme-bg2: #2f2522;
  --theme-border: #5c2d1f;
  --text-p0: #ffc4b3;
  --text-p1: #dfae9f;
  --text-p2: #f1997e;
}
#ZYDark .tag-plugin[color='red'] {
  --theme: #f44336;
  --theme-bg1: #3d1714;
  --theme-bg2: #2f2322;
  --theme-border: #5c231f;
  --text-p0: #ffb8b3;
  --text-p1: #dfa49f;
  --text-p2: #f1867e;
}
#ZYDark .tag-plugin[color='orange'] {
  --theme: #fa6400;
  --theme-bg1: #3d2514;
  --theme-bg2: #2f2722;
  --theme-border: #5c371f;
  --text-p0: #ffd1b3;
  --text-p1: #dfb99f;
  --text-p2: #f1ac7e;
}
#ZYDark .tag-plugin[color='yellow'] {
  --theme: #ffbd2b;
  --theme-bg1: #3d3014;
  --theme-bg2: #2f2b22;
  --theme-border: #5c491f;
  --text-p0: #ffe7b3;
  --text-p1: #dfcb9f;
  --text-p2: #f1cd7e;
}
#ZYDark .tag-plugin[color='green'] {
  --theme: #3dc550;
  --theme-bg1: #143d1a;
  --theme-bg2: #222f24;
  --theme-border: #1f5c27;
  --text-p0: #b3ffbd;
  --text-p1: #9fdfa8;
  --text-p2: #7ef18e;
}
#ZYDark .tag-plugin[color='cyan'] {
  --theme: #1bcdfc;
  --theme-bg1: #14353d;
  --theme-bg2: #222d2f;
  --theme-border: #1f4f5c;
  --text-p0: #b3efff;
  --text-p1: #9fd2df;
  --text-p2: #7ed9f1;
}
#ZYDark .tag-plugin[color='blue'] {
  --theme: #2196f3;
  --theme-bg1: #142b3d;
  --theme-bg2: #222a2f;
  --theme-border: #1f415c;
  --text-p0: #b3ddff;
  --text-p1: #9fc3df;
  --text-p2: #7ebef1;
}
#ZYDark .tag-plugin[color='purple'] {
  --theme: #9c27b0;
  --theme-bg1: #37143d;
  --theme-bg2: #2d222f;
  --theme-border: #531f5c;
  --text-p0: #f4b3ff;
  --text-p1: #d69fdf;
  --text-p2: #e07ef1;
}
#ZYDark .tag-plugin[color='light'] {
  --theme-border: #fff;
  --theme-bg1: #e0e0e0;
  --theme-bg2: #fff;
  --text-p0: #000;
  --text-p1: #111;
  --text-p2: #1f1f1f;
  --text-p3: #555;
  --text-code: #fff;
}
#ZYDark .tag-plugin[color='dark'] {
  --theme-border: #000;
  --theme-bg1: #1f1f1f;
  --theme-bg2: #111;
  --text-p0: #fff;
  --text-p1: #fff;
  --text-p2: #e0e0e0;
  --text-p3: #ddd;
  --text-code: #fff;
}
#ZYDark .tag-plugin[color='warning'],
#ZYDark .tag-plugin[color='light'] {
  --text-p0: #000;
  --text-p1: #111;
  --text-p2: #1f1f1f;
  --text-p3: #555;
  --text-code: #fff;
}
#ZYDark .social-wrap a.social:hover {
  box-shadow: none;
}

/* waline评论样式 */
#ZYDark .wl-count{
  padding: .375em;
  font-weight: bold;
  font-size: 1.25em;
  color: #fff;
}
#ZYDark .cmt-body.waline{
  --waline-white: #000;
  --waline-light-grey: #666;
  --waline-dark-grey: #999;
  /* 布局颜色 */

  --waline-color: #fff;
  --waline-bgcolor: var(--block);
  --waline-bgcolor-light: #272727;
  --waline-border-color: #333;
  --waline-disable-bgcolor: #444;
  --waline-disable-color: #272727;
  /* 特殊颜色 */
  --waline-bq-color: #272727;
  /* 其他颜色 */
  --waline-info-bgcolor: #272727;
  --waline-info-color: #666;
}
 
```

### 函数

复制以下代码并重命名为 ZYDark.js，放至本地路径/blog/source/custom/js 下。

```python
/**
 * 监听系统主题
 * @type {MediaQueryList}
 */
var OSTheme = window.matchMedia('(prefers-color-scheme: dark)');
OSTheme.addListener(e => {
    if (window.localStorage.getItem('ZYI_Theme_Mode') === 'Moss') {
        ThemeChange('Moss');
    }
})
/**
 * 修改博客主题
 * @param theme 亮为light,暗为dark,自动为auto
 * @constructor
 */
const ThemeChange = (theme) => {
    if (theme === 'light' || (theme === 'Moss' && !OSTheme.matches)) {
        document.querySelector("html").id = "ZYLight";
        document.querySelector("#start > aside > footer > div > a:nth-child(6)").style.filter= 'grayscale(0%)';
        document.querySelector("#start > aside > footer > div > a:nth-child(5)").style.filter= 'grayscale(100%)';
    } else {
        document.querySelector("html").id = "ZYDark";
        document.querySelector("#start > aside > footer > div > a:nth-child(5)").style.filter= 'grayscale(0%)';
        document.querySelector("#start > aside > footer > div > a:nth-child(6)").style.filter= 'grayscale(100%)';
    }
    if (theme==='Moss'){document.querySelector("#start > aside > footer > div > a:nth-child(7)").style.filter= 'grayscale(0%)';}
    else {document.querySelector("#start > aside > footer > div > a:nth-child(7)").style.filter= 'grayscale(100%)';}
    window.localStorage.setItem('ZYI_Theme_Mode', theme);
}
/**
 * 初始化博客主题
 */
switch (window.localStorage.getItem('ZYI_Theme_Mode')) {
    case 'light':
        ThemeChange('light');
        break;
    case 'dark':
        ThemeChange('dark');
        break;
    default:
        ThemeChange('Moss');
}
/**
 * 切换主题模式
 */
document.querySelector("#start > aside > footer > div > a:nth-child(5)").onclick = () => {
    ThemeChange('dark');
}
document.querySelector("#start > aside > footer > div > a:nth-child(6)").onclick = () => {
    ThemeChange('light');
}
document.querySelector("#start > aside > footer > div > a:nth-child(7)").onclick = () => {
    ThemeChange('Moss');
}

```

### 提前量

根目录/\_config.yml

```python
# 自定义引入css,js
inject:
  head:
    - |
      <script>
        if (window.localStorage.getItem('ZYI_Theme_Mode')==='dark' || (window.localStorage.getItem('ZYI_Theme_Mode')==='Moss' && window.matchMedia('(prefers-color-scheme: dark)').matches)){
            document.querySelector("html").id = "ZYDark";
        }
      </script>

```

### 引入样式与函数

博客目录/\_config.yml

```python
# 自定义引入css,js
inject:
  head:
    - <link rel="stylesheet" href="/custom/css/ZYDark.css"> # 黑夜样式
  script:
    - <script type="text/javascript" src="/custom/js/ZYDark.js"></script> # 黑夜控制
```

### 自定义博主配置

- `darkmode`用`false`意味对主题而言保持永远白昼(才有了我们的操作空间)
- 然后`footer.social`这部分我对应是 567, 懒得改 JS 的可以前面也加四个社交按钮.
- **博客目录/\_config.stellar.yml**

```python
style:
  darkmode: false # auto / always / false

# 页尾
footer:
  social:
   github:
     icon: '<img src="https://upyun.thatcdn.cn/public/img/icon/github-logo2.png"/>'
     url: https://github.com/ThatCoders
   music:
     icon: '<img src="https://upyun.thatcdn.cn/public/img/icon/neteasemusic-icon.png"/>'
     url: https://music.163.com/#/user/home?id=134968139
   bili:
     icon: '<img src="https://upyun.thatcdn.cn/public/img/icon/bilibili-icon.png"/>'
     url: https://space.bilibili.com/1664687779
   card:
     icon: '<img src="https://upyun.thatcdn.cn/public/img/icon/weChat.png"/>'
     url: https://muselink.cc/naive
   Moon:
     icon: '<img id="ThemeM" src="https://upyun.thatcdn.cn/public/img/icon/Moon.png"/>'
     url: javaScript:void('永夜');
   Sun:
     icon: '<img id="ThemeL" src="https://upyun.thatcdn.cn/public/img/icon/Sun.png"/>'
     url: javaScript:void('永昼');
   AI:
     icon: '<img id="ThemeAI" src="https://upyun.thatcdn.cn/public/img/icon/AI.png"/>'
     url: javaScript:void('跟随系统');
```

## 感谢

> 本文参考[钟意的博客](https://blog.thatcoder.cn/Stellar%E5%8F%AF%E6%8E%A7%E5%A4%9C%E9%97%B4%E6%A8%A1%E5%BC%8F/)。此文用于记录。在此感谢原作者。
