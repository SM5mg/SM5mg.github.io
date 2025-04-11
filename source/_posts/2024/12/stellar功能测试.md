---
title: Stellar新功能测试
mathjax: true
matex: true
mermaid: true
tags:
  - Hexo
  - 功能测试
categories:
  - 技术乱炖
  - 技术杂谈
abbrlink: e48f9054
---

自用，新功能测试

<!-- more -->

## 组件库

### note

{% note color:yellow  测试折叠容器功能，特选择几则脑筋急转弯，仅供娱乐。 %}

```javascript 
{% note color:yellow  测试折叠容器功能，特选择几则脑筋急转弯，仅供娱乐。 %}
```

### quot

{% quot 脑筋急转弯  icon:hashtag   %}

```js 
{% quot 脑筋急转弯  icon:hashtag el:h2  %}
```

### folders

{% folders %}

<!-- folder 吃饭时停电为什么扒拉两口饭灯就会亮？ -->

因为巴啦啦能量。

<!-- folder 小王剪了中分会变成什么？-->

小全

<!-- folder 狐狸为什么站不起来？-->

因为他狡猾(脚滑)/骚断腿

<!-- folder 许仙给老婆买了一顶帽子，白娘子戴上之后，为什么感觉头特别重? -->

因为那是鸭舌帽

<!-- folder 青蛙吃了什么就会变哑巴?-->

南瓜(难呱)

{% endfolders %}

```js 
{% folders折叠容器 %}
<!-- folder 吃饭时停电为什么扒拉两口饭灯就会亮？ -->
{% endfolders %}
```

### emoji

```js 
{% emoji blobcat ablobcatrainbow height:2em %} 你猜对了吗？
```

{% emoji blobcat ablobcatrainbow height:2em %} 你猜对了吗？

### hashtag

