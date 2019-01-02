# find & grep 
## 什么是find和grep
find 和 grep 是 linux 中最常用的两个搜索函数。关于用find还是用grep，只要掌握一个原则就可以了：凡是搜索文件名，就用find，凡是搜索文件内容，就要grep（当然为了提高效率可以结合find使用，后面会讲）。

## find基本用法
### 搜索文件名
例：在当前目录搜索名称为vchaoxi.txt的文件

> `find ./ –name vchaoxi.txt`


`参数 –a  –o  –not`
分别为与、或、非的意思，相当于find中的逻辑运算

例1：在当前目录搜索除了vchaoxi.py文件以外其他.py文件

> `find ./ –not –name vchaoxi.py –a –name "*.py"`


例2：在当前目录搜索名称为vchaoxi或wechaoxi的文件

> `find ./ -name vchaoxi -o -name wechaoxi`


`参数 –prune`
> 该参数的作用是忽略某个文件，即不在这个文件夹里搜索文件以提高效率，该参数常和-o 一起使用

例：在当前目录且不在tmp文件中搜索名为vchaoxi*的文件并打印

> `find ./ -name tmp -prune -o -name vchaoxi* -print`


> 最后的-print: 如果不加-print，结果中除了打印不在tmp文件中的vchaoxi*文件之外还会打印find . -name tmp这个搜索出来的结果
> 上例中 * 为通配符

`参数 –exec`
> find命令后加入该参数可以对搜索结果进行处理

例：在当前目录搜索所有.txt文件并将其删除

> `find ./ –name "*.txt" –exec rm –rf {} \;`


> `{}` 表示前面搜索的结果， `；` 表示命令结束， `\` 用于转义且前面必须要有空格

`参数 –type`
> 该参数用于指定查找文件的类型

例1：在当前目录查找文件名包含vchaoxi的文件夹

> `find ./ –name “*vchaoxi*" –type d`


-type参数后跟指定的文件类型，d为文件夹，f为普通文件

`参数 –size`
> 用于指定查找文件的大小（单位b、k、M、G）

例1：在当前目录查找所有小于10k的文件

> `find ./ –size -10k`

例2：在当前目录查找所有大于10M的文件

> `find ./ –size +10M`


## find搜索匹配进阶及RE（正则表达式）

### -name      是将文件名去匹配而不是文件的输出结果
支持的正则表达式解释如下：
```
*        ： 代表任意字符（可以没有字符）
？       :  代表任意单个字符
[]       ： 代表括号内的任意字符，[abc]可以匹配a\b\c某个字符
[a-z]    ： 可以匹配a-z的某个字母
[A-Z]    ： 可以匹配A-Z的某个字符
[0-9]    ： 可以匹配0-9的某个数字 same as [[:digit:]]
如果方括号内加入“ ^ ”，则表示不去匹配里面的字符
[^a-z]   ： 表示不匹配a-z的某个字符。
```

例1      ： 在当前目录中搜素不以a、b、c开头的所有文件
> `find ./ –name "[^abc]*"`

例2：在当前目录中搜索以大写字母或数字开头的所有文件
> `find ./ -name “[A-Z0-9]*”`


### -regex是将文件的输出结果进行匹配而不是文件名


-regex相对于-name的优势是可以使用正规的RE

例：搜索所有输出结果包含vchaoxi的文件（哪怕文件名不包含vchaoxi，只要该文件在vchaoxi目录中也都可以被搜索到）

> `find . –regex “.*vchaoxi.*”`

> 这里匹配所有字符是 .* 而不是 *

简单的RE符号及用法

```
[]     : 与之前find中描述相同，在此不予赘述
.      : 表示任意单个字符
？     : 表示前面的字符出现一次或零次
+      : 表示前面的字符至少出现一次
*      : 表示前面的字符出现零次或多次
()     : 将表示的字符括起来后面跟量词
```

例：在当前目录搜索输出结果至少出现一次vchaoxi的所有文件
> `find ./ -regex “.*\(vchaoxi\)+.*”`
> ()   要用\转义，该例将会打印出所有包含vchaoxi的目录及其中的文件


例：在当前目录搜索所有文件名末尾为py或pyc的文件
> find ./ -regex “.*py|.*pyc”
> |    逻辑或，可以搜索两个条件         

## grep基本用法
例1：在vchaoxi.mk文件中搜索包含dorayo的行

> `grep “dorayo” vchaoxi.mk`

例2：在当前目录的所有文件中搜索包含dorayo的行

> `grep "dorayo" ./*`

`参数 –r`
> 表示在当前目录和子目录中循环搜索（加入该参数可以不用指定文件，意为已经指定了当前目录及子目录中的所有文件）

例：在当前目录及子目录中的所有文件中搜索包含res的行

> grep –r “res”

`参数 –n`
> 输出的结果打印行号

例：在当前目录及子目录中的所有文件中搜索包含res的行并打印行号

> `grep –nr “res”`

`参数 –i`
> 查找匹配忽略大小写，默认状态下会匹配大小写

