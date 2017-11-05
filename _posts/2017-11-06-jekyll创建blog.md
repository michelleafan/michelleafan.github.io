---
layout:     post
title:      Jekyll +github 创建博客实践
subtitle:   使用 Jekyll，github 快速创建blog
date:       2017-11-06
author:     michelle
header-img: img/post-bg-ios9-web.jpg
catalog: true
tags:
    - Wiki
    - blog
---



### Jekyll +github 创建博客实践

一直就想用一个简单的方式，创建一个属于自己的博客。百度、知乎一番，发现jekyll+github是一个不错的选择，搭建比较容易，可以把主要的经历放在“积沙成塔”的内容创作和知识沉淀上。
找到的最简单易行的方式就是按照简书上分享的文章，好文，必须赞！：
http://www.jianshu.com/p/e68fba58f75c
个人觉得写得挺很好，对于想要马上写博客的人来说很高效实用。按照上面的方式，很快就在github上搞好了一个博客的页面，接下来就是按照自己的需要更换下资源、个人信息等，就可以开始写blog的。
但是笔者想多了解下jekyll，所以重新在linux机器上，从安装jekyll、创建blog、本地调试，到托管到gitbub的过程实践了一遍。
#### 1、安装jekyll(linux)
jekyll 安装之前需要先装依赖的环境：Ruby，Gem，Node.js
笔者基本参照下文完成安装jekyll，不一致的地方再搜一下，很快就能搞好（时间主要花在下载安装的过程）
http://www.cnblogs.com/ee2213/p/3915243.html?utm_source=tuicool
#### 2、创建blog

创建一个目录，用于存放blog，使用'jeyll new blog‘ 创建博客，具体命令如下：
```
mkdir myblog
cd myblog
jekyll new blog
cd blog
jekyll serve --host 0.0.0.0
```
笔者在创建blog的过程中，遇到了如下的问题：
#### 1）执行jekyll new blog之后，一直卡在那里，无响应
强制中断任务（ctrl+c）以后，运行jekyll serve命令，Ruby提示错误：
Bundler::GemNotFound 
原因是依赖的某个模块没有安装
解决方法：
http://blog.csdn.net/moonclearner/article/details/52238033
需要根据错误提示信息确认缺少的模块，执行
bundle install 或者
gem install xxx（模块名）
#### 2) 直接运行jekyll serve命令，在浏览器中不能访问
显示是正常运行的：
![jpg](/assets/images/1.jpg)

浏览器不能访问

![Alt text](./1509898247539.png)
原因没有搞明白，但是通过添加参数解决，通过外网ip+4000端口即可访问：
```
jekyll serve --host 0.0.0.0
```
#### 3 查看并修改博客页面
创建blog后，查看当前的文件目录为：
![alt](./1509898698407.png)
为什么这个地方与其他资料显示的目录结构不一致呢？（_include,_layouts等都没有）
![](./1509898835160.png)
查官网资料发现原因是：https://jekyllrb.com/docs/themes/

![Alt text](./1509899114675.png)

原来这些文件夹都在主题下面
![Alt text](./1509899376180.png)
此处可以将主题下面的文件copy到blog目录下，之后对blog目录下的资源进行修改
之后笔者将_include,_layout替换成需要的（部分替换的资源来源简书那篇文章中的资源）。
当前博客页面即为最终的效果

#### 4提交代码到github上
```
cd my_website_folder   //进入blog所在的文件夹
git init
git add .
git commit -m "Initial commit"
```
可能遇到的问题，linux 没有配置github email 和用户名,解决方法：
```
git config  --global user.name "xxxx"
git config  --global user.emil "xxxxx"
```





