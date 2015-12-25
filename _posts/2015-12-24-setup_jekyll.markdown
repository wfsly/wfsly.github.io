---
layout: post
title:  "ubuntu14.04下配置jekyll"
date:   2015-12-24 21:26
categories: jekyll使用
tags:    jekyll
---

## 友情提示:下列方法仅供参考

## 由于我在笔记本ubuntu下配置jekyll的时候,出现了不一样的情况,所以下面的配置方法暂时还存在问题.  

### 升级ruby和gem版本,安装nodejs
　　因为ubuntu系统里已经安装了ruby和gem, 使用指令`sudo gem install jekyll` 安装jekyll(安装过程有可能比较缓慢,根据源的情况而定)后, 无法正常运行. 与ruby和gem版本问题有关.我在此时安装jekyll时,要求ruby版本要求>=2.0, gem版本要求2.4.


1. 查看版本  
    首先使用 `ruby --version` 和 `gem --version` 查看一下对应的版本号, 看是否符合要求.不过一般预装的版本都比较低.  
2. 安装ruby2.0
    使用指令对ruby upgrade,版本号一直是1.9,所以可以直接使用指令 `sudo apt-get install ruby2.0` 安装ruby2.0.  
3. 升级gem
   对gem 用upgrade升级,无法将版本号升级到2.4. 所以rubygems-update进行gem升级  
   `sudo gem install rubygems-update`  
   `sudo update_rubygems`  
4. 安装nodejs  
    直接运行jekyll会出现无运行环境的错误,这就需要选择一个jekyll的运行环境安装,我选择的是nodejs  
    `sudo apt-get install nodejs`  

    完成之后,jekyll正常运行.
