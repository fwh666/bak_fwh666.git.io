---
layout: post
lock: need
title: 用Github+webhook钩子做自动部署
date: 2020-12-23 21:41:03
author: 文浩
img:
coverImg: http://oes.fuwenhao.club/images/banner/09.jpg
top: false
cover: false
toc: false
mathjax: false
summary:
tags:
  - webhook
  - GitHub
categories: [webhook,Github]
description: Mac下使用Jekyll和github搭建个人博客
keywords: 文浩Marvin ,   wenhao  , 文浩  , 似水似流年  , wenhaoclub  , fuwenhao.club , plus.fuwenhao.club  ,文浩的博客 , 似水似流年的博客
link: https://cdn.jsdelivr.net/gh/wenhaoclub/blog-assets/images/Java/JVM/head2.jpg
---

# 如有用Github钩子做自动部署

> 标签（空格分隔）： Github webhook go 

<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/wenhaoclub/blog-assets/files/js/css/APlayer.min.css">
<script src="https://cdn.jsdelivr.net/gh/wenhaoclub/blog-assets/files/js/APlayer.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/meting@1.1.0/dist/Meting.min.js"></script>
<div class="aplayer" data-id="1901371647" data-server="netease" data-type="song" data-mode="single" data-autoplay="true"></div>

---


## 安装go环境：

    安装go环境：    yum install -y golang
    安装webhook：  go get github.com/adnanh/webhook
    
    命令安装位置可以通过go env查看，GOPATH就是命令安装路径，比如我的命令就安装在/root/go/bin/webhook。


### webhook无法go安装的方案：
#### 方案一：
1. 去GitHub官网下载Linux的安装包：
   - https://github.com/adnanh/webhook/releases
   - 下载相应的版本到本地，存放到服务器内。
2. 解压缩tar包，得到webhook执行文件
3. 将文件放入 /usr/bin目录下
4. 授权： chmod u+x /usr/bin/webhook

#### 方案二：
1.  去Github官网下载adnanh/webhook的源码
2. 下载到服务器内，执行 go build 得到webhook的可执行脚本
3.  讲webhook放入/usr/bin/目录下

## webhook配置与启动

编写配置文件hooks.json，格式如下。

```
[
  {
    "id": "deploy-webhook",
    "execute-command": "hexoBlog.sh",
    "command-working-directory": "/home/fwh/Blog/"
  }
]

```

- id：钩子的id，可自定义
- execute-command：要执行的脚本名，就是刚才编写的部署脚本
- command-working-directory：脚本所在目录
- 注意脚本.sh 是可执行的。 chmod u+x filename.sh

完成后通过webhook命令启动，可以看到id为deploy-webhook的配置已经加载了，我们需要注意的是监听的端口和路径，等下要用到。

```
执行命令：
/root/go/bin/webhook -hooks hooks.json -verbose
或者
/usr/bin/webhook -hooks hooks.json -verbose
或者-后台执行命令：
nohup /usr/bin/webhook -hooks hooks.json -verbose >> webhook.log 2>&1 &

----------
输出内容如下：

[webhook] 2020/04/22 15:18:22 version 2.6.11 starting
[webhook] 2020/04/22 15:18:22 setting up os signal watcher
[webhook] 2020/04/22 15:18:22 attempting to load hooks from hooks.json
[webhook] 2020/04/22 15:18:22 found 1 hook(s) in file
[webhook] 2020/04/22 15:18:22   loaded: deploy-webhook
[webhook] 2020/04/22 15:18:22 serving hooks on http://0.0.0.0:9000/hooks/{id}
[webhook] 2020/04/22 15:18:22 os signal watcher ready


http://0.0.0.0:9000/hooks/{id}

```

- 其他参考命令：

```
# 非后台运行
github-webhook -b [shell脚本路径] -s [github webhook设置的密码]

# 后台运行
nohup github-webhook -b [shell脚本路径] -s [github webhook设置的密码] & 

# 定向日志输出
nohup github-webhook -b ~/sh/你的脚本.sh -s hook密码 >> ~/logs/webhook.log 2>&1 &
```


## Github Webhooks配置

现在服务器已经启动了webhook程序监听9000端口，接下来仅需要告诉Github这个地址和端口就好了。

打开仓库设置页，添加webhook。

在指定的github项目中，选择设置，选webhook选项

配置webhooks，Payload URL就是要通知的地址，把刚才打印出的端口和路径填上即可，其他默认。

现在可以提交代码测试了，如果推送失败Github中会有错误提示，同样的，成功不仅在Github中能看到，服务器的打印日志也有记录。

## 注意事项：

1. 记得服务器要开放的9000端口，同时防火墙也需要开放9000端口，用telnet命令验证一下端口或者lsof -i:9000
2. 关于webhook脚本建议后台指定日志输出。
3. 注意执行命令采用的权限问题，可能会出现脚本无权限执行的情况。建议全部采用基础用户组操作；确保文件是可执行的： chmod u+x  脚本.sh   并且确认shell脚本使用是 #! /bin/bash
4. 以上操作前提是-服务器的项目已经配置过SSH密钥获取GitHub项目，此文不做赘述。


## 参考网址：

- webhook官网：https://github.com/adnanh/webhook
- 钩子自动部署：https://juejin.cn/post/6844904138128506894
- GO使用Webhook实现github自动化部署：https://www.cnblogs.com/phpper/p/12951970.html
- shell脚本执行报错exec format error解决:https://blog.csdn.net/aixueai/article/details/115002798
- Linux执行.sh文件，提示No such file or directory的问题的解决方法:https://blog.csdn.net/iemdm1110/article/details/71750919