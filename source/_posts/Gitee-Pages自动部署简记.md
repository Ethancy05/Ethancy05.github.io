---
title: Gitee Pages自动部署简记
date: 2021-02-17 17:08:36
tags: hexo
description: 博客备份
---
# 前言 #

我的博客是部署在github上的，但是在国内的访问速度并不理想。替代方案有国内的平台Gitee、Coding，本文主要讲述使用Gitee作为国内替代方案，并实现自动部署GiteePages。
# 为什么选择Gitee #

我是最先了解到Gitee，但是尝试后发现Gitee并不能自动部署你的Git Pages，需要Pro版才能每当你更新源代码时，才能自动部署。而且Gitee也不支持自定义域名。  
而后又了解到coding，也有很多人使用Github+Coding双线方案。在Coding上部署时发现，现在的Coding静态网站是和腾讯云联系在一起，涉及到付费，并且未备案的域名也不能使用国内CDN，于是放弃了。
之后就在搜索有没有自动部署GiteePages的方案。

# 自动部署方法 #
> 参考的是Github上的项目 <https://github.com/yanglbme/gitee-pages-action>



