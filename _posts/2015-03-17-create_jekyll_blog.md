---
layout: post
title: Mac下Jekyll安装
category : 技术分享
tagline: "Supporting tagline"
tags : [Jekyll, blog, 技术]
---
{% include JB/setup %}
# Mac下Jekyll安装

<br><br>
之前一直用Wordpress,虽然功能强大，各种插件各种bug，如果想弄个主题，折腾得要命。最近改用jekyll+gitHub免费空间。记录一下。<br >
我用的是Mac，所以只讲述Mac下如何安装，Windows如何安装需自行Google
    
**需要环境支持**<br>
Ruby，Mac自带，如果没有请安装

**安装Gem**<br>
Gem是Ruby第三方插件管理器<br>
下载Gem到本地后，在终端输入如下代码

``` python
## 检查gem版本
gem -v
## 更新Gem(提示权限)
gem update --system
```
<!--break-->

[官网安装教程](https://rubygems.org/pages/download)

gem update --system。这一步需要翻墙，否则会出现404错误。[解决办法参考](https://ruby.taobao.org/)


**安装jekyll**

上面安装的Gem派上用场

```
安装jekyll(提示权限)
$ gem install jekyll
安装成功之后，查看版本号
$ jekyll -v
```

<br>**使用jekyll**<br><br>
jekyll安装成功之后，可以在终端上执行 jekyll 命令来使用了，有两种方法，一种是自己新建一个jekyll博客，另外一种是使用现成的博客。

我比较懒，当然是直接使用现成的博客了。

我使用的主题  http://enml.github.io/site 

不浪费口水，直接撸<br>
下载主题，在终端中使用命令cd到该主题根目录下；

``` 
## 博客生成，默认生成再_site目录下，当然也可以在配置文件中自定义
jekyll build
## 开启jekyll本地预览
jekyll server
```


在浏览器中输入 http://localhost:4000 即可访问博客站点<br />
不能访问请检查_config.yml配置文件是否需要修改

**遇到的坑：**

较老版本使用 jekyll --server <br />
执行 jekyll build 命令报错

```
ERROR: YOUR SITE COULD NOT BE BUILT:
       Missing dependency: rdiscount
```

解决：rdiscount是 Jekyll依赖的一个包，可以通过安装这个包来解决。

```
安装rdiscount
$ gem install rdiscount
```

如果缺少其他包，同理使用 gem install 解决

安装各种依赖包的时候可能会提示权限不足，比如安装rdiscount提示我/usr/bin没有写入权限
解决：

```
sudo chmod -R 777
```

安装完毕后将/usr/bin权限设置回操作前的权限。否则下次终端启动时可能报错。

**上传GitHub**

再_post中放入md文件，文件格式必须遵从YEAR-MONTH-DAY-title.md。<br />
上传至GitHub后，我们就可以在线查看博客了。<br />
贴上我的jekyll博客地址 http://pyrinelaw.github.io<br />

**附：**

由权限问题导致终端启动报错，请使用Mac磁盘工具修复<br />
新建jekyll博客教程：http://www.jekyll.org/ (╯□╰ 需要翻墙)<br />
也可以去这个网站上找各种主题 http://jekyllthemes.org/<br />
尊重他人劳动成果，引用他人主题请注明出处<br />










