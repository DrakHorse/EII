# Encryption In Image
Version 0.6.4

## 0. 简介
### 0.1 什么是 Encryption In Image
Encryption In Image(简称EII)是一种文本加密技术，其加密方法是将文本隐藏于图片的颜色中，对图片颜色做出细微更改以无损保存文本内容

### 0.2 性能
EII 多次对算法做出优化，基于numpy的算法程序，弥补了Python确实的算法性能

### 0.3 储存率
EII的储存原理是将字符的Unicode编码储存与颜色的RGB数组当中

一张图片最多可储存 2097152(128^3)个字符，因此，若想要储存极限个字符，仅需一张最少(1920x1093)的图片即可

根据使用像素颜色储存字符的算法，EII算法本没有字符数限制，但因算法第2像素储存文本长度信息，但每个像素仅能储存0-2097152(128^3)，因此，有字符数限制，
这可以通过改进算法解决，但目前无需储存过多的字符，因此没有突破限制的必要

### 0.4 版权声明
该项目完全开源免费，开源协议为 GNU GPL 3.0

团队: DarkHorse  https://github.com/DrakHorse/ \
联系：leafjuly@outlook.com

## 1. 运行
### 1.1 交互界面
打开目录下的 encryption_in_image_ui.exe(linux为encryption_in_image_ui) 以运行\
左侧导航栏中点击加密/解密以使用

或者，运行src目录中的 main.py

### 1.2 接口
EII接口完全开源，文件位于src目录下的eii.py

## 2.x 使用
### 2.1 加密使用
加密需要一张原图与文本，在图像界面中，填写好这两项必要内容后，点击加密即可

加密后点保存即可保存加密图

### 2.2 解密使用
解密需要填入加密图与原图，点击解密即可

### 2.3 破坏原图
由于加密后会对原图进行修改，因此，修改后的图片可能被看出被修改的像素数量
因此，很可能泄漏文本长度信息，在破坏原图后即可略微提高安全性

### 2.4 密钥
若图像加密达不到安全性，可以使用EII内置的简单二次加密，在加密时输入密钥，即可使用
密钥必须为一串整数

若加密时使用了密钥，解密时也必须使用，否则解密的文本为无规则的乱码

该加密算法为对称加密，在使用EII前，可以先对字符串进行RSA等非对称安全性更高的密钥加密算法
