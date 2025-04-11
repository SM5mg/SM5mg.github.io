---
layout: wiki #layout 的值固定为wiki，与第二项一同作用于侧边栏，如果没有它们侧边栏也会消失
wiki: Build_self_networks # wiki 的值写你在source/_data/projects.yml中新增的项目名
title: Stellar动态友链 # 文章标题

---

记录 stellar 动态友链的详细设置过程。

<!-- more -->

## 一. Fork 仓库|开启 Issue&Action|开启读写权限

> `Github`仓库目录：https://github.com/xaoxuu/issues-json-generator/fork

- 具体操作：

1. 点击`fork`项目 ➡️ 名称设为`friends`➡️ 任务栏点击`settings`下滑到`issue`点击勾选`√`，此时任务栏出现`Issue`➡️ 点击任务栏`Aciton`，点击`i understand`。

{% image https://s2.loli.net/2023/12/20/fsOW3XbBQh6yTMw.png %}

{% image https://s2.loli.net/2023/12/20/e28zMvsrt9dUapn.png %}

{% image https://s2.loli.net/2023/12/20/dNrtYOCwivDqglR.png %}

2. ➡️ 点击任务栏`settings`，左侧选择`Action`下的【`General`】，下滑到【`Workflow Permissions`】，勾选读写权限**`Read and write permissions`** 。

{% image https://s2.loli.net/2023/12/20/1YOxsgmlvyGIqHz.png %}

## 二. 配置 Label 标签|修改 config.yml

1. 点击任务栏`Issue`➡️ 点击`Label`➡️ 删除现有标签，新增并保留以下四个标签：`active`、`suspend`、`404`、`checklist。`{% image https://s2.loli.net/2023/12/20/icsnMLmx2lykKgP.png %}
2. 点击任务栏【`code`】➡️ 点击进入`config.yml`文件，点击铅笔符号修改内容。{% image https://s2.loli.net/2023/12/20/4vRhy8wYdK632Ja.png %}{% image https://s2.loli.net/2023/12/20/xDRCIGMSFYcs532.png %}

## 三. 测试是否成功

1. 点击 `issue` ➡️`New issue`➡️ `Get Started`➡️ 填入你的基本信息，`label` 设置为 ``active`➡️`submit new issue`提交。

   {% image https://s2.loli.net/2023/12/20/13sm4ljxGReEAhv.png %}

   {% image https://s2.loli.net/2023/12/20/idQD9W271k6uNV8.png %}

   {% image https://s2.loli.net/2023/12/20/yzb95DMWFPvTqwn.png %}

2. 添加后，等待一会，点击任务栏【`code`】进入`output`分支，查看【v2】目录下的`data.json`文件，出现刚才新建的 issue 内容则设置成功。

   {% image https://s2.loli.net/2023/12/20/gykPRJtdrlbhq7a.png %}{% image https://s2.loli.net/2023/12/20/uxsEKUPFrQwG7vy.png %}

## 四. 具体使用

Stellar 作者原教程：[链接](https://xaoxuu.com/wiki/stellar/tag-plugins/data/#friends)
其他参考文章：[链接](https://zfe.space/post/python-issues-api.html)

在文档中直接引用写入以下代码即可：

```
{% friends
api:https://api.vlts.cc/output_data/v2/你的github用户名/你的github仓库名 %}
#示例： {% friends api:https://api.vlts.cc/output_data/v2/sumorio/friends %}
```
