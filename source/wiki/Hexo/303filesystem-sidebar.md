---
layout: wiki #layout 的值固定为wiki，与第二项一同作用于侧边栏，如果没有它们侧边栏也会消失
wiki: Build_self_networks # wiki 的值写你在source/_data/projects.yml中新增的项目名
title: Stellar文档系统 | 侧边栏设置 # 文章标题

---

记录 Stellar 主题下的 wiki 文档系统的侧边栏设置。(1.20 后的版本已不支持)

<!-- more -->

{% box  color:yellow %}

**文档系统中有项目需要新增时，总共需要进行三个步骤：**

1.  ➡️ 配置`source/_data/projects.yml`.

2.  ➡️ 在`source/wiki/`目录下新建文件夹（名称随意），该目录下创建文章。

3.  ➡️ 配置`index.md`文件的头文件`front-matter`部分。

{% endbox %}

---

假设我们要创建一个名为“GPT 漫游”的新项目。
在这个项目中，我们将设置一个结构化的侧边栏，它将被分为四个主要部分：教程、工具、前线和其他。
这样的布局旨在为访问者提供清晰的导航，使他们可以轻松找到相关的文章和资源。

{% image https://s2.loli.net/2023/12/20/3ridsp7SJL2jBQF.png %}{% image https://s2.loli.net/2023/12/20/qPDFonVp5jle3Et.png %}

## 一. 配置 projects.yml

➡️ 配置`source/_data/projects.yml`。
➡️ `ChatGPT-File `为本次项目的 ID，可以随意起名，但是保证唯一。
➡️ Sections 相当于文档分类器，这里可以自行设置区间|自行命名，这将影响前端的侧边栏文字展示和文章归属。

```python
#专栏-Chatgpt
ChatGPT-File: #ID，用英文起名，随意起但是唯一
  title: GPT漫游 #wiki文档系统列表中的项目名称
  description: Hi，我是Sumorio。本文档致力于记录Chatgpt及其相关的一切。 #wiki文档系统列表中的项目介绍
  name: ChatGPT项目 #侧边栏左上角名称
  subtitle: "探索关于GPT的一切可能。| Designed by Sumorio。" #大标题下的小标题
  sidebar: [toc]
  tags: ChatGPT #项目标签
  logo:
    src: https://s2.loli.net/2023/10/20/tw8yrHvR31qfQm2.jpg #图片
    small: 120px
    large: 240px
  sections: #区间自行设置，保证区间不要重合
    "🏳️‍🌈ChatGPT教程": [100, 199]
    "🏳️‍🌈ChatGPT工具": [200, 299]
    "🏳️‍🌈ChatGPT前线": [300, 399]
    "🏳️‍🌈其他相关": [400, 499]
```

## 二. 新增文件

➡️ `source/wiki/`目录下新建文件夹 ChatGPT（名称随意），需要添加新文档时在该目录下创建文件。

{% image https://s2.loli.net/2023/12/20/hVDQfXiw2qoeLWa.png %}

## 三. 配置 front-matter

这里以文档 101test 为例：

➡️ 配置`index.md`文件的头文件`front-matter`部分。
➡️ order 的值用来对文章归类，想让文章归属哪个分类就把 ID 设置成相应值。
➡️ wiki 的值为 projects.yml 中项目的唯一 ID。
➡️ menu 见下文。

```python
layout: wiki #layout 的值固定为wiki，与第二项一同作用于侧边栏，如果没有它们侧边栏也会消失
wiki: ChatGPT-File # wiki 的值等于在source/_data/projects.yml中新增的项目ID名称（唯一）
title: 101test # 这里title的值就是页面最终呈现的折叠标签名
menu_id: wiki #与主题配置的menu_id一致,见下文

order: 101
# order的值的作用就是将它定义到上个步骤里创建的分组里。
# 上一步我在source/_data/projects.yml将[100,199]这个区间赋予给了【ChatGPT教程】，我这里的order的值是101。
# 101在100至199这个区间内，所以页面最终的效果就是把文章归类到【ChatGPT教程】这个分组，其他同样，只需要修改文章title和order的值。

breadcrumb: false
# 表示本页面不显示顶部导航，如果你需要显示的话，把这一行删除即可

comments: false
#表示本页面不启用评论版块，需要启用评论板块的话把值改成true
```

{% image https://s2.loli.net/2023/12/20/lU6jAcw3N8qPYnM.png %}

## 四. Menu_id

- Menu_id 位于配置文件`_config.stellar.yml`的`Sidebar`下的`menu`下，`post`,`wiki`,`more`,`friends`就是`menu_id`,在写文章时，我们需要在`front_matter`部分填写对应的`menu_id`.

- Stellar 同时具有博客和 Wiki 两个大模块，为了能够正确进行导航栏高亮，所以引入了`menu_id` 来进行区分，通常情况下，`layout: post` 和 `layout: wiki` 两种布局模板可以自动为 `sidebar.menu.post` 和 `sidebar.menu.wiki` 的导航栏按钮高亮。自己创建的独立页面也可以在 `front-matter` 中指定 `menu_id` 来使某个按钮处于选中状态。

{% image https://s2.loli.net/2023/12/20/GDcrtwW9ZH1Opl2.png %}
