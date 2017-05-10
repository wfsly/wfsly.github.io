---
 layout: post
 title: gitstatus中文乱码问题
 date: 2017-05-10 18:14:35
 categories: git
---

突然遇到了执行`git status`的时候，中文显示乱码，于是网上搜了一下，一行设置就可以
搞定`git config --global core.quotepath false`. 方法参考自[Ruohan Chen博客]

[Ruohan Chen博客]: http://blog.crhan.com/2012/09/git-status-%E4%B8%AD%E6%96%87%E4%B9%B1%E7%A0%81%E8%A7%A3%E5%86%B3/
