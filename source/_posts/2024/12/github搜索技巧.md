---
title: Github的正确搜索姿势
tags:
  - Github
categories:
  - 技术乱炖
  - 技术分享
abbrlink: d4aaf8b4
---

敢说你会Github搜索。Github搜索技巧。
<!-- more -->

> GitHub 是全球最大的代码托管平台，掌握高效的搜索技巧对于开发者来说至关重要。本文将详细介绍 GitHub 的高级搜索技巧，帮助您更快地找到所需的代码、项目和议题。

## 普通搜索

普通人在搜索时，通常采用的方法：选择 most match,most star 的类目排序，随后选择相应的语言和仓库进行筛选。

{% image https://s2.loli.net/2023/12/18/eUDotLz6mGu7hnW.png %}

然而，这只是 google 搜索的冰山一角,下面几个方法可以让你掀开 github 搜索的神秘面纱。

## 高级搜索

### 查询大于或小于另一个值的值

| 查询语法 | 示例        | 描述                  |
| :------- | :---------- | :-------------------- |
| >        | stars:>1000 | 星标超过 1000 的仓库  |
| >=       | topics:>=5  | 至少有 5 个主题的仓库 |
| <        | size:<10000 | 小于 10KB 的文件      |
| <=       | stars:<=50  | 星标不超过 50 的仓库  |

### 查询范围之间的值

| 查询语法 | 示例         | 描述                       |
| :------- | :----------- | :------------------------- |
| n..n     | stars:10..50 | 星标在 10 到 50 之间的仓库 |

### 查询日期

| 查询语法                      | 示例                          | 描述                                    |
| :---------------------------- | :---------------------------- | :-------------------------------------- |
| created:>                     | created:>2016-04-29           | 2016 年 4 月 29 日之后**创建**的议题    |
| pushed:YYYY-MM-DD..YYYY-MM-DD | pushed:2016-04-30..2016-07-04 | 2016 年 4 月末到 7 月之间**推送**的仓库 |

### 排除特定结果

| 查询语法   | 示例                           | 描述                                 |
| :--------- | :----------------------------- | :----------------------------------- |
| NOT        | hello NOT world                | 含有"hello"但不含有"world"的仓库     |
| -QUALIFIER | stars:>10 -language:javascript | 超过 10 个星标且非 JavaScript 的仓库 |

### 对带有空格的查询使用引号

| 查询语法 | 示例            | 描述                    |
| :------- | :-------------- | :---------------------- |
| 使用引号 | label:"bug fix" | 具有"bug fix"标签的议题 |

### 使用用户名的查询

| 查询语法           | 示例           | 描述                      |
| :----------------- | :------------- | :------------------------ |
| QUALIFIER:USERNAME | author:sumorio | 由用户 sumorio 创作的提交 |

## 更高级的搜索

### 按仓库名称、说明或自述文件内容搜索

通过  `in`  限定符，您可以将搜索限制为仓库名称、仓库说明、自述文件内容或这些的任意组合。

如果省略此限定符，则只搜索仓库名称和说明。

| 查询语法       | 示例               | 描述                      |
| :------------- | :----------------- | :------------------------ |
| in:name        | vue in:name        | 名称中含有"vue"的仓库     |
| in:description | vue in:description | 说明中含有"vue"的仓库     |
| in:readme      | vue in:readme      | 自述文件中提及"vue"的仓库 |

### 在用户或组织的仓库内搜索

| 查询语法      | 示例                     | 描述                                 |
| :------------ | :----------------------- | :----------------------------------- |
| user:USERNAME | user:sumorio forks:>=100 | 用户 sumorio 拥有超过 100 复刻的仓库 |
| org:ORGNAME   | org:github               | GitHub 组织的仓库                    |

### 按仓库大小搜索

| 查询语法  | 示例            | 描述                               |
| :-------- | :-------------- | :--------------------------------- |
| size:n..n | size:1000..5000 | 大小在 1000KB 到 5000KB 之间的仓库 |

### 按关注者数量搜索

| 查询语法       | 示例             | 描述                             |
| :------------- | :--------------- | :------------------------------- |
| followers:n..n | followers:10..50 | 关注者数量在 10 到 50 之间的用户 |

### 按复刻数量搜索

| 查询语法   | 示例        | 描述                    |
| :--------- | :---------- | :---------------------- |
| forks:n..n | forks:>=100 | 至少有 100 次复刻的仓库 |

### 按星号数量搜索

| 查询语法   | 示例        | 描述                    |
| :--------- | :---------- | :---------------------- |
| stars:n..n | stars:>=500 | 至少有 500 个星标的仓库 |

### 按仓库创建或上次更新时间搜索

基于创建时间或上次更新时间过滤仓库。

- 对于仓库创建，使用  `created`  限定符；
- 了解仓库上次更新的时间，使用  `pushed`  限定符。 `pushed`  限定符将返回仓库列表，按仓库中任意分支上最近进行的提交排序。
  两者均采用日期作为参数。 日期格式  `YYYY-MM-DD`（年-月-日）。

| 查询语法                       | 示例                 | 描述                              |
| :----------------------------- | :------------------- | :-------------------------------- |
| created:YYYY-MM-DD..YYYY-MM-DD | created:>=2020-01-01 | 2020 年 1 月 1 日之后创建的仓库   |
| pushed:YYYY-MM-DD..YYYY-MM-DD  | pushed:<=2020-12-31  | 2020 年 12 月 31 日之前更新的仓库 |

### 按语言搜索

| 查询语法          | 示例                | 描述                       |
| :---------------- | :------------------ | :------------------------- |
| language:LANGUAGE | language:javascript | 使用 JavaScript 语言的仓库 |

### 按主题搜索

您可以查找归类为特定  [主题](https://docs.github.com/cn/free-pro-team@latest/articles/classifying-your-repository-with-topics)  的所有仓库。

| 查询语法    | 示例        | 描述              |
| :---------- | :---------- | :---------------- |
| topic:TOPIC | topic:react | 涉及 React 的仓库 |

### 按主题数量搜索

使用  `topics`  限定符以及  [大于、小于和范围限定符](https://docs.github.com/cn/free-pro-team@latest/articles/understanding-the-search-syntax)  按应用于仓库的  [主题](https://docs.github.com/cn/free-pro-team@latest/articles/classifying-your-repository-with-topics)  数量搜索仓库。

| 查询语法    | 示例       | 描述                  |
| :---------- | :--------- | :-------------------- |
| topics:n..n | topics:>=5 | 至少有 5 个主题的仓库 |

### 使用可视界面搜索

- 使用  [search](https://github.com/search) page 或  [advanced search](https://github.com/search/advanced) page 进行搜索。
- [advanced search](https://github.com/search/advanced) page 提供用于构建搜索查询的可视界面。
  按照条件因素进行过滤搜索，例如仓库具有的星标数或复刻数。 在填写高级搜索字段时，您的查询将在顶部搜索栏中自动构建。

| 查询语法             | 示例 | 描述                           |
| :------------------- | :--- | :----------------------------- |
| 使用 GitHub 搜索界面 | -    | 通过 GitHub 的可视界面进行搜索 |

### 按许可搜索

按其[许可](https://docs.github.com/cn/free-pro-team@latest/articles/licensing-a-repository)搜索仓库。 必须使用[许可关键词](https://docs.github.com/cn/free-pro-team@latest/articles/licensing-a-repository/#searching-github-by-license-type)按特定许可或许可系列过滤仓库。

| 查询语法        | 示例        | 描述                |
| :-------------- | :---------- | :------------------ |
| license:LICENSE | license:mit | 使用 MIT 许可的仓库 |

### 按公共或私有仓库搜索

您可以基于仓库是公共还是私有来过滤搜索。

| 查询语法                | 示例       | 描述     |
| :---------------------- | :--------- | :------- |
| is:public 或 is:private | is:private | 私有仓库 |

### 按照是否镜像搜索

您可以根据仓库是否为镜像以及托管于其他位置托管来搜索它们。

| 限定符                      | 示例                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | 描述                            |
| :-------------------------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :------------------------------ |
| mirror:true 或 mirror:false | [m](https://github.com/search?utf8=%E2%9C%93&q=mirror%3Atrue+GNOME&type=)[i](https://github.com/search?utf8=%E2%9C%93&q=mirror%3Atrue+GNOME&type=)[rror](https://github.com/search?utf8=%E2%9C%93&q=mirror%3Atrue+GNOME&type=)[:t](https://github.com/search?utf8=%E2%9C%93&q=mirror%3Atrue+GNOME&type=)[ru](https://github.com/search?utf8=%E2%9C%93&q=mirror%3Atrue+GNOME&type=)[e](https://github.com/search?utf8=%E2%9C%93&q=mirror%3Atrue+GNOME&type=)[ GNOME](https://github.com/search?utf8=%E2%9C%93&q=mirror%3Atrue+GNOME&type=) | 镜像且包含 "GNOME" 字样的仓库。 |

### 基于仓库是否已存档搜索

基于仓库是否[已存档](https://docs.github.com/cn/free-pro-team@latest/articles/about-archiving-repositories)来搜索仓库。

| 查询语法                        | 示例           | 描述         |
| :------------------------------ | :------------- | :----------- |
| archived:true 或 archived:false | archived:false | 未存档的仓库 |

## 基于具有 good first issue 或 help wanted 标签的议题数量搜索

使用限定符  `help-wanted-issues:>n`  和  `good-first-issues:>n`  搜索具有最少数量标签为  `help-wanted`  或  `good-first-issue`  议题的仓库。

| 查询语法                | 示例                   | 描述                                   |
| :---------------------- | :--------------------- | :------------------------------------- |
| good-first-issues:n..n  | good-first-issues:>=1  | 至少有 1 个 good first issue 的仓库    |
| help-wanted-issues:n..n | help-wanted-issues:>=1 | 至少有 1 个 help wanted 的仓库<br><br> |

