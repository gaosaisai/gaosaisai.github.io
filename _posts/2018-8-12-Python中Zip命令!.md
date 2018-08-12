---
layout:     post
title:      Python中Zip命令！
subtitle:   Python遇到的第一个问题
date:       2018-08-11
author:     sarah
header-img: img/post-bg-debug.png
catalog: true
tags:
    python
---

## 关于Python中zip命令的使用！！！

关于解决问题这里，真的是折腾了我好久啊~~~没办法谁让我是计算机小白 去自学Python呢555
先附上我执行出来的代码！
#### 代码：
```python
import os
import time

source=['C:\\code']

target_dir='E:\\backup'        

target=target_dir + os.sep + time.strftime('%Y%m%d%H%M%S')+'.zip'


if not os.path.exists(target_dir):
    os.mkdir(target_dir)


zip_command='zip -r {0} {1}'.format(target,
                                    ''.join(source))

print('Zip command is:')
print(zip_command)
print('Running:')

if os.system(zip_command) ==0:
    print('Successful back to',target)

else:
    print('backup FAILED')

```


首先，我对代码进行了修改：
zip_command='zip -r {0} {1}'.format(target,source[0])
当时查博客，看到只备份一个文件夹的时候可以这么做，我就试了，所以没有使用b.join(a)的方法来联结，而是直接采用[]来指定字符串。

接下来，关于zip命令以及添加环境变量的环节。
这时候已经超级没有耐心了，不知道问题出在哪，更加没有心情搞下去了~~~
按python简明教程上的先下载并安装zip命令（我当时保存到C盘）。下载链接:[点击打开链接](http://gnuwin32.sourceforge.net/packages/zip.htm)

然后添加环境变量。感觉这遇到小白学代码的第一个坑了，并不知道环境变量代表啥，百度了一下大概意思是指：在环境变量里添加了软件的安装路径，等到我们想运行软件的时候，他在其他地方找不到会自己去环境变量的路径下查找。然后我就不小心把环境变量里的所有东西全部删除了，并且是无法恢复的那种删除方式，等我运行程序的时候就开始报如下错误了：
'zip' is not recognized as an internal or external command,……
然后尝试把环境变量的添加改变一下，从原来的  C:\Program Files (x86)\GnuWin32\bin，改变成"C:\\Program Files (x86)\\GnuWin32\\bin"，但是还是不行，又重新检查全部得环境变量，把相应的Python，Java等这些都添加上去了，然后尝试了一次重启。问题解决了。
运行出来结果后对之前的操作进行总结，发现自己之前弄不出来的绝大部分原因是:
 > * 环境变量未设置好（80%）是因为这个
 > * 还有对于引号、空格等的使用不清楚。

