# Linux常用服务器构建-samba

## 1. 介绍

Samba是在Linux和UNIX系统上实现SMB协议的一个免费软件，能够完成在windows、mac操作系统下访问linux系统下的共享文件

## 2. 安装

使用apt命令安装samba

![](/assets/Snip20161218_1.png)

## 3. 配置

### 3.1 创建存放共享文件的路径

在home路径下操作：

![](/assets/Snip20161218_2.png)

修改其权限：

![](/assets/Snip20161218_4.png)

修改samba的配置文件：

![](/assets/Snip20161218_5.png)

![](/assets/Snip20161219_121.png)

### 3.2 创建samba账户

![](/assets/Snip20161218_7.png)

![](/assets/Snip20161218_17.png)

## 4 重启samba

当对配置进行了更新，需要重启samba软件后才可生效

重启命令如下：

![](/assets/Snip20161218_20.png)

## 5. 访问共享文件

### 5.1 mac下访问方式

![](/assets/Snip20161218_11.png)

![](/assets/Snip20161218_13.png)

![](/assets/Snip20161218_14.png)

![](/assets/Snip20161218_16.png)

### 5.2 windows下访问方式

![](/assets/Snip20161218_18.png)

![](/assets/Snip20161218_19.png)