---
layout: post
title:  "python读取json文件"
categories: python
tags: django开发
---

python对json文件的处理, 有一个[json][json.doc]模块.

脚本中首先要导入json模块
`import json`

json模块主要有两个函数, `json.load()`和`json.dump()`

### json.load() 读取

{% highlight python %}

temp_file = open('...dir/file_name.json', 'r')
data = json.load(temp_file)

{% endhighlight %}

创建一个文件对象temp_file打开一个json文件, temp_file作为load()的函数, load函数将json文件中的数据解析后保存到data变量中,之后就可以对json数据进行操作.

### json.dump() 写入
{% highlight python %}

    temp_file = open('...dir/file_name.json', 'r')
    json.dump(temp_file, data)

{% endhighlight %}

dump函数将data中的json数据写入到文件中






[json.doc]: https://docs.python.org/2/library/json.html#module-json