{% hashtag 苏末了 https://sumorio.com  color:green %}

```js 
{% hashtag 苏末了 https://sumorio.com  color:green %}
```

### image

{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/wolframlanguage.png 阳光明媚 width:300px   padding:10px  download:href  bg:#393E46 %}

```js  
{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/wolframlanguage.png 阳光明媚 width:300px   padding:10px  download:href  bg:#e0ebe4 %}
```

### icons.yml

```
{% quot prefix:solar:planet-bold-duotone 这是一个 icons.yml 配置的示例 %}

{% quot prefix:https://api.iconify.design/line-md:moon-alt-to-sunny-outline-loop-transition.svg 这是一个 url 的示例 suffix:https://api.iconify.design/solar:list-heart-minimalistic-line-duotone.svg %}
```

{% quot prefix:solar:planet-bold-duotone 这是一个 icons.yml 配置的示例 %}

{% quot prefix:https://api.iconify.design/line-md:moon-alt-to-sunny-outline-loop-transition.svg 这是一个 url 的示例 suffix:https://api.iconify.design/solar:list-heart-minimalistic-line-duotone.svg %}

### button

{% button 探索 /explore/  icon:solar:planet-bold-duotone size:xs  %}

{% button 探索 /explore/    icon:solar:planet-bold-duotone   %}

```js 
{% button 探索 https://github.com/xaoxuu/hexo-theme-stellar/ icon:solar:planet-bold-duotone size:xs  %}
{% button 探索 https://github.com/xaoxuu/hexo-theme-stellar/ icon:solar:planet-bold-duotone   %}
```

### OKR

{% okr o1 %}

2024年的小目标：完成 Volantis 6.0 并发布上线
来自2025年的复盘：已《基本》实现目标 {% emoji tieba 滑稽 %}

<!-- okr kr1 percent:1 -->
重构 tag-plugins 和 wiki 系统

- 当 {% mark KR %} 进度为 100% 时，标签默认显示为 {% mark color:green 已完成 %}
- 当 {% mark KR %} 未设置进度时，默认为 {% mark 0% %}
- 当 {% mark O %} 未设置进度时，则显示所有 {% mark KR %} 进度平均值

<!-- okr kr2 percent:0.9 status:off_track -->
完成主要页面设计稿
{% tabs align:left %}
<!-- tab 小提示1 -->
您可以在 _config.yml 文件中修改标签的颜色和文案
<!-- tab 小提示2 -->
您可以在 _config.yml 文件中增加任意的标签配置
{% endtabs %}

<!-- okr kr3 percent:-0.12 status:unfinished -->
完成前置准备工作（如果你知道答案，请在留言区帮帮我！🥹）
{% checkbox 在咸水和海滩之间找一亩地 %}
{% checkbox 求出圆周率后15位 %}
{% checkbox 找出宇宙的终极逻辑 %}
{% checkbox 去地狱里走两步 %}

<!-- okr kr-4 status:at_risk -->
开发、测试和发布
{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/Hudi.png   height:64px 支持嵌套插入图片等其它简单组件 %}

{% endokr %}


{% quot OKR目标计划 %}

{% okr o1  %}

学无止境，每年至少完成两个兴趣爱好的挖掘和开拓，同时产出该爱好相关的作品。

<!-- okr kr1 percent:0.5 status:at_risk -->

个人博客：完成因版本更新导致的遗留问题和历史版本迁移

1.  {% mark color:yellow **旧界面重构** %}: 每次主题更新，更改时间周期不超过 5Days。

2.  {% mark color:yellow **新内容更新** %}：在保持日常更新频率的同时，完成其余板块的更新

- 完成 wiki-系统、笔记-模块、about 界面的配置更新|内容重组|界面美化。

- 完成 chatgpt 板块完善、前端板块持续输出不少于 10 篇。

<!-- okr kr2 percent:0.2 status:unfinished -->

个人技能：持续学习全栈开发，全面提升个人技术能力。

1.  {% mark color:blue **前端** %}：完成学习并完成个人网页的开发。
2.  {% mark color:blue **后端** %}：与前端联合，完成一个自动化网页商城的搭建。

<!-- okr kr3 percent:0 status:unfinished -->

娱乐活动：学习数位板的使用，搭配 blender 模型设计并完成一个人物建模。

{% endokr %}

###  Copy

{% copy curl -s https://sh.xaox.cc/install | sh %}
{% copy curl -s https://sh.xaox.cc/install | sh prefix:$ %}
{% copy git:https xaoxuu.com/hexo-theme-stellar %}
{% copy git:ssh xaoxuu.com/hexo-theme-stellar %}
{% copy git:gh xaoxuu.com/hexo-theme-stellar %}

```js 
{% copy curl -s https://sh.xaox.cc/install | sh %}
{% copy curl -s https://sh.xaox.cc/install | sh prefix:$ %}
{% copy git:https xaoxuu.com/hexo-theme-stellar %}
{% copy git:ssh xaoxuu.com/hexo-theme-stellar %}
{% copy git:gh xaoxuu.com/hexo-theme-stellar %}
```

### radio

{% radio 没有勾选的单选框 color:purple %}
{% radio checked:true 已勾选的单选框  color:red %}

```js 
{% radio 没有勾选的单选框 color:purple %}
{% radio checked:true 已勾选的单选框  color:red %}
```

### checkbox

{% checkbox 普通的没有勾选的复选框 %}
{% checkbox checked:true 普通的已勾选的复选框 %}
{% checkbox symbol:plus color:green checked:true 显示为加号的绿色的已勾选的复选框 %}
{% checkbox symbol:minus color:yellow checked:true 显示为减号的黄色的已勾选的复选框 %}
{% checkbox symbol:times color:red checked:true 显示为乘号的红色的已勾选的复选框 %}

```js 
{% checkbox 普通的没有勾选的复选框 %}
{% checkbox checked:true 普通的已勾选的复选框 %}
{% checkbox symbol:plus color:green checked:true 显示为加号的绿色的已勾选的复选框 %}
{% checkbox symbol:minus color:yellow checked:true 显示为减号的黄色的已勾选的复选框 %}
{% checkbox symbol:times color:red checked:true 显示为乘号的红色的已勾选的复选框 %}
```

### audio

{% audio netease:109485 %}

{% audio type:0 netease:6938689445 autoplay:0 %}

```js 
{% audio https://github.com/volantis-x/volantis-docs/releases/download/assets/Lumia1020.mp3 %}

{% audio netease:109485 %}

{% audio type:0 netease:6938689445  autoplay:0 %}
```

### video

{% video bilibili:BV1NV4y1L79y width:100% autoplay:0 %}

{% grid c:2 %}
<!-- cell -->
{% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov %}
<!-- cell -->
{% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov width:100% %}
{% endgrid %}

### navbar

{% navbar active:/wiki/  [博客文章](/)  [项目](/wiki/)  [专栏](/topic/) [朋友圈&留言板](#comments)  [自我介绍](/about/) [GitHub](https://github.com/xaoxuu/) %}
```js  
{% navbar active:/wiki/  [博客文章](/)  [项目](/wiki/)  [专栏](/topic/) [朋友圈&留言板](#comments)  [自我介绍](/about/) [GitHub](https://github.com/xaoxuu/) %}
```

### psw/u/emp/wavy/del/sup/sub/kbd

> 这是 {% psw 密码 %} 标签
>
> 这是 {% u 下划线 %} 标签
>
> 这是 {% emp 着重号 %} 标签
>
> 这是 {% wavy 波浪线 %} 标签
>
> 这是 {% del 删除线 %} 标签
>
> 这是 {% sup 上角标 color:red %} 标签
>
> 这是 {% sub 下角标 %} 标签
>
> 这是 {% kbd 键盘样式 %} 标签，试一试：{% kbd ⌘ %} + {% kbd D %}

```js 
- 这是 {% psw 密码 %} 标签
- 这是 {% u 下划线 %} 标签
- 这是 {% emp 着重号 %} 标签
- 这是 {% wavy 波浪线 %} 标签
- 这是 {% del 删除线 %} 标签
- 这是 {% sup 上角标 color:red %} 标签
- 这是 {% sub 下角标 %} 标签
- 这是 {% kbd 键盘样式 %} 标签，试一试：{% kbd ⌘ %} + {% kbd D %}
```

## Timeline时间线

{% timeline %}
<!-- node 2024 年 1 月 1 日 -->
新年快乐。🐾😸
{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/my_boy.png  width:50px %}
<!-- node 2024 年 2 月 6 日 -->
回家过年，新的一年，新的成长。

<!-- node 2024 年 12 月 12 日 -->

这是一个预言说说。🈲

{% endtimeline %}

## 在目录树中隐藏某篇文章

可以在 `front-matter` 中不设置 `title` 标题，或者将 `title` 改为 `seo_title`。

```js /blog/source/xxx/xxx.md
title: ''
seo_title:标题
```

## ghcard 卡片

{% ghcard sumorio %}
{% ghcard sumorio/sumorio.github.io  theme:dark %}

```
{% ghcard sumorio %}
{% ghcard sumorio/sumorio.github.io  theme:dark %}
```



## Tabs 分栏器

{% tabs active:2 align:center %}

<!-- tab 图片test -->
{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/friend_boy.png width:60px %}

<!-- tab 代码块test -->

```swift
let x = 123
print("hello world")
```

<!-- tab 文字test -->
这是一个测试。Test it 😸🐾

{% endtabs %}

## grid 网格分区容器

{% grid bg:card c:4 br:9px w:150px gap:6px %}
<!-- cell -->
阿尔贝·加缪（1913—1960年），法国声名卓著的小说家、散文家和剧作家，存在主义文学大师，“荒诞哲学”的代表人物。
<!-- cell -->
不要走在我后面，因为我可能不会引路；不要走在我前面，因为我可能不会跟随；请走在我的身边，做我的朋友。
<!-- cell -->
我们很少信任比我们好的人，宁肯避免与他们来往。相反，我们常对与我们相似、和我们有着共同弱点的人吐露心迹。我们并不希望改掉弱点，只希望受到怜悯与鼓励。
<!-- cell -->
真正的救赎，并不是厮杀后的胜利，而是能在苦难之中找到生的力量和心的安宁。
{% endgrid %}

## swiper 轮播容器

默认一张图片是 50% 宽度，通过设置 `width:min` 设置为 25% 宽度，`width:max` 设置为 100% 宽度。effect:cards/coverflow.

{% swiper effect:coverflow width:min %}
![1](https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/my_boy.png)
![2](https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/friend_boy.png)
![3](https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/-puzzle.png)
![4](https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240113180018.png)
{% endswiper %}


```
{% swiper effect:cards %}
![](https://images.unsplash.com/photo-1625171515821-1870deb2743b?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=774&q=80)
![](https://images.unsplash.com/photo-1528283648649-33347faa5d9e?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=774&q=80)
![](https://images.unsplash.com/photo-1542272201-b1ca555f8505?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=774&q=80)
![](https://images.unsplash.com/photo-1524797905120-92940d3a18d6?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=774&q=80)
{% endswiper %}
```

## katex 插件

$$\sum_{i=0}^n i^2 = \frac{(n^2+n)(2n+1)}{6}$$

## mathjax 插件

$$\sum_{i=0}^n i^2 = \frac{(n^2+n)(2n+1)}{6}$$

## 图表类插件

```mermaid
graph LR
A(打开冰箱) -->|拿出大象| B(把大象装冰箱)
B -->|安抚大象情绪| C(关闭冰箱)
```


```mermaid
journey
    title My working day
    section Go to work
      Make tea: 5: Me
      Go upstairs: 3: Me
      Do work: 1: Me, Cat
    section Go home
      Go downstairs: 5: Me
      Sit down: 5: Me
```

## Post文章问题

### 文章如何置顶？

在`front-matter`配置`sticky: 数字序号`。



### 删除顶部导航

在`front-matter`配置`breadcrumb: false`



### 不显示文章标题

在`front-matter`配置`h1: ''` 将一级标题置空。


## paper标签
{% paper under_line title:单影只人 author:且听风吟 footer:留言 date:2023.09.08 %}
<!-- line left-->
见字如面。
<!-- line right-->
见字如面。
<!-- paragraph -->
心是一座孤岛，即便岛上繁花似锦，四季更替，依然只是一个人的风景。繁华也好，萧条也好，都只属于一个人。记得有人说过这样一句话：一人花开，一人花落，这些年从头到尾，无人问询。那种寥落，如轩窗外的一片月色，独自在树梢起舞，却无人欣赏它清丽的舞姿。又像是一阙小词，笔笔皆清冷，笔笔皆寂寥。
<!-- section 抓到一名同学 -->
欢迎留言哦！
<!-- paragraph -->
好的，一定会的！
{% endpaper %}

{% paper title:一些喜欢的文字 author: footer:祝君好 date: %}
<!-- line left--> 
❄️字迹已经模糊,因为思念的缘故.
❄️我从没被谁知道,所以也没被谁忘记.在别人的回忆中生活,并不是我的目的.
❄️画下丘陵——长满淡淡的茸毛,我让它们挨得很近,让它们相爱,让每一个默许,每一阵静静的春天的激动,都成为一朵小花的生日.
❄️树枝想去撕裂天空,却只戳了几个微小的窟窿,它透出了天外的光亮,人们把它叫做月亮和星星.
❄️种子在冻土里梦想春天。
❄️路是这样窄吗？只是一脉田埂。拥攘而沉默的苜蓿，禁止并肩而行。如果你跟我走，你会数我的脚印；如果我随你去，只能看你的背影。

>
❄️人生两件幸事，思想自由，行动自由。 
❄️唯有承认了孤独的必然，才能享受不从众的自在，有多少孤独就有多少真实。 
❄️一个人能够追求的最高理想就是自我的完善。 
❄️一颗石子扔到河里，整个宇宙就会变得和原来不同。 
❄️你终究会成为你正在成为的人，你的每一个选择都是来自你人生意义的诘问。 
❄️剃刀锋利，越之不易；智者有云，得渡人稀。 
{% endpaper %}

