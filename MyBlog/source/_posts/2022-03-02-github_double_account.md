---
layout: post
lock: need
title: 如何在一台电脑上设置多个github账号
date: 2022-03-02 21:41:03
author: 文浩
img:
coverImg: https://baseoss.fuwenhao.club/banner/09.jpg
top: false
cover: false
toc: false
mathjax: false
summary:
tags:
  - Gitee
  - GitHub
categories: [GitHub]
description: 双账号登录
keywords: 文浩Marvin ,   wenhao  , 文浩  , 似水似流年  , wenhaoclub  , fuwenhao.club , plus.fuwenhao.club  ,文浩的博客 , 似水似流年的博客
link: https://cdn.jsdelivr.net/gh/wenhaoclub/blog-assets/images/Java/JVM/head2.jpg
---

# 如何在一台电脑上设置多个github账号
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/wenhaoclub/blog-assets/files/js/css/APlayer.min.css">
<script src="https://cdn.jsdelivr.net/gh/wenhaoclub/blog-assets/files/js/APlayer.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/meting@1.1.0/dist/Meting.min.js"></script>
<div class="aplayer" data-id="1901371647" data-server="netease" data-type="song" data-mode="single" data-autoplay="true"></div>


> 背景：一台PC需要配置两个不同的GitHub账号，实现ssh的连接并push到不同账号下的仓库。
>
> 账号一：fuwenhao594@163.com
>
> 账号二：fuwenhao945@gmail.com



## 第一步：生成密钥

1. 执行： ssh-keygen -t rsa -C "fuwenhao945@gmail.com"
2. 可以指定生成文件命名： /Users/fwh/.ssh/id_rsa_github_gmail
3. 添加私钥：  ssh-add id_rsa_github_gmail
4. 同上步骤生成另一个账号的公钥：
   1. ssh-keygen -t rsa -C "fuwenhao594@163.com"
   2. /Users/fwh/.ssh/id_rsa_github_163_fwh666
   3.  ssh-add id_rsa_github_163_fwh666



## 第二步：将密钥配置到Github账户中

1. 登录Github上，选择个人设置(setting) 
2. 选择SSH and GPG keys 选项
3. New SSH  keys
4. 输入公钥，即生成的id_rsa_github_gmail.pub的文件内容
5. 标题自定义



## 第三步： 编辑配置文件

1. 在/Users/fwh/.ssh目录下创建文件config

2. 输入内容:

   ```yaml
   # github配置-gmail
   Host github.com
       HostName github.com
       User git
       IdentityFile ~/.ssh/id_rsa_github_gmail
   
   #github配置-163-fwh666
   Host github.com
       HostName github.com
       User git
       IdentityFile ~/.ssh/id_rsa_github_163_fwh666
   ```



## 第四步：测试验证

1. 输入： ssh -T git@github.com 
   1. 返回：  Hi wenhaoclub! You've successfully authenticated, but GitHub does not provide shell access.  
   2. 账号对应的用户名称一致，表示成功。
2. 输入： ssh -T git@gitee.com
   1. 返回正常信息







参考地址：

-  一台电脑上同时使用两个github账户  https://www.programminghunter.com/article/6112809308/
- 执行ssh-add时添加私钥到git中报错Could not open a connection to your authentication agent https://blog.csdn.net/Dior_wjy/article/details/79035214

