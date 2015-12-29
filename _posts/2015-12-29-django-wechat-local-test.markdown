---
layout: post
title:  "本地测试微信开发--ngrok内网穿透利器"
date:   2015-12-29 17:00
categories: django
tags:   django开发 微信开发
---
微信公众号开发, 要面临的一个问题就是, 后台代码需要有外网ip, 因为需要和微信服务器交互, 所以没法像写其他django程序一样, 利用自带服务器进行调试. 可以每写完程序都部署到自己使用的服务器上, 但是这样太过蛋疼, 毕竟调试程序太频繁了. 对应的一种解决方法就是, 将本地映射到公网ip, 利用此类软件, 比较有名的就是ngrok, 一种反向代理, 通过在公共的端点和本地运行的web服务器之间建立一个安全的通道.通过运行ngrok, 通过ngrok分配的域名在外网访问到自己本地服务器上的程序.详细介绍可以自行查看[ngrok官网][ngrok官网].

但是由于ngrok已经被墙, 之后出现了一个ngrok国内版[tunnel][tunnel], 但是也已经被墙掉了. 然而广大网友不乏好人, 有人自己架设ngrok服务供大家使用, 我找到了一个[qydev][qydev], 用着还可以. 具体使用方法网站主页上都由给出.

这样就可以实现本地调试微信开发了.


[ngrok官网]:    https://ngrock.com
[tunnel]:       http://tunnel.mobi
[qydev]:        http://qydev.com
