---
layout: wiki #layout 的值固定为wiki，与第二项一同作用于侧边栏，如果没有它们侧边栏也会消失
wiki: Build_self_networks # wiki 的值写你在source/_data/projects.yml中新增的项目名
title: Github Pages托管静态页面 # 文章标题

---

> [GiHub Pages 入门——官方文档](https://docs.github.com/zh/pages/quickstart#introduction)

## 一、新建仓库

1. 在 GitHub 任何页面的右上角，选择  ，然后单击“新建存储库”。
2. 创建一个仓库，仓库名和 github 用户名保持一致：用户名.github.io。

## 二、配置 SSH 密钥

只有配置好密钥，才能通过 git 操作实现本地代码与 Github 代码库的同步。

1. 进入最初新建的文件夹 D:/Hexo/blog
2. 右键打开 Git Bash Here，输入命令后，回车三次

```python
ssh-keygen -t rsa -C "你的邮箱地址" #如"88888@qq.com
```

3. 进入 C 盘 users/用户名文件夹/.ssh 文件夹，其中有 2 个文件夹：
   1. id_rsa 是这台电脑的私人密钥；
   2. id_rsa.pub 是公共密钥。
4. 复制 id_rsa.pub 中的内容粘贴到 github 的 SSH 中

## 三、GitHub 新增 SSH

1. 点击右上角 Github 信息 ➡️ 点击设置 ➡️ 左侧栏 SSH and GPG keys➡️ 新增 SSHkeys
2. title 随便起个名字，将第二步复制的 rsa 密钥复制到这里
3. 在 Git Bash Here 中输入命令，显示 successful 成功。

```python
ssh -T git@github.com
```

## 四、修改配置

1. 打开 github 的同名仓库，点击 code➡️SSH➡️ 复制
2. 将复制的链接加入本地\_config.yml 文件中，参考如下：

```python
deploy:
  # 类型
  type: git
  # 部署分支名称，按照自己喜欢的起名就可以。这里写完还需要在 GitHub 上进行分支创建并配置
  branch: main
  # 仓库，这里使用的 SSH 方式
  repo: git@github.com:***/***.github.io.git #这里填第2步中复制的内容
  # 如果你看了 hexo 的文档，这里很清楚。部署的时候会使用这个消息作为提交的信息
  message: Automatic deploy by Github Action：{{ now('YYYY-MM-DD HH:mm:ss') }}
```

## 五、更新提交

输入下面的命令，本地文件会自动更新提交到 github 上。

```python
hexo c
hexo g #自动生成上传的文件
hexo d #上传git
```

如果输入指令报错`not found git`，可以先下载安装插件。

```
npm install hexo-deployer-git --save
```

{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240111104231.png %}
