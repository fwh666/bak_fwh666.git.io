---
layout: post
lock: need
title: Jekyll&&Hexo发博文说明
date: 2020-12-21 21:41:03
author: 文浩
img:
coverImg: http://oes.fuwenhao.club/images/banner/09.jpg
top: false
cover: false
toc: false
mathjax: false
summary:
tags:
  - Jekyll
  - Hexo
categories: [Jekyll]
description: Jekyll&&Hexo发博文说明
keywords: wenhao  , 文浩  , 似水似流年  , wenhaoclub  , fuwenhao.club , plus.fuwenhao.club  ,文浩的博客 , 似水似流年的博客
link: https://cdn.jsdelivr.net/gh/wenhaoclub/blog-assets/images/Java/JVM/head2.jpg
---
# 序：
>PS：👇背景音乐会自动播放的。不行就戳一下👇
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/wenhaoclub/blog-assets/files/js/css/APlayer.min.css">
<script src="https://cdn.jsdelivr.net/gh/wenhaoclub/blog-assets/files/js/APlayer.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/meting@1.1.0/dist/Meting.min.js"></script>
<div class="aplayer" data-id="1495058484" data-server="netease" data-type="song" data-mode="single" data-autoplay="true"></div>

# Jekyll发布说明：
 - 本地博文存储路径： /Users/fwh/A_FWH/SourceTree/wenhaoclub/_posts
	 - 快捷命令：cdwenhaoclub
 - 文章内容编辑：注意标头格式
 

```
---
layout: post
lock: need
title: 记--疫情期间短暂厨艺生涯😪
categories: [Life]
description: 自己买菜，自己洗菜，自己烧菜，自己吃菜
keywords: wenhao, 文浩 ,  fuwenhao.club ,  wenhaoclub , 做饭
link: https://cdn.jsdelivr.net/gh/wenhaoclub/blog-assets/images/Java/JVM/head2.jpg
---
```

 - 内容上传到GitHub上
 

```
博客远程地址： https://github.com/wenhaoclub/wenhaoclub.github.io.git

关于无法上传问题： 参考网址：https://juejin.cn/post/6844904193170341896
1. 打开 https://github.com.ipaddress.com  
2. 打开 https://ipaddress.com/website/github.global.ssl.fastly.net#ipinfo
3. 打开 https://ipaddress.com/website/assets-cdn.github.com
4. sudo vim /etc/hosts  更新相应的IP地址刷新，重新上传GitHub。
```

 - 去个人服务器上执行：shblog
	 - 快捷命令：alias shblog='sh /home/fwh/Blog/blog.sh'
 - 去网址检查是否有最新的文章内容： https://fuwenhao.club

--- 

# Hexo发布说明：
- 本地博文存储路径：/Users/fwh/A_FWH/Hexo_fwh_20191127/MyBlog/source/_posts
	- 快捷命令：cdmyblog
- 文章内容编辑：注意标头格式

```
---
layout: post
lock: need
title: 记--新的环境-新的开始-新的自己
date: 2020-07-04 21:41:03
author: 文浩
tags:
  - 改变
categories: [Life]
description: 回炉塑造中……
keywords: wenhao  , 文浩  , 似水似流年  , wenhaoclub  , fuwenhao.club , 文浩的博客
---
```
- 文章内容上传到Github上

```
hexo  clean   :  清除本地页面数据；
hexo  g   :  本地生成最新页面；
hexo  s   :  本地浏览器刘览；
hexo  d  ：本地内容上传到GitHub上；
```

- 去个人服务器上执行：shHexoblog
	 - 快捷命令：alias shHexoblog='sh /home/fwh/Blog/hexoBlog.sh'
- 去网址检查是否有最新的文章内容： https://plus.fuwenhao.club

丧，每个人都会有，但要努力，要学习，要优秀。

Fighting。

