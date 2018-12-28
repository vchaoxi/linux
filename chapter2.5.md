# Linux常用服务器构建-ftp服务器

## ftp服务器

FTP 是File Transfer Protocol（文件传输协议）的英文简称，而中文简称为“文传协议”。

用于Internet上的控制文件的双向传输。

同时，它也是一个应用程序（Application）。基于不同的操作系统有不同的FTP应用程序，而所有这些应用程序都遵守同一种协议以传输文件。

在FTP的使用当中，用户经常遇到两个概念："下载"（Download）和"上传"（Upload）。

"下载"文件就是从远程主机拷贝文件至自己的计算机上；

"上传"文件就是将文件从自己的计算机中拷贝至远程主机上。用Internet语言来说，用户可通过客户机程序向（从）远程主机上传（下载）文件。

![](/assets/01-linux基础-99.jpeg)

1.安装vsftpd服务器

```python

sudo apt-get install vsftpd

```

![](/assets/01-linux基础-100.png)

![](/assets/01-linux基础-101.png)

2.配置vsftpd.conf文件

```python

sudo vi /etc/vsftpd.conf

```

![](/assets/01-linux基础-102.png)

![](/assets/01-linux基础-103.png)

![](/assets/01-linux基础-104.png)

![](/assets/01-linux基础-105.png)

![](/assets/01-linux基础-106.png)

![](/assets/01-linux基础-108.png)

![](/assets/01-linux基础-107.png)

![](/assets/01-linux基础-109.png)

![](/assets/01-linux基础-110.png)

![](/assets/01-linux基础-111.png)

![](/assets/01-linux基础-112.png)

3.测试上传功能，登陆ftp服务器

```python

ftp  <IP>

```



4.上传命令，可以把文件上传到ftp服务器

```python

put <somefile>

```

5.下载命令，可以把ftp服务器上的文件下载到本地

```python

get <somefile>

```

## 图形界面的ftp客户端(filezilla)

