# Ubuntu 18.04 常用配置

## 自定义配置
### 01. 交换左 Control 和 Caps Lock 键（重启后失效）

```
setxkbmap -option ctrl:swapcaps
```
### 02. 将 Caps Lock 键修改为 Control 键（永久生效）

1. 编辑 keyboard 文件

```
sudo vim /etc/default/keyboard
```

2. 将 XKBOPTIONS="" 修改为

```
XKBOPTIONS="ctrl:nocaps"
```

3. 运行如下命令，设置即刻生效，过程中一路回车使用默认配置

```
sudo dpkg-reconfigure keyboard-configuration

```

###  03. 点击启动器图标，窗口最小化

```
gsettings set org.gnome.shell.extensions.dash-to-dock click-action 'minimize'
```


##  基础配置
### 01. 如果 Ubuntu 日期时间显示不正确，执行如下命令（若无问题，忽视即可）

```
sudo timedatectl set-local-rtc 1
```

### 02. 如果因 Ubuntu 和 Windows 的双系统造成了 Windows 系统的时间错误，执行如下命令（若无问题，忽视即可）

1. 先在ubuntu下更新一下时间，确保时间无误

```
sudo apt install ntpdate
sudo ntpdate time.windows.com
```

2. 然后将时间更新到硬件上

```
sudo hwclock --localtime --systohc
```

### 03. 更新系统软件包

```
sudo apt-get update ; sudo apt-get upgrade
```

### 04. 清理未使用的库

```
sudo apt autoremove
```


## 卸载不需要的软件
### 01. libreoffice 不好用，卸载后，稍后安装 wps

```
sudo apt remove libreoffice-common 
```

### 02. 卸载 Amazon 的链接

```
sudo apt remove unity-webapps-common 
```

### 03. 卸载基本不用的自带软件（用的时候再装也来得及）

```
sudo apt­ remove thunderbird totem rhythmbox empathy brasero simple-scan gnome-mahjongg aisleriot gnome-mines cheese transmission-common gnome-orca webbrowser-app gnome-sudoku landscape-client-ui-install
sudo apt remove onboard deja-dup
```

## 常用开发软件
### 01. 安装 Vim

```
sudo apt install vim
```

### 02. 安装编译环境

```
sudo apt install build-essential
```

### 03. 安装 git

```
sudo apt install git
```

### 04. 安装并更换 zsh

1. 安装 zsh

```
sudo apt install zsh
```

2. 切换 shell 为 zsh

```
chsh -s /bin/zsh
```

3. 安装 oh-my-zsh 配置

```
sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

4. 安装语法高亮插件 zsh-syntax-highlighting
```
# 1. clone 插件源码到 oh-my-zsh 的 plugins 目录
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
# 2. 在 ~/.zshrc 中激活该插件
plugins=( [plugins...] zsh-syntax-highlighting)
# 3. 使用 source 命令使配置生效
source ~/.zshrc
```

### 05. 安装 npm
```
sudo apt install npm
```

### 06. 安装 Oracle Java（Option）

```

sudo add-apt-repository ppa:webupd8team/java    
sudo apt update    
sudo apt install oracle-java8-installer   
```

### 07. 安装 axel，用来取代 wget

```
# axel是Linux命令行界面的多线程下载工具，比wget的好处就是可以指定多个线程同时在命令行终端里下载文件
sudo apt install axel
```

### 08. 安装 ExFat 文件系统驱动

```
sudo apt install exfat-fuse exfat-utils
```

### 09. 安装 lnav（Option）

```
# lnav工具是在终端界面看日志的神器
sudo apt install lnav
```

### 10. 安装 gdebi

```
# Gdebi 安装本地的.deb软件包，并自动解决依赖问题
sudo apt install gdebi-core
```

### 11. 安装 AppImageLauncher（Option）

### 12. 安装 Shadowsocks-Qt5

```
axel -n10 https://github.com/shadowsocks/shadowsocks-qt5/releases/download/v3.0.1/Shadowsocks-Qt5-3.0.1-x86_64.AppImage
chmod a+x Shadowsocks-Qt5-x86_64.AppImage
./Shadowsocks-Qt5-x86_64.AppImage
```

### 13. 安装 VSCode

```
axel -n10 https://vscode.cdn.azure.cn/stable/7f3ce96ff4729c91352ae6def877e59c561f4850/code_1.28.2-1539735992_amd64.deb
sudo dpkg -i code_1.28.2-1539735992_amd64.deb
sudo apt install -f
```

### 14. 安装 `pip` 和 `pip3`
```
sudo apt install python-pip
sudo apt install python3-pip
```

### 15. 安装 `sshd`
```
sudo apt install openssh-server
```

## 其他软件
### 01. 安装 Chrome 浏览器 和其插件 SwitchyOmega

1.  下载 Google Chrome

```
axel -n10 https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
```

2. 安装 Google Chrome

```
sudo gdebi google-chrome-stable_current_amd64.deb
```

3. 运行 Google Chrome

```
google-chrome
```

4. 安装并配置插件 SwitchyOmega （略）

### 02. 安装 unrar

```
sudo apt install unrar
```

### 03. 安装搜狗输入法

1. 卸载 ibus

```
sudo apt-get remove ibus
```

2. 清除 ibus 配置

```
sudo apt purge ibus
```

3. 安装 fcitx 输入法框架

```
sudo apt install fcitx-table-wbpy fcitx-config-gtk
```

4. 切换为 fcitx 输入法，并重启系统

```
im-config -n fcitx
sudo shutdown -r now
```

5. 下载搜狗输入法

```
axel -n10 http://cdn2.ime.sogou.com/dl/index/1524572264/sogoupinyin_2.2.0.0108_amd64.deb?st=ryCwKkvb-0zXvtBlhw5q4Q&e=1529739124&fn=sogoupinyin_2.2.0.0108_amd64.deb
```

6. 安装搜狗输入法

```
sudo dpkg -i sogoupinyin_2.2.0.0108_amd64.deb
sudo apt install -f
```

7. 重启，打开 fcitx 输入法配置，能看到 SougouPinyin

```
sudo shutdown -r now
fcitx-config-gtk3
```

### 04. 安装 WPS Office

```
sudo apt install wps-office
```

### 05. 安装截屏软件 shutter

```
sudo apt install shutter
```

### 06. 安装视频播放器

```
sudo apt install vlc
```






