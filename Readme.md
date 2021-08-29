# 防止长时间未运行，忘记如何启动
## 安装
```
npm install hexo-cli -g
hexo init blog
cd blog
npm install
hexo server
```

## 常见命令
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
