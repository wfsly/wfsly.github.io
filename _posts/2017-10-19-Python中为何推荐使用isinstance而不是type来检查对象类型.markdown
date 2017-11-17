---
 layout: post
 title: Python中为何推荐使用isinstance而不是type来检查对象类型
 date: 2017-10-19 03:24:42
 categories: python
---

## 待完善
type检查内建类型时会比较准确，当检查继承类或者经典类时，其结果不准确，[参考链接][url]

```
class UserInt(int):
    def __init__(self, value=0):
        self.value = value

i = 1
n = UserInt(1)

print (type(i) is type(n))
output: False

```
[url]: http://www.jianshu.com/p/7ef549503c93
