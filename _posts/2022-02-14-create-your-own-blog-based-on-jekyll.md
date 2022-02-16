---
date: 2022-02-13 12:00:00
layout: post
title: 打造属于你自己的网站！
subtitle: 仿造netfilx风格，打造属于你自己的网站！
description: 仿造netfilx风格，打造属于你自己的网站！
category: 技术
image: /assets/img/about-bg.jpg
optimized_image: /assets/img/about-bg.jpg
tags:
  - jekyll
  - sass
  - liquid
  - gulp
author: liujing
category: 技术
jishu: true
---

github打造自己的网站，在网上已经有很多回答。但是每个回答都有其不足的地方，而且东西十分零碎。基于这个问题，我结合了[jekflix-template](https://github.com/thiagorossener/jekflix-template)和[blogdemo](https://github.com/leach-chen/blogdemo)，打造属于自己的博客。

也欢迎大家star[本站源码](https://github.com/liujing1995/jekyll-blog-demo)

也可以改造成属于你自己个人网站，[网页预览（点击可查看）](https://liujing1995.github.io/)

GitHub搭建个人网站可基于jekyll或者hexo或者其它的，本教程使用的是**jekyll**

## 需要的知识点

- ruby
- sass
- gulp
- jekyll

##  网站托管
我们知道，一个网站要能够在任何地方都能够被访问，那么需要部署到服务器上。其实github就提供了这样的功能，只要按照github格式要求，新建一个仓库，把你的网站代码上传到里面，那么就可以在任何时候任何地方都能够访问了，那么如何搭建这个代码托管仓库呢？
可参考官方链接，我这也把步骤写出来。

1.首先你要到GitHub上注册一个账号,例如我注册的用户名为：liujing1995

2.点击New repository–>输入仓库名称格式为：用户名.github.io(如：liujing1995.github.io)->点击Create repository

3.浏览器里访问[https://你自己设定的仓库名称.github.io/](https://liujing1995.github.io/),可以发现这个url可以被访问了，你可以把改仓库拉取到本地，然后在里面新建一个index.html的文件,在里面输入任意内容，然后再把代码推送到git上，然后再访问该链接，可以发现index.html里面的内容被访问到了。

git相关知识点可参考[git使用教程](https://www.jianshu.com/p/e57a4a2cf077)

到这里，一个免费且无限流量的github代码托管仓库就创建完成了。

## 项目安装

本安装方法是基于windows10

1、首先安装 [Ruby](https://www.ruby-lang.org/en/documentation/installation/)和 [NodeJS](https://nodejs.org/) .

2、安装Jekyll.

```
$ gem install jekyll
```

3、其次安装gulp client.

```
$ npm install gulp-cli -g
```

4、Fork 或者直接下载 [Jekyll theme](https://github.com/liujing1995/liujing1995.github.io)仓库代码 

5、cd到项目的路径下

```
$ cd path/to/jekyll-blog-demo
```

6、在项目的路径下安装npm packages:

```
$ npm install
```

7、安装 Ruby dependencies:

```
$ bundle install
```

8、Build Jekyll:

```
$ bundle exec jekyll build
```

9、Then run Gulp:

```
$ gulp
```



##  jekyll项目目录介绍



> _includes/ 包含一些html模板
>
> _layouts/ 包含一些html模板
>
> _sass/ 用于保存scss文件
>
> _posts/ 博客内容
>
> _site/ jekyll解析后的html文件夹，这个文件夹作为最终展示界面
>
> _posts/ 博客内容
>
> _pages/ 其他需要生成的网页，如About页
>
>  assets/ 辅助资源 css布局 js脚本 图片等
>
>  _config.yml 网站的一些配置信息
>
> myblog/ 自定义html页面，也会被jekyll解析，放入_site文件夹中 
>
>  index.html 网站的入口



也可参考[官方链接](http://jekyllcn.com/docs/home/)



## 修改模板

### 1、修改配置文件

提供的配置文件在src/yml/目录下

具体的配置方式参考[jekflix-template](https://github.com/thiagorossener/jekflix-template/wiki/settings),自己如果对sass和前端比较熟的也可以自己定义

### 2、修改样式

提供的样式文件在_sass/目录下，如果对相应的样式不满意，可以修改。

如果对.scss的修改不是很了解，可点击[参考链接](https://www.sass.hk/guide/)

### 3、修改模板

提供的模板文件在\_includes/和\_layouts/下

#### 3.1 jekyll调用逻辑

1. jekyll项目首先会访问主目录结构下的index.html

   ![](/image/create-your-own-blog-based-on-jekyll/xx.png "图1")

任何只要包含[Front Matter](https://jekyllrb.com/docs/frontmatter/)头信息的文件在 Jekyll 中都能被当做一个特殊的文件来处理，[Front Matter](https://jekyllrb.com/docs/frontmatter/)可以理解为两行三虚线之间，需要定义两行三虚线之间的内容。

头信息必须在文件的开始部分，并且需要按照 YAML 的格式写在两行三虚线之间。

在这两行的三虚线之间，你可以设置**预定义的变量**（下面这个例子可以作为参考），甚至创建一个你**自己定义的变量**。这样在接下来的文件和任意模板中或者在包含这些页面或博客的模板中都可以通过使用[Liquid 标签](https://shopify.github.io/liquid/basics/introduction/)来访问这些变量。

预定义变量，就是jekyll预先设置的变量，如下表所示

<table>
  <thead>
    <tr>
      <th><strong>变量名称</strong></th>
      <th><strong>描述</strong></th>
    </tr>
  </thead>
  <tfoot>
    <tr>
      <td>layout</td>
      <td>如果设置的话，会指定使用该模板文件。指定模板文件时候不需要文件扩展名。模板文件必须放在 `_layouts` 目录下。</td>
    </tr>
  </tfoot>
  <tbody>
    <tr>
      <td>permalink</td>
      <td>如果你需要让你发布的博客的 URL 地址不同于默认值 `/year/month/day/title.html`，那你就设置这个变量，然后变量值就会作为最终的 URL 地址。</td>
    </tr>
    <tr>
      <td>published</td>
      <td>如果你不想在站点生成后展示某篇特定的博文，那么就设置（该博文的）该变量为 false</td>
    </tr>
  </tbody>
</table>

在本教程中的index.html中，layout变量的值为post，表示采用`_layouts`目录下的post.html作为模板。

2. 加载\_layout文件夹内的所有模板，并将其中的 字段按照_includes文件夹内对应文件填入

3. 遍历_post文件夹及子文件夹，对所有命名符合`yyyy-mm--dd-title.md` 格式的博客文件放入`site.posts` 变量(按时间倒序)，并对其进行解析，并且根据[Front Matter](https://jekyllrb.com/docs/frontmatter/) 头的内容套入layout生成对应title的博客，解析生成的博客按照目录结构放在\_site/ 文件夹中。

   ![](/image/create-your-own-blog-based-on-jekyll/post.png "图2")

4. 遍历整个项目子目录，扫描所有含[Front Matter](https://jekyllrb.com/docs/frontmatter/) 头的文件，放入`site.pages` 变量并根据`permalink` 字段指定的URL目标位置生成index.html

5. 在生成过程中，文件中包含的Liquid脚本会被解析并替换。Liquid指令 包括Object、Tag、Filter三类，其中object是变量，在解析过程中会被直接文本替换。

#### 3.2 模板修改

通过3.1了解了jekyll的调用过程，现在只需要对html修改即可。




最后，自己的博客搭建完毕，你也可以根据本文的内容任意修改。
