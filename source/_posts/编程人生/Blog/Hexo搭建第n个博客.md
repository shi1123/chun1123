---
title: Hexo搭建第n个博客
date: 2019/7/13 20:46:25
categories:
  - 编程人生
  - Blog
tags:
  - blog
  - hexo
  - github
  - gitee
  - next
---
# 使用 hexo 搭建个人博客发布到gitee/github

## 1. hexo 搭建

参考资料：hexo[中文文档](https://hexo.io/zh-cn/docs/)

### 安装前提

安装 Hexo 相当简单，只需要先安装下列应用程序即可：

- [Node.js](http://nodejs.org/) (Node.js 版本需不低于 10.13，建议使用 Node.js 12.0 及以上版本)
- [Git](http://git-scm.com/)

<!-- more -->
### 安装 Git

- Windows：下载并安装 [git](https://git-scm.com/download/win).
- Mac：使用 [Homebrew](http://mxcl.github.com/homebrew/), [MacPorts](http://www.macports.org/) 或者下载 [安装程序](http://sourceforge.net/projects/git-osx-installer/)。
- Linux (Ubuntu, Debian)：`sudo apt-get install git-core`
- Linux (Fedora, Red Hat, CentOS)：`sudo yum install git-core`

> Mac 用户
>
> 如果在编译时可能会遇到问题，请先到 App Store 安装 Xcode，Xcode 完成后，启动并进入 **Preferences -> Download -> Command Line Tools -> Install** 安装命令行工具。

> Windows 用户
>
> 对于中国大陆地区用户，可以前往 [淘宝 Git for Windows 镜像](https://npm.taobao.org/mirrors/git-for-windows/) 下载 git 安装包。

### 安装 Node.js

Node.js 为大多数平台提供了官方的 [安装程序](https://nodejs.org/en/download/)。对于中国大陆地区用户，可以前往 [淘宝 Node.js 镜像](https://npm.taobao.org/mirrors/node) 下载。

其它的安装方法：

- Windows：通过 [nvs](https://github.com/jasongin/nvs/)（推荐）或者 [nvm](https://github.com/nvm-sh/nvm) 安装。
- Mac：使用 [Homebrew](https://brew.sh/) 或 [MacPorts](http://www.macports.org/) 安装。
- Linux（DEB/RPM-based）：从 [NodeSource](https://github.com/nodesource/distributions) 安装。
- 其它：使用相应的软件包管理器进行安装，可以参考由 Node.js 提供的 [指导](https://nodejs.org/en/download/package-manager/)。

对于 Mac 和 Linux 同样建议使用 nvs 或者 nvm，以避免可能会出现的权限问题。

### 安装 Hexo

所有必备的应用程序安装完成后，即可使用 npm 安装 Hexo。

```
# Mac 用户需要在前面加上 sudo 使用管理员权限安装
$ npm install -g hexo-cli
```

### 初始化 blog

安装 Hexo 完成后，请执行下列命令，Hexo 将会在指定文件夹中新建所需要的文件。

```
$ hexo init MyBlog
$ cd MyBlog
$ npm install
```

新建完成后，指定文件夹的目录如下：

```
.
├── _config.yml
├── package.json
├── scaffolds
├── source
|   ├── _drafts
|   └── _posts
└── themes
```



### 配置blog

<iframe src="https://www.youtube.com/embed/A0Enyn70jKU" frameborder="0" loading="lazy" allowfullscreen="" style="box-sizing: inherit; margin: 1em 0px; padding: 0px; border: 0px; outline: 0px; font-weight: inherit; font-style: inherit; font-family: inherit; font-size: 15px; vertical-align: baseline;"></iframe>

## 网站

| 参数          | 描述                                                         |
| :------------ | :----------------------------------------------------------- |
| `title`       | 网站标题                                                     |
| `subtitle`    | 网站副标题                                                   |
| `description` | 网站描述                                                     |
| `keywords`    | 网站的关键词。支持多个关键词。                               |
| `author`      | 您的名字                                                     |
| `language`    | 网站使用的语言。对于简体中文用户来说，使用不同的主题可能需要设置成不同的值，请参考你的主题的文档自行设置，常见的有 `zh-Hans`和 `zh-CN`。 |
| `timezone`    | 网站时区。Hexo 默认使用您电脑的时区。请参考 [时区列表](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones) 进行设置，如 `America/New_York`, `Japan`, 和 `UTC` 。一般的，对于中国大陆地区可以使用 `Asia/Shanghai`。 |

其中，`description`主要用于SEO，告诉搜索引擎一个关于您站点的简单描述，通常建议在其中包含您网站的关键词。`author`参数用于主题显示文章的作者。

#### 我的 blog 的 site 配置如下

```
# Site
title: SZP
subtitle: 'Daily Records'
description: '总得留下点什么'
keywords: coding
author: szp
language: zh-CN
timezone: 'Asia/Shanghai'
```

#### 常见命令

```
# 初始化blog
$ hexo init [folder]
# 新建可以是分类，也可以是文章和草稿，layout (post/page/draft)也就是文章
$ hexo new [layout] <title>
# 生成 categories 目录
$ hexo new page categories
# 生成 tags 目录
$ hexo new page tags

# 生成第一篇blog 'my first blog'
$ hexo new 'my first blog'

# 清除缓存，特别是修改使用的主题时
$ hexo clean

# 生成静态文件。
$ hexo generate
# 简写
$ hexo g

# 发布文章
$ hexo publish [layout] <filename>

# 启动服务器。默认情况下，访问网址为： http://localhost:4000/。
$ hexo server
# 简写
$ hexo s

# 部署网站。一般是推送到 github 或者 gitee 上
$ hexo deploy
# 简写
$ hexo d
# 有可能报错，需要安装 hexo-deployer-git 插件
$ npm install --save hexo-deployer-git
```

#### 发布到github/gitee

gitee 参见[连接](https://gitee.com/help/articles/4136#article-header0)

github 参见[连接](https://docs.github.com/en/pages)

_config.yml配置

```
# Deployment
## Docs: https://hexo.io/docs/one-command-deployment
deploy:
  type: 'git'
  repo: 'https://gitee.com/chun1123/chun1123.git'
  branch: 'master'
```

##### 关联Git和Gitee

- 用户信息配置，Git Bash：

```verilog
git config --global user.name "你的Gitee用户名"
git config --global user.email "你的Gitee注册邮箱"
```

补充，`git config --list`可查看配置信息。

- 生成SSH Key（会有提示，可以直接默认，三个回车即可）:

```excel
ssh-keygen -t rsa -C "你的Gitee注册邮箱"
```

- 记事本打开`id_rsa.pub`公钥文件(我的在`C:\用户\16647\.ssh`文件夹下)，复制其中全部内容，到Gitee设置中添加SSH公钥。
- 测试SSH连接（第一次连接会有SSH警告，输入`yes`忽略即可）：

```nginx
ssh -T git@gitee.com
```

## 配置 next 主题

### next 主题使用
[参考链接](https://theme-next.iissnan.com/getting-started.html)

### 安装

在终端窗口下，定位到 Hexo 站点目录下。使用 `Git` checkout 代码：

```
$ cd your-hexo-site
$ git clone https://github.com/iissnan/hexo-theme-next themes/next
```

### 启用主题

与所有 Hexo 主题启用的模式一样。 当 克隆/下载 完成后，打开 **站点配置文件** _config.yml ， 找到 `theme` 字段，并将其值更改为 `next`。

```
theme: next
```

### 主题设定

Scheme 是 NexT 提供的一种特性，借助于 Scheme，NexT 为你提供多种不同的外观。同时，几乎所有的配置都可以 在 Scheme 之间共用。目前 NexT 支持三种 Scheme，他们是：

- Muse - 默认 Scheme，这是 NexT 最初的版本，黑白主调，大量留白
- Mist - Muse 的紧凑版本，整洁有序的单栏外观
- Pisces - 双栏 Scheme，小家碧玉似的清新
- Gemini - 单栏 Scheme，左边菜单，右边文章

Scheme 的切换通过更改 **主题配置文件**，搜索 scheme 关键字。 你会看到有三行 scheme 的配置，将你需用启用的 scheme 前面注释 `#` 去除即可。

```
#选择 Pisces Scheme
#scheme: Muse
#scheme: Mist
scheme: Pisces
#scheme: Gemini
```

## 设置搜索

### Local Search 由 [flashlab](https://github.com/iissnan/hexo-theme-next/pull/694) 贡献

添加百度/谷歌/本地 自定义站点内容搜索

1. 安装 `hexo-generator-searchdb`，在站点的根目录下执行以下命令：

   ```
   $ npm install hexo-generator-searchdb --save
   ```

2. 编辑 **站点配置文件**，新增以下内容到任意位置：

   ```
   search:
     path: search.xml
     field: post
     format: html
     limit: 10000
   ```

3. 编辑 **主题配置文件**，启用本地搜索功能：

   ```
   # Local search
   local_search:
     enable: true
   ```

## 设置中文

编辑 **站点配置文件** _config.yml ， 将 `language` 设置成你所需要的语言。建议明确设置你所需要的语言，例如选用简体中文，配置如下：

```
# 注意与 themes/next/language 下的文件名对应，这里 zh-CN 不要加 ''，否则识别不了
language: zh-CN
```

## 设置 author 头像

在 source 目录下新建 images 文件夹，将头像文件 avatar.png 放入其中。

更改 **主题配置文件**，修改 avator 关键字

```
# Sidebar Avatar
avatar:
  # Replace the default image and set the url here.
  url: /images/avatar.png # 头像目录
  # If true, the avatar will be dispalyed in circle.
  rounded: false
  # If true, the avatar will be rotated with the cursor.
  rotated: false
```

## 设置通过文件路径自动生成文章分类(categories)

插件[github](https://github.com/xu-song/hexo-auto-category)

### 安装

```
$ npm install hexo-auto-category --save
```

### 配置

编辑 **站点配置文件** `_config.yml`

```
# Generate categories from directory-tree
# Dependencies: https://github.com/xu-song/hexo-auto-category
# depth: the max_depth of directory-tree you want to generate, should > 0
auto_category:
 enable: true
 depth: 
```

### 编译和预览

```
$ hexo clean && hexo g && hexo s
```

生成的文章分类 `source/_post/web/framework/hexo.md` 如下所示:

```
categories:
  - web
  - framework
```

### 作者blog地址

[eson的blog](https://blog.eson.org/)

## 设置【阅读全文】展示文章简介

### 文章中使用设置手动截断(推荐)

```
# 前言
&emsp;&emsp;GitHub为广大开发者提供了一个非常好的平台，不仅是代码的开源，同时GitHub还提供了开发者可以在GitHub上建立自己的站点（GithubPage）的一个非常有意思的功能。它功能有限只能创建静态的网站。
&emsp;&emsp;本文整理自己的部署过程，意在帮助那些刚刚接触GitHub的新手同学，可以利用GitHub快速创建高逼格的个人博客站点。

<!-- more -->
# 准备工作
- GitHub账号，创建一个仓库，规则为：例如我的账号为mds1455975151，则新建仓库名称为mds1455975151.github.io
- NodeJS环境及相关基本知识，我的环境如下：
 - os: Windows_NT 6.1.7601 win32 x64
 - node: 8.9.2
- Git基本使用及git for windows安装使用。
 - git version: 2.15.0.windows.1
```

### 设置并显示文章摘要

设置description属性

```
---
title: Git常见问题解决
date: 2017-12-08 21:40:28
categories: 技术
tags: [Git,常见问题]
description: 日常使用git遇到的各种报错及问题详解
---
```

### 自动形成摘要设置截断长度

在主题配置文件中添加如下配置,默认截取的长度为150 字符，可以根据需要自行设定.

```
auto_excerpt:
  enable: true
  length: 150
```
