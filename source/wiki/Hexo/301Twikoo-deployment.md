---
layout: wiki #layout 的值固定为wiki，与第二项一同作用于侧边栏，如果没有它们侧边栏也会消失
wiki: Build_self_networks # wiki 的值写你在source/_data/projects.yml中新增的项目名
title: Hexo-stellar部署twikoo评论系统 # 文章标题

---

Hexo 部署 twikoo 评论系统，邮件推送 versel，被墙导致无法评论的解决方案。

<!-- more -->

## 一、配置数据库

### 1.申请 MongoDB 账号

进入[MongoDB](https://www.mongodb.com/cloud/atlas/register)注册一个账号。可以使用 github 直接登录。

### 2.创建 MongoDB 数据库

**申请完毕后进入界面，选择最右边的免费共享数据库 ➡️aws➡️N.virginia(us-wast-1)➡️create.**
{% image https://s2.loli.net/2023/12/19/nxgDCrekU7fSjpa.png width:300px %}
**设置用户名和密码，记住密码，后面需要使用。**
{% image https://s2.loli.net/2023/12/19/IAW3bc56LsKTkrn.png width:300px %}
**ip 设置 0.0.0.0/0.**
{% image https://s2.loli.net/2023/12/19/8nfysaKSmiPw5HT.png width:300px %}
**自动跳转至数据库列表首页，点击 connect.**
{% image https://s2.loli.net/2023/12/19/cMDrEwBfZjk9bI3.png width:300px %}
**链接应用。**
{% image https://s2.loli.net/2023/12/19/knUNfsTL7AI8lrp.png width:300px %}

记住第 3 条的代码，后续部署需要用到，且使用时需要把 password 处替换你之前设置的密码。

```python
mongodb+srv://sumor:<password>@sumor0.kxmeq0a.mongodb.net/?retryWrites=true&w=majority
```

{% image https://s2.loli.net/2023/12/19/eLyvk8xQKwOCsIU.png width:300px %}

## 二、部署到 Vercel

### 1.申请账号

申请一个[Vercel](https://vercel.com/signup)账号.

### 2.部署仓库

点击[versel.com](https://vercel.com/import/project?template=https://github.com/imaegoo/twikoo/tree/main/src/server/vercel-min)链接将 Twikoo 一键部署到 Vercel：随便起个名→create.

> 注：如果导入后出现空白界面或部署失败等现象，极大可能是 Twikoo 的仓库地址更换了，可以参考官网获取部署链接：[官方部署文档](https://twikoo.js.org/quick-start.html)

{% image https://s2.loli.net/2023/12/19/7rlk6GMsBRzuQ3a.png width:300px %}

点击进入创建的任务页面-visit.

{% image https://s2.loli.net/2023/12/19/HOVdPq1LFrheZNo.png width:300px %}

### 3.新建变量

进入`Settings - Environment Variables`页面。
新建一个 NAME 为`MONGODB_URI`;VALUE 为你在前面记录到的`数据库连接字符串`的环境变量-save 保存。

**注意：需要手动输入`第二步`设置的密码，去掉<>，具体如：**

```
mongodb+srv://ambor0225:123456@cluster0.rx4....
```

{% image https://s2.loli.net/2023/12/19/SionGthvZdqjOa5.png  width:300px %}

### 4.再次部署

进入`Deployments`界面，点击右边的竖三点，点击`Redeploy`。

{% image https://s2.loli.net/2023/12/19/ZI1OKusy5kGd9jc.png width:300px %}

### 5.检验部署结果

回到`Overview`，点击 Domains 下方的链接，如果环境配置正确，可以看到 “Twikoo 云函数运行正常” 等字样。
{% image https://s2.loli.net/2023/12/19/AHb4YjiQfXVsz2t.png width:300px %}

> `Domains下方的链接`即为后面需要使用到的环境 id。

至此，Twikoo 评论系统部署完成。

## 三、实现邮件通知

### 1.开通[POP3](https://so.csdn.net/so/search?q=POP3&spm=1001.2101.3001.7020)/SMTP 服务

> 以网易为例，其他邮箱可自行摸索，原理大同小异。

前往你的邮件服务提供商，发短信开启 POP3/SMTP 服务-保存最后的授权密码，后面要用。

{% image https://s2.loli.net/2023/12/19/pEaOZoCqms5UXuF.png width:300px %}

{% image https://s2.loli.net/2023/12/19/POf2veCNIspaij7.png width:300px %}
 
{% image https://s2.loli.net/2023/12/19/p8YP2UvLSqX3Gck.png width:300px %}

## 四、配置 Twikoo

### 1.博客启用 Twikoo

> 此部分教程以 stellar 主题为例说明，其他主题可参阅对应的使用文档。

配置博客文件`_config.stellar.yml`，启用 twikoo 评论：（云函数位于 versel，domains 下的小地球后面）

```python
######## Comments ########
comments:
  service: twikoo

  # Twikoo
  # https://twikoo.js.org/
  twikoo:
    js: https://gcore.jsdelivr.net/npm/twikoo@1.6.8/dist/twikoo.all.min.js # 建议锁定版本
    envId: https://xx.xx.com # twikoo云函数,

```

{% image https://s2.loli.net/2023/12/19/agWGxcmizjR3FBP.png width:300px %}

重新启动服务，进入博客页面，随意找到一篇文章，查看最下方的评论处，找到评论下方小按钮。点击设置。

{% image https://s2.loli.net/2023/12/19/vNRFT7lD2HPh49i.png width:300px %}

{% image https://s2.loli.net/2023/12/19/jnBfEVOxcyeYzlH.png width:300px %}

【配置管理】-邮件通知：大部分不用填写，使用默认即可。下面几个必填。

> SENDER_EMAIL: <sumorio@126.com>
> SMTP_SERVICE: 126
> SMTP_PORT: 465
> SMTP_SECURE: true
> SMTP_USER: <邮件通知邮箱用户名>(需与 SENDER_EMAIL 一致)
> SMTP_PASS: (pop 授权码)

{% image https://s2.loli.net/2023/12/19/sQtg1DMxuF53jK9.png width:300px %}
{% image https://s2.loli.net/2023/12/19/RK15ysP2WBtzawY.png width:300px %}
{% image https://s2.loli.net/2023/12/19/wXECHos7ku9W5NF.png width:300px %}

其中`DEFAULT_GRAVATAR`参数可以设置评论默认使用的头像类型，头像区别如下：

{% image https://s2.loli.net/2023/12/19/ErteBbA3iRkHzXI.png width:300px %}

## 五、versel 版本不符升级配置

官方文档：https://twikoo.js.org/update.html

> 1. 进入 [Vercel 仪表板](https://vercel.com/dashboard) - twikoo - > Settings - Git
> 2. 点击 Connected Git Repository 下方的仓库地址
> 3. 打开 package.json，点击编辑
> 4. 将 `"twikoo-vercel": "latest"` 其中的 `latest` 修改为最新版本号。点> 击 Commit changes
> 5. 部署会自动触发，可以回到 [Vercel 仪表板](https://vercel.com/dashboard)，查看部署状态

## 六、解决 versel 被墙无法留言

1. 登录你的域名解析平台，我这里使用的阿里云-进入【域名解析】工作台-添加域名-twikoo+你的域名-txt 授权校验。

{% image https://s2.loli.net/2023/12/19/rPQOG16bdZaiVvC.png width:300px %}

2. 保存好弹出的验证记录信息，后面要用，先不要点击验证。

{% image https://s2.loli.net/2023/12/19/LEgAFNXW95n8ZHU.png width:300px %}

3. 进入【解析设置】界面，点击进入你的域名后台【添加记录】，将上一步的信息填入对应信息即可。
{% image https://s2.loli.net/2023/12/19/PJNRLQqxi41jZln.png width:300px %}

{% image https://s2.loli.net/2023/12/19/6PzFyjYoZs7wcnJ.png width:300px %}

4. 返回第 2 步，进行验证。

{% image https://s2.loli.net/2023/12/19/CfW18xyU9eEDu27.png width:300px %}

5. 进入新增的域名后台，将二级域名解析到 Vercel，新增两条记录。

   | 主机记录 | 记录类型 | 解析请求来源(isp) | 记录值               | TTL     |
   | -------- | -------- | ----------------- | -------------------- | ------- |
   | twikoo   | CNAME    | 默认              | cname.vercel-dns.com | 10 分钟 |
   | @        | A        | 默认              | 76.76.21.21          | 10 分钟 |

{% image https://s2.loli.net/2023/12/19/fj4HiFQMKwemAqh.png width:300px %}

{% image https://s2.loli.net/2023/12/19/3duG2m7o5T6xKy4.png width:300px %}

6. Vercel 项目中添加 Domains

进入【Project Settings】->【Domains】添加域名即可。

{% image https://s2.loli.net/2023/12/19/MyYCRzuIWdAqiro.png width:300px %}

7. 进入博客后台，替换主题配置文件的\_config.stellar.yml 以下内容中的 envid.

{% image https://s2.loli.net/2023/12/19/PVx8fF2dwupiUtG.png width:300px %}

最后的最后，要记得重新编译运行查看效果哦~

{% image https://s2.loli.net/2023/12/19/qcSUxyQVDBAK9eh.png width:300px %}
