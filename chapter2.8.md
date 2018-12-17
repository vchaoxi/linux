# 附录-vim分屏操作

## vim分屏操作

分屏操作:

```python

sp: 上下分屏,后可跟文件名 

vsp: 左右分屏,后可跟文件名

Ctr+w+w: 在多个窗口切换

```

启动分屏:

1.使用大写O参数进行垂直分屏

```python

$ vim -On file1 file2 ...

```

2.使用小写o参数进行水平分屏

```python

$ vim -on file1 file2 ...

```

注: n是数字，表示分屏的数量,n要大于等于文件个数

关闭分屏

1.关闭当前窗口

```python

ctrl+w c

```

2.关闭当前窗口，如果只剩最后一个，则退出vim

```python

ctrl+w q

```

编辑中分屏

1.上下分割当前打开的文件

```python

ctrl+w s

```

2.上下分割，并打开一个新的文件

```python

:sp filename

```

3.左右分割当前打开的文件

```python

ctrl+w v

```

4.左右分割，并打开一个新的文件

```python

:vsp filename

```

分屏编辑中光标的移动

vi中的光标键是h,j,k,l,要在各个屏之间切换，只需要先按一下ctrl+w

1.把光标移动到上边的屏

```python

ctrl+w k

```

2.把光标移动到下边的屏

```python

ctrl+w j

```

3.把光标移动到右边的屏

```python

ctrl+w l

```

4.把光标移动到左边的屏

```python

ctrl+w h

```

5.把光标移动到下一个的屏

```python

ctrl+w w

```

移动分屏

1.向上移动

```python

ctrl+w K

```

2.向下移动

```python

ctrl+w J

```

3.向右移动

```python

ctrl+w L

```

4.向左移动

```python

ctrl+w H

```

屏幕尺寸

1.增加高度

```python

ctrl+w +

```

2.减少高度

```python

ctrl+w -

```

3.让所有屏的高度一致

```python

ctrl+w =

```

4.左加宽度

```python

ctrl+w >

```

5.右加宽度

```python

ctrl+w <

```

6.右增加n宽 (如：n=30)

```python

ctrl+w n <

```

## vim打造IDE

### 简洁版IDE

```python

C+p: 生成tags
C+]: 跳转到函数定义
C+t：从函数定义返回

C+o：在左侧打开文件列表
F4:  在右侧打开函数列表

C+n：补齐函数，向下翻

```

vimrc是vim的配置文件，可以修改两个位置

```python

1. /etc/vim/vimrc

2.~/.vimrc

~/.vimrc优先级高

```