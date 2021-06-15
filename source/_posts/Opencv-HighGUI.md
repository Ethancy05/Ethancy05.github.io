---
title: Opencv-HighGUI
date: 2021-05-04 19:39:50
tags:
categories: Opencv
description: opencv highgui
---

# 1. 图像的载入、显示和输出到文件
## 1.1imread()函数
### 原型

```
Mat imread(const string& filename, int flags = 1)
```
第一个参数是需要载入的文件路径。   
第二个参数flags是加载图像的颜色类型，一般可以忽略。
> 取-1，已废置，忽略；   
> 取0，始终将图像转换成灰度再返回；   
> 取1，总是转换成彩色再返回；   
> 取2，若载入图像的深度为16位或32位，就返回对应深度图像，否则，转换成8位再返回。

## 1.2 imshow()函数
### 原型
```
void inshow(const string& winname, InputArray mat);
```

第一个参数表示窗口标识名称。   
第二个参数，InputArray类型的Mat，填需要显示的图像

## 1.3 namedWindow函数
### 原型
```
void nameWindow(const string& winname,int flags = WINDOW_AUTOSIZE)
```

第一个参数填写被用作窗口的窗口标识符名称；   
第二个参数，窗口的标识   

**作用：**通过指定名字，创建一个可以作为图像和进度条的容器窗口。

## 1.4 imwrite函数

### 函数声明
```
bool imwrite(const string& filename,InputArray img, const vector<int>& params=vector());
```
第一个参数，文件名，如“123.jpg”；   
第二个参数，Mat类的图像数据；  
第三个参数，保存编码，一般不需填写。  