---
layout: post
title:  "ubuntu14.04下配置jekyll"
date:   2015-12-24 21:26
categories: jekyll使用
tags:    jekyll
---

## 友情提示:下列方法仅供参考

## 由于我在笔记本ubuntu下配置jekyll的时候,出现了不一样的情况,所以下面的配置方法暂时还存在问题.  

1. 安装gem`sudo apt-get install rubygems`, 由于ubuntu14.04 提示"E: Package 'rubygems' has no installation candidate"错误，
执行`sudo apt-get install rubygems-integration`指令

2. 执行 `sudo gem install jekyll`指令安装jekyll
若提示“ERROR: Error installing jekyll: ERROR: Failed to build gem native extension.”错误，则需安装ruby-dev,
`sudo apt-get install ruby-dev`

3. 继续执行安装指令，如果ruby版本低于2.0， 会报错"ERROR: Error installing jekyll:jekyll requires Ruby version >= 2.0.0."

4. 如果以上3步无法安装，那么就执行下列命令也可以完成jekyll安装
```
sudo apt-get install ruby2.0 ruby2.0-dev
sudo gem2.0 install jekyll-import
```

5. 经使用发现，运行`jekyll server`指令后依然会出现错误，解决方法-
```
sudo gem2.0 install bundler
bundle install
```

----
-----------------------2016.8.24更新分割线---------------------------

## 旧的内容
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
