---
layout: post
title:  "将django服务器在80端口上运行"
date:   2015-12-29 20:35
categories: django
tags:   django开发 微信开发
---

微信接入时需要填写自己微信公众账号后台服务器的url, 并且需要运行在80端口上, 所以在使用ngrok进行本地测试时, 需要让django的测试服务器使用80端口. 当按照django运行server的命令, 最后加上80端口时, 会出现`Error: You don't have permission to access that port.`的错误.

经网上查阅, [常城博主的一篇博客][Error:You don't have permission to access that port]提到了解决方法, 使用sudo运行启动server的指令.

`sudo python manage.py runserver 80`

但是又出现了下列问题
{% highlight python %}
Traceback (most recent call last):
      File "manage.py", line 8, in <module>
          from django.core.management import execute_from_command_line
      ImportError: No module named django.core.management
{% endhighlight %}
此问题是由于命令中使用的python路径错误导致, 我的项目的django, python环境是通过virtualenv安装的, 所以使用的是virtualenv虚拟环境中安装的python指令, 而不是系统中的python命令, 所以在将虚拟环境中的python指令路径也加入到指令中, 之后运行就可以了.

`sudo /home/wang/dev/vdj/bin/python manage.py runserver 80`


[Error:You don't have permission to access that port]:  http://blog.csdn.net/chenggong2dm/article/details/7629503
