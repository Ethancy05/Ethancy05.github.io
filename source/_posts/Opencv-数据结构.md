---
title: Opencv-数据结构
date: 2021-05-04 19:40:33
tags:
categories: Opencv
description: 数据结构与基本绘图
---

# 1.Mat-基础图像容器
## 1.1 Mat结构使用
Mat是一个类，有两个数据部分组成：矩阵图（含矩阵尺寸、存储方法、存储地址等信息）和一个指向存储所有像素的指针。

## 1.2显式创建Mat对象的七种方法

> 书中列举了7种，此处记录一种

**使用Mat()构造函数**

例

```
Mat M(2,2,CV_8UC3,Scalar(0,0,255))
```
参数：  
行数、列数、存储元素的数据类型以及每个矩阵点的通道数

# 2.常用数据结构和函数
## 2.1 Point类
用法：

```
Point point；
point.x = 10;
point.y = 8;
```
或者
```
Point point = Point(10,8);
```


## 2.2  Scalar类
Scalar表示具有四个元素的数组，被大量用于传递像素值，一般用三个参数，第四个不用可以不写。   
参数表达式：

```
Scalar(a,b,c)
```
表示，定义的RGB颜色值：红色分量为c，绿色分量为b，蓝色分量为a。

## 2.3 Size类
使用频率最高的是下面这个构造函数
```
Size_(_Tp _width, _Tp _height);
```
另外代码末尾定义了模板类型的高度和宽度：
```
_Tp width,height; //宽度和高度
```
可以用xxx.width ,xxx.height 分别表示xxx的宽度和高度

例：   
```
Size(5,5);//构造出的Size宽度和高度都为5，即xxx.width ,xxx.height 均为5
```

## 2.4 矩形的表示：Rect类
 - Rect类的成员变量有x,y,width,height,分别为矩形左上角的点坐标，和矩形的宽度和高度。      
 - 常用的成员函数有：   
    **Size()**  返回值为Size；   
    **area()**  返回矩形的面积；   
    **contains(Point)**  判断点是否在矩形内；   
    **inside(Rect)** 判断矩形是否在矩形内；   
    **tl()**  返回左上点坐标；      
    **br()**  返回右下点坐标；
- 求矩阵交集与并集： 
```
Rect rect = rect1 & rect2;
Rect rect = rect1 | rect2;
```
- 矩阵的平移和缩放：
```
Rect rectShift = rect + point;
Rect rectScale = rect + size;
```
## 2.5 颜色转变空间：cvtColor()函数
> 作用:实现RBG\HSV\HSI等颜色空间的转换，也可装换为灰度图像

原型

```
void cvtColor(InpuyArray src, OutputArray dst, int code, int dstCn=0)
```
第一个参数为输入图像，第二个参数为输出图像，第三个参数为颜色空间转换的标识符，第四个为目标图像的通道数，0表示取原图像通道数。   

示例：

```
cvtColor(srcImage,dstImage,COLOR_GRAY2BGR);
```
第三个参数具体查表。


# 3.基本图形的绘制（以下函数需要自定义，暂不阐述）
## ~~3.1 DrawEllipse() 函数~~

```
void DrawLine(Mat img, double angle) //绘制不同角度、相同尺寸的椭圆
```
~~其中，函数定义内部使用了WINDOW_WIDTH,这是定义窗口大小的宏   
与之相关的   ~~
```
Point(WINDOW_WIDTH/2 ,WINDOW_WIDTH/2)//中心
Size(WINDOW_WIDTH/4, WINDOW_WIDTH/16) //外矩形框
```
## ~~3.2DrawFilledCircle()~~