`参数 –l（L的小写，不是大写的i）`
> 输出结果只显示文件名，不显示行

`参数 -s`
> 不显示不存在或无匹配文件的错误信息

`参数 –w`
> 可以精确匹配后面的单词，而不是字符串匹配

`参数 -v`
> 逆反模式，即输出不匹配的所有行

`参数 -o`
> 仅显示匹配到的字符串，而不是输出匹配到的行

### grep中RE的使用以及egrep
find中所说的REgrep这边都可以使用，后面不再赘述，需要注意的是 + 、？要用\转义

egrep是grep的进化版，改进了许多grep中不方便之处如下：

egrep使用RE符号 + ， ？ ， | （或） , {} 时不用转义，如果要用其本身则需要转义

所以，如果需要用到RE的话，尽量选择egrep

简单的RE符号及用法
```
< , >       ：分别表示单词的开始和结束，将单词放入其中可以精确匹配（类似于-w）
例：搜索精确匹配Dialer单词的行（形如DialerActivity则不会匹配）
 egrep –nr “\<Dialer\>”
> \>表示的是单词的结束，单词可能是下一个单词，这里写的时候需要注意

 ^ , $          ： 分别表示行的开始和结束（^ 用在 [ ] 内表示不匹配其中的字符，注意区别）

{n}             ： 表示前面的字符匹配n次
{n,m}           : 表示前面的字符匹配n-m次
{,m}            : 表示前面的字符至多匹配的m次
{n,}            : 表示前面的字符至少匹配n次
[ ]             : 方括号使用和find一样
[[:space:]]     : 表示空格或tab
```

例1：当前目录搜索包含access your和Phone permission的行（如果中间的字符串看不清或者不方便写或者可能是转义符如换行符等，可以用.*代替）
> `egrep –nr “access your.*Phone permission”`


## find和grep的在搜索中的实际应用-进阶
find和grep结合使用
在实际应用中，find和grep配合使用将会非常方便而迅速，先看一个例子：

```
function jgrep()
{
    find . -name .repo -prune -o -name .git -prune -o -name out -prune -o -type f -name "*\.java" -print0 | xargs -0 grep --color -n "$@"
}
```

这个是位于Android源码build/envsetup.sh中的jgrep函数，用于搜索java文件内容，是经常使用的一个函数，是find结合grep的典型案例。如果已经确定了搜索内容在java文件中，那么相比于直接用grep进行全局搜索，这种先搜索所有的java文件，再在其中搜索内容的方式可以显著提高效率。

我们先来解析一下这个函数：
```
find .                  ：在当前目录搜索
-o                      : 或，并列多个条件
-name .repo –prune       ： 忽略.repo目录（git库相关）
-name .git –prune        ： 忽略.git目录（git库相关）
-name out –prune         ： 忽略out目录（编译生成的目录）
-type f                 ：指定文件类型为普通文件
-name "*\.java"          ： 指定匹配的文件名为.java文件
-print0 | xargs -0       ： 忽略搜索中可能出现的错误信息，并将搜索到的文件作为结果向后传递并继续执行
grep --color –n               ：用grep在之前搜索到的文件中进行内容搜索，输出行号并标识颜色
"$@"                              ：表示在使用jgrep函数时输入的参数，这里即为grep搜索的内容
```

## find、grep中xargs 和 | 的使用
```
|       ：管道命令符，它会将前一个命令的标准输出作为后一个命令的标准输入，这  里不展开了，具体作用可以自行寻找资料学习。
xargs   ： 如果仅使用 | ，那么前面的结果会作为输入直接传递到后面的命令中，而使用xargs，就可以使前面的结果作为参数传递到后面的命令中，而这个特性对于find和grep而言十分重要。
```
下面举几个例子来说明find中xargs的用法：
例1：在当前目录中搜索所有AndroidManifest.xml文件并在其中搜索DialtactsActivity
> `find . –name AndroidManifest.xml | xargs grep –n –color “DialtactsActivity”`

> 说明：该例是xargs最基本的用法，如果将xargs去掉，那么grep搜索的内容是find输出的结果内容而非结果文件


例2：在当前目录搜索所有的values-zh-rCN文件目录并在其中搜索所有的strings.xml文件（即所有中文字符串存放位置），然后在搜索到的strings.xml文件中搜索“通话”字符串
> `find . –type d –name “values-zh-rCN” | xargs -i find {} –name “strings.xml” | xargs grep –n –-color '通话'`

该例中xargs后使用了-i参数，该参数的作用是可以将后面命令中的 {} 符号视为前面find搜索的结果文件。本例中连续使用了两次xargs进行结果的传递。

例3：在当前目录中的所有mk文件中搜索ro.build.type
> `find . –type f –name “*.mk” –print0 | xargs -0 grep –n –color “ro.build.type”`

本例中和之前提到的jgrep函数都是用了 –print0 | xargs -0进行结果传递而非单纯使用xargs，这样做的好处是如果find搜索会忽略可能出现的错误，使最终输出的结果更清晰，因此在使用xargs时建议按照–print0 | xargs -0方式写命令。

