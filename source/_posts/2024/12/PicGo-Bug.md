---
title: PicGo Bug "unable to verify the first certificate"
mathjax: true
matex: true
mermaid: true
tags:
  - Bug
  - PicGo
categories:
  - 技术乱炖
  - Bug修复
abbrlink: 5e927dfc
---

记录一次神奇的Bug：图床工具PicGo。

<!-- more -->

## 问题描述

在使用 `PicGo` 进行图片上传时，出现一个关于TLS证书验证的错误，log日志错误信息具体如下：

```
[PicGo ERROR] {
  "method": "PUT",
  "url": "https://api.github.com/repos/Sumorio/BlogPic/contents/douban-id.png",
  "statusCode": 0,
  "message": "unable to verify the first certificate",
  "stack": "Error: unable to verify the first certificate\n    at TLSSocket.onConnectSecure (node:_tls_wrap:1530:34)\n    at TLSSocket.emit (node:events:394:28)\n    at TLSSocket._finishInit (node:_tls_wrap:944:8)\n    at TLSWrap.ssl.onhandshakedone (node:_tls_wrap:725:12)",
  "response": {
    "status": 0,
    "statusCode": 0,
    "body": ""
  }
} 
```

第一次出现关于`TLSSocket`的问题，让人迷惑...

## 原因分析

查阅资料发现：

- 有的人为了可以顺利访问`github`用到`steam++`加速，steam++对用户有安装安全证书；
- 有的人为了可以顺利访问`github`用到`fastgithub`加速，同样有安装安全证书。

结论：出现bug的原因与网络加速工具有关，在使用`fastgithub`类似的加速工具时，可能引发一些网络通信问题（尤其涉及 `SSL` 证书验证），从而导致图床上传失败。

在网络通信中，`SSL` 证书是确保通信安全的关键组成部分。服务器使用 `SSL` 证书来证明其身份，并加密传输的数据，以防止第三方窃听或篡改。

当访问一个使用 `SSL`（或其继任者 `TLS`）加密的网站或服务时，浏览器会验证服务器的 `SSL` 证书，确保连接安全。

然而，某些网络加速工具可能会修改网络流量，甚至可能与 `SSL`证书验证机制发生冲突。

这可能导致 `SSL` 证书验证失败，因为服务器的证书无法正常验证，从而出现类似 `"unable to verify the first certificate"` 的错误。

## 解决方案

！！！！关闭`FastGithub` 类似的网络加速工具 ！！！

回到正常世界的感觉真好。



## 参考文件

[PIcGo官方FAQ](https://github.com/Molunerfinn/PicGo/blob/dev/FAQ.md)

