---
title: 记openwrt折腾设置
date: 2021-02-16 10:34:00
tags: openwrt 软路由
categories: openwrt
---
# 前言 #
**简单记录一下折腾openwrt期间遇到的一些问题和简单设置**

## 简单设置 ##
- 方式：旁网关
- 配置：x86_64旧笔记本，U盘启动，单网口

1. 刷好系统后，ssh连接openwrt或在笔记本进入交互界面，输入命令更改软路由ip（与自家主网关同网段）
	    
    `vim /etc/config/network`

2. 输入i进行编辑，编辑完后按ESC退出编辑，输入:wq以返回交互界面
3. 软路由连路由器，同网段主机登陆后台
4. 找到“网络-接口”，修改Lan口。
5. 简单设置如下： 静态地址，ip已更改，网关改为主网关，DNS设置为主网关，关闭DHCP服务，桥接等
   ![](https://cdn.jsdelivr.net/gh/Ethancy05/CDN-for-blog@1.0/BlogImage/记openwrt折腾设置/1.png)

----------
## 小结 ##
到此处可能有些人已经可以上网了（从机设置不赘述）

但我在这还是遇到了问题，手机（或电脑）接入openwrt网关不能上网

后来查询资料，总结了两点

## 解决办法 ##

- 方法一：设置防火墙规则   
   `iptables -t nat -I POSTROUTING -j MASQUERADE`

- 方法二：增加wan口，绑定lan，取消桥接

## 参考链接 ##
[https://blog.csdn.net/vmp_jin/article/details/111300822](https://blog.csdn.net/vmp_jin/article/details/111300822 "旁路由设置的正确方式")
