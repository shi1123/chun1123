---
title: centos7中安装MongoDB
date: 2021/7/13 01:07:11
description: centos7中安装MongoDB,使用 rpm 包安装,或者使用使用 .tgz 包安装
categories:
  - 编程人生
  - 后端
  - 数据库
  - MongoDB
tags:
  - MongDB
  - centos7
  - rpm
  - 外网访问
  - tgz
---

# centos7中安装MongoDB
[官方文档](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-red-hat/)
## 使用 rpm 包安装

### 1. 配置yum源.

创建 `/etc/yum.repos.d/mongodb-org-5.0.repo` 文件使得可以直接使用 `yum` 安装:

```
[mongodb-org-5.0]
name=MongoDB Repository
baseurl=https://repo.mongodb.org/yum/redhat/$releasever/mongodb-org/5.0/x86_64/
gpgcheck=1
enabled=1
gpgkey=https://www.mongodb.org/static/pgp/server-5.0.asc
```

### 2. 安装：

```
sudo yum install -y mongodb-org
```

### 3. 默认情况下, MongoDB 使用 `mongod` 默认用户并使用以下默认文件夹:

- `/var/lib/mongo` (the data directory)
- `/var/log/mongodb` (the log directory)

创建 MongoDB 数据和日志文件夹:

```
sudo mkdir -p /var/lib/mongo
sudo mkdir -p /var/log/mongodb
```

### 4. 启动关闭：

```mongod  --shutdown --dbpath /var/lib/mongo
# start 需要加上--bind_ip_all允许外网访问
mongod --dbpath /var/lib/mongo --logpath /var/log/mongodb/mongod.log --fork --bind_ip_all

# close
mongod  --shutdown --dbpath /var/lib/mongo
```



## 使用 .tgz 包安装

### 1. 安装依赖

```
sudo yum install libcurl openssl xz-libs
```

### 2. 下载并解压依赖

```
wget https://fastdl.mongodb.org/linux/mongodb-linux-x86_64-ubuntu1604-4.2.8.tgz    # 下载
tar -zxvf mongodb-linux-x86_64-ubuntu1604-4.2.8.tgz                                # 解压
```

### 3. 拷贝可执行文件到 `/usr/local/bin`中或者创建软连接

```
# 拷贝可执行文件到 /usr/local/bin/
sudo cp /path/to/the/mongodb-directory/bin/* /usr/local/bin/ 
# 创建软连接
sudo ln -s  /path/to/the/mongodb-directory/bin/* /usr/local/bin/
```

### 后面的步骤和上面 使用 rpm 安装步骤的 3 和 4 相同

#### 遇到的问题，使用 `.tgz` 安装的时候，启动时一直报错

```
[root@testserver mongodb-linux-s390x-rhel72-5.0.2]# mongod --dbpath /var/lib/mongo --logpath /var/log/mongodb/mongod.log --fork
-bash: /usr/local/bin/mongod: 无法执行二进制文件
```

#### usr/local/bin 中的可执行文件权限如下：

```
[root@testserver mongodb-linux-s390x-rhel72-5.0.2]# ls -al /usr/local/bin总用量 259648
drwxr-xr-x.  2 root root       220 8月  13 23:03 .
drwxr-xr-x. 14 root root       163 6月  26 21:08 ..
-rwxr-xr-x.  1 root root  12254032 12月 21 2020 docker-compose
-rwxr-xr-x   1 root root     15205 8月  13 23:03 install_compass
-rwxrwxrwx   1 root root  56701488 8月  13 23:03 mongo
-rwxrwxrwx   1 root root 104345864 8月  13 23:03 mongod
-rwxrwxrwx   1 root root  73220648 8月  13 23:03 mongos
-rwxr-xr-x   1 root root   4829704 6月  26 21:09 redis-benchmark
lrwxrwxrwx   1 root root        12 6月  26 21:09 redis-check-aof -> redis-server
lrwxrwxrwx   1 root root        12 6月  26 21:09 redis-check-rdb -> redis-server
-rwxr-xr-x   1 root root   5002960 6月  26 21:09 redis-cli
lrwxrwxrwx   1 root root        12 6月  26 21:09 redis-sentinel -> redis-server
-rwxr-xr-x   1 root root   9486792 6月  26 21:09 redis-server
```

还没有解决，最后使用 rpm 包安装成功。