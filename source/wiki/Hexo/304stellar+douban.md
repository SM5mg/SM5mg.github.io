---
layout: wiki #layout 的值固定为wiki，与第二项一同作用于侧边栏，如果没有它们侧边栏也会消失
wiki: Build_self_networks # wiki 的值写你在source/_data/projects.yml中新增的项目名
title: Hexo-Stellar配置豆瓣观影记录
---

引入**hexo-douban**插件，实现在个人博客展示豆瓣电影评论、书评、音乐评论等。

<!-- more -->

## 获取豆瓣ID

进入豆瓣主页——打开【我的广播】——鼠标右键点击检查进入【开发者模式】——鼠标任意点击一个广播条目——在开发者后台中找到`data-uid`字段，就是豆瓣用户ID-纯数字。

{%image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/douban-id.png %}

##  安装插件

在`Git Bash`客户端中运行命令：
{% copy npm install hexo-douban --save prefix:$ %}

## 配置

将下面的配置写入站点的配置文件 `_config.yml` . (不是主题的配置文件).

```_config.yml
douban:
  id: 改成你的ID  #这个需要修改为你个人的id
  dynamic: false
  item_per_page: 30
  meta_max_line: 5
  customize_layout: page
  builtin: true   #如果想生成豆瓣页面，这个需要设置为true
  movie:
    title: '豆瓣观影'
    quote: '电影是第一个让人类知道自己是谁的艺术。'
    path: /movie/index.html #生成的网页路径，定义成你自己的路径
  book:
    title: '豆瓣阅读'
    quote: '读书忌死读，死读钻牛角。'
    path: /book/index.html #生成的网页路径，定义成你自己的路径
  timeout: 10000
```

## 使用

### 显示帮助文档

在`Git Bash`客户端中运行命令：

`hexo douban -h`

>  注释：选择自己需要的参数即可
>   -b, --books   Generate douban books only 书
>   -g, --games   Generate douban games only 游戏
>   -m, --movies  Generate douban movies only 电影
>   -s, --songs   Generate douban songs only 音乐

### 启动生成

在`Git Bash`客户端中运行命令：
{% copy hexo clean && hexo douban -bm && hexo g && hexo s prefix:$ %}

为了展示这里用`-bm`，仅生成书和影的页面。如果不加参数，那么默认参数为`-bgms`，生成四个页面。

### 测试访问

如果上面的配置都没有问题，就可以使用`localhost:4000`+`你设置的网页地址`，浏览器访问网址，可以访问代表设置成功。

```ip
http://localhost:4000/book/
http://localhost:4000/movie/
```

## 部署

如果你是`hexo-stellar`主题，可以在`_config.stellar.yml`文件中配置菜单链接，展示豆瓣电影和书籍的页面。

```
# 侧边栏主功能导航菜单
menubar:
  columns: 5 # 一行多少个
  items: # 可按照自己需求增加，符合以下格式即可
    - id: movie
      theme: '#1e6150'
      icon: solar:documents-bold-duotone
      title: Movie
      url: /movie/
      ...
```

## 其他

**需要注意的是**，通常大家都喜欢用`hexo d`来作为`hexo deploy`命令的简化，但是当安装了`hexo douban`之后，就不能用`hexo d`了，因为`hexo douban`跟`hexo deploy` 的前缀都是`hexo d`。

第一次使用` hexo douban` 时，后台会异步进行数据获取，一般需要等待一段时间（后台访问你的标记页面）才能查到数据。顺利情况下，平均一个页面会花 10s。

后续如果你的豆瓣数据更新了，`hexo douban` 同样也会自动进行更新（同样需要等待一段时间才会查到更新数据），不过出于安全考虑，一个用户 id**每半小时至多只会同步一次**。

由于豆瓣本身深分页的 RT 过高（上万条目的翻页 RT 会到 15s 到 60s），为了防止系统同步压力过大，每个用户的每一类条目最多只会同步 1w 条。

如果 dynamic 设置为 true，则每次访问页面时都会向后端自动发起更新请求，无需手动执行 `hexo douban `命令。



## 官方文档

[hexo-douban](https://github.com/mythsman/hexo-douban)
