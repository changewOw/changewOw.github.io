---
title: 3d Gaussians Splatting
date: 2024-12-16 13:31:21
tags: "3dgs"
categories: "3dgs"
comments: false
---


[解析1](https://zhuanlan.zhihu.com/p/661569671)
[数学推导](https://zhuanlan.zhihu.com/p/666465701)
[解析2](https://www.zhihu.com/question/626506306)


### 1D Gaussian

1D普通高斯函数

### 1D->3D
3D高斯可以用来表示空间中的任意形状的椭球  
3D高斯函数引入了协方差矩阵，用u来控制椭球中心，用协方差来控制椭球的伸缩和旋转  

### 初始化椭球
对于协方差矩阵有要求，需要协方差半正定，这类约束无法进行数值优化  
所以可以通过先缩放后旋转来获得协方差矩阵  
也即，$ \Sigma=RSS^TR^T $，也就需要一个向量s，和一个四元数q来表达  
通过直接优化s和q来间接优化协方差矩阵  

### Splatting
Rasterization光栅化意味着将三维三角形project到平面并像素化  
Splatting则意味着把3D椭球project到平面，就像雪球击打在平面留下一个印记  

### 
在三角mesh的project过程中，三个离散点，不会出现不线性，不正定，不仿射等问题  
3D高斯的基础单元是一个3D分布，project变换不再仿射，论文使用了 $ \Sigma'=JW\Sigma W^TJ^T $   



