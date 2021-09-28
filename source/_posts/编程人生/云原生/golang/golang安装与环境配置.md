---
title: golang 基础环境搭建
date: '2021/9/18 16:10:13'
description: Mac 下安装和配置 golang 环境
tags:
  - golang
  - mac
  - GOROOT
  - GOPATH
categories:
  - 编程人生
  - 云原生
  - golang
---

# golang 基础环境搭建
1、下载安装 Mac

https://golang.google.cn/dl/

2、设置环境变量

```
# For go installed from original pkg download from https://golang.org/doc/install
export GOPATH=$HOME/dev/go-workspace
export GOROOT=/usr/local/go
export PATH=$PATH:$GOPATH/bin
export PATH=$PATH:$GOROOT/bin

# For Go installed from home brew. (brew update and brew install golang)
export GOPATH=$HOME/dev/go-workspace
export GOROOT=/usr/local/opt/go/libexec
export PATH=$PATH:$GOPATH/bin
export PATH=$PATH:$GOROOT/bin
```

<input type="search" id="search" name="keyword" autocomplete="off"  class="search-text" placeholder="小米灵感触控笔">
