---
layout: post
title:  "在settings.py中设置django模板templates默认文件路径"
date:  2015-12-28 12:42 
categories: django
tags:   django开发 微信开发
---
在view的函数中, 返回的response要使用html模板的时候, django中创建一个templates目录, 将以后需要用到的前端模板都放在里面. 首先要在settings.py中配置templates模板默认的文件夹路径, 否则会出现对应html文件"TemplateDoesNotExist"的Error.

因为如果设置templates路径,django默认会按照优先级从以下两个位置中读取templates资源

`django/contrib/admin/templates`

`django/contrib/auth/templates`

所以在使用templates之前, 在settings.py中找到TEMPLATES, 将其中的DIR的列表中加入所要使用的templates的路径, django查找的优先级按列表中位置的顺序.

{% highlight python %}
TEMPLATES = {
    {

        'BACKEND':  'django.template.backends.django.DjangoTemplates',
        'DIR':  [],
        'APP_DIR':  True,
        ......
    }
}
{% endhighlight %}
在DIR后边列表中可以直接加入templates所在的绝对位置, 但是为了程序的通用性, 我们需要让程序自己去确定模板在项目中的位置. settings.py中在一开始就通过os模块接口, 获取到了当前项目根路径, `BASE_DIR`是项目所在路径.
{% highlight python %}
BASE_DIR = os.path.dirname(os.path.dirname(os.path.abspath(__file__)))
{% endhighlight %}
所以只需要在`BASE_DIR`的基础上加入templates的路径即可
{% highlight python %}
'DIR':  [BASE_DIR + '/templates']
{% endhighlight %}
