---
layout: wiki #layout 的值固定为wiki，与第二项一同作用于侧边栏，如果没有它们侧边栏也会消失
wiki: Build_self_networks # wiki 的值写你在source/_data/projects.yml中新增的项目名
title: Github Pages绑定域名 # 文章标题

---

域名绑定Github Pages，个人访问令牌认证。

<!-- more -->

{% quot 域名注册 el:h2  %}

1. 进入 [阿里云官网](https://www.aliyun.com/)，支付宝登录后，进入【**右上角"控制台"**】→【**左上角"域名"**】，来到**域名搜索页面**。

2. **注册阿里云域名**，目前新人 1 元购.com 域名，可按喜好购买 →[新人 1 元购活动入口](https://wanwang.aliyun.com/domain/1yuan?spm=5176.27906258.J_9945901770.functions-listName0-cardsRight0.5d903ec6Qax9Ku).

3. 新用户需要进行**实名认证**，在订单详情页有相关提示进行认证即可，一般 10 分钟内可审核通过。

4. 实名认证成功后，可直接**购买域名**，选择支付宝支付即可。

   恭喜你，现在起拥有了属于自己的域名。

{% quot 域名解析 el:h2  %}

- 当域名状态显示为 **正常** 时，开始进行 **域名解析**，点击右侧操作中的 **解析** 进入云解析 DNS 页面。

![](https://s2.loli.net/2023/10/23/4Ddfp63TJGXqiuA.png)

- 点击 **添加记录** ，添加**两条 CNAME 记录**，填写内容如下。

![](https://s2.loli.net/2023/10/23/mYqeWJukMzyAXPp.png)

这里解释下，需要新增两条主机记录@/www 的原因是，方便可以通过 [sumorio.com]()以及 [www.sumorio.com](www.sumorio.com) 两种形式对网站进行访问。

{% quot 域名绑定 el:h2  %}

前往[Github Page](https://github.com/Sumorio)已搭建好的仓库中，点击**settings**→ **page**→**Custom domain** 项中添加进行解析后的自定义域名。

![](https://s2.loli.net/2023/10/23/TFs2MjUiDelrC4h.png)

![](https://s2.loli.net/2023/10/23/vzqfuFiwBK7hg3m.png)

等待两分钟，DNS 认证成功后，即可使用新域名登录你的 github pages 网页。

{% quot 访问令牌Https el:h2  %}

### 阿里云申请 SSL 证书

- 进入[阿里云数字证书管理服务平台](https://yundunnext.console.aliyun.com/?spm=a2c4g.11186623.0.0.7dd455adjyWjhp&p=cas#/certExtend/buy/cn-hangzhou)
- 如图所示，**点击 SSL 证书 → 免费证书 → 立即购买 → 我同意**。申请免费证书数量。

![](https://s2.loli.net/2023/10/23/GrnJQwmguC4WYcN.png)

- 申请成功后，再次进入该页面，**点击 SSL 证书 → 免费证书 → 创建证书 → 申请证书 → 填写域名信息。** 提交审核并等待，一般秒批审核。

![](https://s2.loli.net/2023/10/23/aUiRPxer9ltopyH.png)

### Github 修改 CNAME

- Github 仓库的 cname 文件中新增一条指令：sumorio.com（不用加 https）

  ![](https://s2.loli.net/2023/10/23/ZyqGWuKosgcX9PU.png)

- Github 仓库的 settings→pages→ 勾选 Enforce HTTPS 。

![](https://s2.loli.net/2023/10/23/xejJzXoZapkwT64.png)

完。
