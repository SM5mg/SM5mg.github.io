---
title: NameSilo+CloudFlare+GitPages域名注册|域名解析
categories:
  - 技术乱炖
  - 技术分享
topic: tech
leftbar:
  - recent_topic_tech
  - recent
tags:
  - NameSilo
  - CloudFlare
abbrlink: 4812c2a7
---
域名注册，域名解析，Github 绑定多个域名。
<!-- more -->
如果图片加载缓慢或者裂开，需要打开魔法上网。

- 域名注册：[www.namesilo.com](https://www.namesilo.com)
- 域名解析：[www.cloudflare.com](https://www.cloudflare.com)

## 1)NameSilo|注册域名

1. 注册账号并登录:[namesilo](https://www.namesilo.com)

2. 输入自己心仪的域名，加入购物车。

{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240110154145.png %}

3. 右上角进入购物车，点击`view cart`；google 搜索”namesilo 优惠码“，找到并输入至`promotion code`中。地址可以随意填写，如果有需要，可以进入[地址生成网](https://www.dizhishengcheng.com/)随意生成并填入。结账方式可以选择【支付宝】。值得注意的是，该网页偶尔可能访问缓慢，不要着急，慢慢来。

{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240110154206.png %}

{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240110153533.png %}

{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240110155348.png %}

{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240110153634.png %}

4. 支付宝付款成功后，一分钟左右，跳转到后台页面，可以看到`dashboard`中的`Active domains`新增了一个账号。

{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240110153906.png %}

## 2)CloudFlare|托管域名

1. 注册账号并登录[www.cloudflare.com](https://www.cloudflare.com)

2. 将上文新注册的域名填写到 cloudflare 中.

   {% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240110163043.png %}

   {% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240110164522.png %}

3. 选择 free,continue,continue；来到更改服务器页面，复制红框中的 nameservers 地址到 namesilo 的域名设置中。

   {% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240110164639.png %}

   {% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240110164922.png %}

4. 点击返回到 Namesilo 网站进行域名设置：[域名设置网址](https://www.namesilo.com/account_domains.php),点击图中的金币按钮，如果没有这个按钮，可以等待大概 20 分钟后，新账号系统可能正在审核分配资源。

   {% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240110165035.png %}

5. 删除原始配置，将第 3 步 cloudflare 中的 namesevers 粘贴并提交。

   {% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240110165436.png %}

6. 显示 active ，表示域名已经成功托管到 cloudflare 平台进行管理。以后关于域名的设置都交给 cloudflare，可以不用登录 namesilo 了。

   {% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240110165655.png %}

7. 回到 cloudflare 平台，继续操作。

   {% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240110165840.png %}

   {% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240110165934.png %}

8. 回到 cloudflare 首页，查看域名更新状态，pending 为正在等待。一般审核的时间 2 分钟~24 小时不等，需要耐心等待。我大概等待 3 分钟后，域名生效为 active.

   {% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240110170111.png %}

   {% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240110171230.png %}

## 3)GithubPages|绑定自定义域名

登录 github 新建一个仓库，如果是第一次搭建 github pages 网页，命名一定要是`<username>.github.io`这种形式，username 就是自己[github](https://so.csdn.net/so/search?q=github&spm=1001.2101.3001.7020)账号的用户名（比如仓库名为 `sumorio.github.io`)，分支是 main 主分支。因为这是我的第二个网页，所以名称随意起，我这里仓库名为`Blog-Stellar`.

如图，新建好仓库后，进入 settings，page，选择分支并把注册好的域名填入，保存。

{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240111153131.png %}

保存之后 github 会`自动`的在仓库 CODE 根目录里生成一个`CNAME`文件，里面存储着域名配置信息。

{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240111153023.png %}

设置后继续返回 cloudflare 进行后续设置。

## 4)CloudFlare|设置 DNS/HTTPS

{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240111153621.png %}

{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240111115643.png %}

{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240111155428.png %}

{% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240111162455.png %}

以上设置完成，此刻可以通过域名进入网站。

**关于 Github Pages 设置中不能开启 `Enforce HTTPS`，勾选框一直无法点击的问题。大概率是 Cloudflare 的代理状态的造成的，解决方案如下`开启Encryption Full (strict) 严格模式`。**

## 5)开启 Encryption Full (strict) 模式

Full (strict) 模式与 Full 模式的区别在于: Full (strict) 模式使用的是由可信 CA 或 Cloudflare Origin CA 签名的有效证书并对每个请求验证证书，而非 Full 模式使用的无需验证的自签名证书。

GitHub Pages 可以通过开启 `Enforce HTTPS` 来获取免费的可信证书，满足开启 Full (strict) 模式的条件。

1. 在 Cloudflare 的 DNS 设置中把 Proxy status 全部设置为 `DNS Only` 状态，即灰色的云朵。

   {% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240111162646.png %}

2. 回到 Pages 设置，刷新一下，删除域名 Remove，重新填写，再 save，就可以勾选 `Enforce HTTPS` 了

   {% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240111163220.png %}

3. GitHub 会自动申请 SSL 证书，有了这个证书才能够在 Cloudflare 开启 Full (strict) 模式

4. 等待 Pages 的 HTTPS 生效后，回到 Cloudflare，把刚才修改的 Proxy status 全部恢复为 `Proxied` 状态，即橙色的云朵。

   {% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240111163517.png %}

5. 到 `SSL/TLS` 设置中，将 Encryption Mode 设置为 `Full (strict)`

   {% image https://cdn.jsdelivr.net/gh/Sumorio/BlogPic/20240111163553.png %}

## 6)科普：DNS 记录类型

**A 记录**

A 记录 (Address record) 是用来指定主机名（或域名）对应的 IP 地址记录。用户可以将该域名下的网站服务器指向到自己的网页服务器 (web server) 上。同时也可以设置域名的子域名。它会传回一个 32 位元的 IPv4 地址。

**AAAA 记录**

AAAA 记录 (AAAA record) 是用来将域名解析到 IPv6 地址的 DNS 记录。用户可以将一个域名解析到 IPv6 地址上，也可以将子域名解析到 IPv6 地址上。它会传回一个 128 位元的 IPv6 地址。

**CNAME 记录**

CNAME 记录 (Canonical Name Record)，用于将一个域名（同名）映射到另一个域名（真实名称），域名解析服务器遇到 CNAME 记录会以映射到的目标重新开始查询。CNAME 记录可用于 CDN 加速，通过 CDN 加速别名解析网站域名。

**NS 记录**

NS (Name Server) 记录是域名服务器记录，用来指定该域名由哪个 DNS 服务器来进行解析。如果需要把子域名交给其他 DNS 服务商解析，就需要添加 NS 记录。

**MX 记录**

MX (mail exchanger) 记录用于指定负责处理发往收件人域名的邮件服务器。

**TXT 记录**

TXT 记录一般指为某个主机名或域名设置的说明。

**TTL**

TTL (Time To Live) 表示解析记录在 DNS 服务器中的缓存时间，长度为秒。当本地 DNS 服务器收到某一域名的解析请求时，需要向该域名指定的权威 DNS 服务器发送解析请求获取解析记录。获得的解析记录会在本地 DNS 服务器中保存一段时间。在这段时间内，如果本地 DNS 服务器再次收到该域名的解析请求，将不再向权威 DNS 服务器发送解析请求，而是直接返回保存在本地 DNS 服务器中的解析记录。
