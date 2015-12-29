---
layout: post
title:  "接入微信公众平台"
date:   2015-12-29 21:10
categories: django
tags:   django开发 微信开发
---

#### 1.填写服务器基本配置
接入微信公众平台, 首先需要在"基本配置"中配置服务器, url我使用的是利用ngrok之后生成的域名, token自己随意设置, EncodingAESKey随机生成即可. 消息加密方式, 由于不太熟悉, 所以暂时选择了明文模式.

#### 2.验证服务器url的有效性
开发者文档中的接入指南上解释, 提交服务器基本配置后, 微信后台服务器会向填写的url发送一个GET请求, 请求中会携带四个参数:

* signature:  微信服务器结合开发者提交的token, 以及GET请求中的timestamp, nonce参数通过sha1加密之后生成的签名, 用于开发者在服务器后台根据参数生成sha1加密字符串来比对, 从而进行确认GET请求是否来自微信公众平台.
* timstamp: 时间戳, GET请求中的参数, 用于开发者生成加密字符串.
* nonce:    随机数, 作用同timestamp.
* echostr:  随机字符串, 用于在后台确认后, 返回给微信公众平台, 来完成服务器验证.

#### 3.views中验证signature的代码
{% highlight python %}
import hashlib

from django.http import HttpResponse
from django.shortcuts import render

def index(request):
    if request.method == 'GET':
        signature = request.GET.get('signature')
        timestamp = request.GET.get('timestamp')
        nonce = request.GET.get('nonce')
        echostr = request.GET.get('echostr')

        token = '*****'
        args = [token, timestamp, nonce]
        args.sort()
        encrypt_signature = hashlib.sha1(args[0] + args[1] + args[2]).hexdigest()

        if signature == encrypt_signature:
            return HttpResponse(echostr)

{% endhighlight %}
通过request.GET.中提供的接口, 获取对应的四个参数, 开发着自己要利用token, timestamp和nonce生成一个加密签名, 将此三个参数的值按字典序排序后, 生成一个字符串, 我利用python自带的hashlib对字符串进行了sha1加密, 加密之后需调用hash对象的hexdigest()将加密内容转为字符串. 如果生成的加密字符串encrypt_signature和signature一致, 就将echostr放入HttpResponse中返回, 将echostr简单的返回即可. 使用复杂点的方式有可能导致微信公众平台服务器接收不到正确的echostr, 使得token验证失败.
