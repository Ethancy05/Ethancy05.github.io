---
title: 记一次win10无法访问openwrt|smb服务的解决方案
copyright_author_href: https:ethancy05.top
date: 2021-02-23 15:19:25
tags: 
   - smb
   - openwrt
categories: Openwrt
description: 记载win10不能访问openwrt的smb服务的解决办法（报错）
---
# 问题描述
openwrt配置好SMB相关服务，在win10网络邻居可以看到OPENWRT主机，但是双击无法访问，错误代码“0x80070035”；而在安卓系统文件管理器客户端则可以正常访问。   
# 解决办法
- 首先确保网络共享及发现已开启、相关服务正常开启并运行
- 新建文本，内容
```
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\LanmanWorkstation\Parameters]

"AllowInsecureGuestAuth"=dword:00000001
```
格式更改为.reg,双击运行

- 如果注册表注册不了，请win键+R 运行 regedit.exe；   
依次点开    HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\LanmanWorkstation\Parameters；   

找到AllowInsecureGuestAuth，双击打开，把数值数据改为 1，然后点击确定。 

- 结束
# 注意

> 有关账户问题可能会涉及，可尝试本地账户
