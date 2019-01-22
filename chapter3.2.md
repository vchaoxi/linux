# linux 下 Vim 集成配置使用及说明

> `已在 Ubuntu 18.04 下测试成功`

[TOC]

## 安装

执行如下命令

```
git clone --depth=1 https://github.com/amix/vimrc.git ~/.vim_runtime
sh ~/.vim_runtime/install_awesome_vimrc.sh
```

## 自定义配置
### 设置 Emacs 操作习惯

1. 执行如下命令，创建并编辑自定义配置文件 

```
vi ~/.vim_runtime/my_configs.vim
```

2. 在里面粘贴如下内容

```
" emacs 操作习惯
inoremap <C-e> <END>
inoremap <C-a> <HOME>
inoremap <C-f> <Right>
inoremap <C-b> <Left>
inoremap <C-n> <Down>
inoremap <C-p> <Up>
```

3. 执行如下命令，让配置生效

```
source ~/.vimrc
```

## 使用说明
### Key Mapping
- `leader`键是`,`
- 也就是所有见到的`<leader>`就是`,`

### 常见快捷键
- 查看和管理 buffers `<leader>o`
- 关闭当前 buffer(s) `<leader>bd` 和 `<leader>ba`
- 查看最近打开文件 `<leader>f`
- 快速查找文件或 buffer `<leader>j` 或 `<ctrl>f`
- 打开或关闭 NERD Tree `<leader>nn`
- 聚焦编辑模式 `<leader>z`
- 查找内容 `/` 或 `<space>`
- 取消高亮 `<leader><cr>`
- `split`和`vsplit`切割的窗口见跳转 `<C-j/k/h/l>`
- 打开新的标签页 `<leader>tn`
- 关闭当前标签页 `<leader>tc`

### 编辑快捷键
- 注释 gcc / gcu
- 缩进 << >>

### 分屏操作
> sp: 上下分屏,后可跟文件名 
> vsp: 左右分屏,后可跟文件名

**分屏编辑中光标的移动**

vi中的光标键是h,j,k,l,要在各个屏之间切换，只需要先按一下ctrl+w

1.把光标移动到上边的屏
> ctrl+w k

2.把光标移动到下边的屏
> ctrl+w j

3.把光标移动到右边的屏
> ctrl+w l

4.把光标移动到左边的屏
> ctrl+w h

5.把光标移动到下一个的屏
> ctrl+w w


**关闭当前分屏窗口**

关闭当前窗口
> ctrl+w c

关闭当前窗口，如果只剩最后一个，则退出vim
> ctrl+w q

**启动分屏：**

1.使用大写O参数进行垂直分屏
> $ vim -On file1 file2 ...
> 注: n是数字，表示分屏的数量,n要大于等于文件个数

2.使用小写o参数进行水平分屏
> $ vim -on file1 file2 ...
> 注: n是数字，表示分屏的数量,n要大于等于文件个数



**分屏屏幕尺寸调整：**

1.增加高度
> ctrl+w +

2.减少高度
> ctrl+w -

3.让所有屏的高度一致
> ctrl+w =

4.左加宽度
> ctrl+w >

5.右加宽度
> ctrl+w <

6.右增加n宽 (如：n=30)
> ctrl+w n <

## 第三方插件
### Python 开发插件安装
1. YouCompleteMe

