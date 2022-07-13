---
layout: post
lock: need
title: 科学上网指南
date: 2022-03-01 21:41:03
author: 文浩
img:
coverImg: https://baseoss.fuwenhao.club/banner/09.jpg
top: false
cover: false
toc: false
mathjax: false
summary:
tags:
  - VPN
  - Shadowsocks
categories: [VPN]
description: 科学上网指南
keywords: wenhao  , 文浩  , 似水似流年  , wenhaoclub  , fuwenhao.club , plus.fuwenhao.club  ,文浩的博客 , 似水似流年的博客
link: https://cdn.jsdelivr.net/gh/wenhaoclub/blog-assets/images/Java/JVM/head2.jpg
---
# 科学上网操作指南

## 准备工作：

1. 国外的VPS服务器：
   1. 本人选择搬瓦工网址购买服务器； 
   2. 获取服务器的IP地址；
2. 个人PC的Xshell连接工具：
   1. 个人笔记本是MacBook Pro
   2. 连接工具是SecureCRT
3. SSH连接上VPS服务器：
   1. 不多赘述；



## 开始搭建：

### 采用Xray技术搭建：

1. 新购买服务器需要安装URL命令：

   ```shell
   yum install -y curl
   ```

2. 执行Xray脚本：

   1. 注意：此脚本是选择参考搭建的脚本。如果脚本网址失效，参看备份的xray.sh脚本信息。

   ```shell
   bash <(curl -sL https://cdn.jsdelivr.net/gh/Misaka-blog/Xray-script@master/xray.sh)
   
   ```

   1. <img src="https://v2xtls.org/wp-content/uploads/2020/12/Xray%E4%B8%80%E9%94%AE%E5%AE%89%E8%A3%85%E8%84%9A%E6%9C%AC.jpg" alt="Xray一键安装脚本" style="zoom:50%;" />
   2. 选择： xray-vmess+ws+TLS（推荐）
   3. 确认是否满足条件：需要输入带伪装的域名；
      1. 关于带伪装的域名操作：
      2. 域名解析： 
         1. 个人是阿里云域名管理：xray.fuwenhao.club解析到VPS的IP上；
   4. 伪装网站类型
      1. 默认选择
   5. 最终会输出Vmess信息，保存文本备用：
      1. <img src="https://gitee.com/fwh666/fwh_images/raw/master/fwh_images/image-20220322111357609.png" alt="image-20220322111357609" style="zoom:50%;" />

3. 验证服务搭建是否正常：

   1. 输入伪装域名：xray.fuwenhao.club  能回显默认伪装静态网站，表现服务搭建成功。



#### 客户端配置登录：

1. 下载ClassX客户端：https://github.com/yichengchen/clashX/releases

2. 配置yaml文件：

   1. 下载yaml配置文件：https://v2xtls.org/clash_template2.yaml

   2. <img src="https://gitee.com/fwh666/fwh_images/raw/master/fwh_images/image-20220322134325598.png" alt="image-20220322134325598" style="zoom: 33%;" />

   3. 主要配置Vmess内容：

      1. 在host上配置上伪装域名 xray.fuwenhao.club ，如果没有就注释掉

   4. ClassX客户端：

      1. 选择-配置-选择刚配置的yaml文件

      2. 选择-控制台：

      3. PROXY选择使用的节点：默认是“自动选择快速节点”，也可以指定使用某个节点。

         “Final”选择默认规则：DIRECT表示直连，PROXY走代理。个人建议使用直连，网站打不开再选择代理。

         其他看不懂的东西保持默认就好了。

         在主界面点击“设置”，设置启用系统代理和选择代理模式：

         代理模式有全局、规则和直连，(可以认为)对应其他客户端的全局模式、PAC模式和禁用系统代理。**绝大多数情况建议使用规则模式**。



### 采用Shadowsockes技术搭建：

1. 执行脚本：

   1. 注意：此脚本是选择参考搭建的脚本。如果脚本网址失效，参看备份的ssr.sh脚本信息。

   ```shell
   bash <(curl -sL https://s.hijk.art/ssr.sh)
   ```

2. 选择安装：

3. 安装成功输出内容：

4. <img src="https://gitee.com/fwh666/fwh_images/raw/master/fwh_images/image-20220322135100475.png" alt="image-20220322135100475" style="zoom: 33%;" />

#### 客户端配置登录：

1. 下载shadowsockes客户端：https://github.com/qinyuhang/ShadowsocksX-NG-R/releases
2. 配置：
   1. 选择PAC自动模式；
   2. 服务器设置：
      1. 输入地址、端口号、加密方式、密码信息后。
3. 开启shadowsockes客户端；
4. 登录上网验证是否成功。





## 参考网址：



- 搬瓦工服务器购买指南：
  - https://www.banwagongzw.com/2.html
  - https://www.bawagon.com/vps-paypal/

- ShadowsocksR/SSR一键脚本：
  - https://v2xtls.org/shadowsocksr-ssr%e4%b8%80%e9%94%ae%e8%84%9a%e6%9c%ac/
  - 客户端官网下载地址：https://github.com/qinyuhang/ShadowsocksX-NG-R/releases
  - SSR版ShadowsocksX-NG配置教程：https://v2xtls.org/ssr%e7%89%88shadowsocksx-ng%e9%85%8d%e7%bd%ae%e6%95%99%e7%a8%8b/
- Xray一键脚本：
  - https://v2xtls.org/xray%e4%b8%80%e9%94%ae%e8%84%9a%e6%9c%ac/
  - ClashX客户端官网下载地址：https://github.com/yichengchen/clashX/releases
  - ClashX操作教程：https://v2xtls.org/clashx%e9%85%8d%e7%bd%aev2ray%e6%95%99%e7%a8%8b/



## 备份文件：

- Xray的执行脚本和客户端安装包：
  - 个人服务器目录：/home/fwh/FileBak/
- Shadowsockers执行脚本和客户端安装包：
  - 个人服务器目录：/home/fwh/FileBak/ 后续搞成网址形式
- 关于完整版的操作文章：
  - 个人服务器目录：/home/fwh/FileBak