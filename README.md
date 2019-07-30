# BBSS 是 宝宝Screen Shared 的简写。
一款windows下的屏幕共享软件。  
本程序使用qt开发。  
BBSS文件夹内部是源码。  
包括客户端源码和服务器端源码。  
  
**BBSSServer  是打包好的服务器端程序。**  
**BBSSClient  是客户端程序。**  
  
要求客户端和服务器端必须是在同一个局域网中。  
  
# 简单说一下实现原理：
# 服务器端
## 第一步
先截屏，截取屏幕后保存到bitmap。
## 第二步
把bitmap宽高都切成10份，一共100块的bitmap。  
把切割后的图片和上次发送的图片比较，如果不一样，然后准备发送  
把需要发送的bitmap转换为jpeg图片。  
把jpeg图片序列号为byte。  
## 第三步
把序列号的图片，通过udp发送到指定的端口。  
  
# 客户端
监听指定的端口，然后接受数据。  
把接受到的数据，反序列化为jpeg图片。  
把jpeg图片，转换为bitmap。  
把小的bitmap合并成大的bitmap。  
然后再客户端显示。  
  