# Python 实践

[TOC]

从[第10章](https://woodpecker.org.cn/abyteofpython_cn/chinese/ch10.html)开始

## 解决问题——编写一个 Python 脚本

### 问题

制作一个自动备份程序
工作原理：

1. 需要备份的文件和目录由一个列表指定
1. 备份应该保存在主备份目录中
1. 文件备份成一个zip文件
1. zip存档的名称是当前的日期和时间
1. 使用标准的zip命令

### 解决方案

[版本1](code/backup_ver1.py 'backup_ver1.py')

```python
import os
import time

time.strftime('%Y%m%d%H%M%S')  # 生成时间字符串

os.system(str)  # 在终端输入 str 命令，成功返回0
```

```terminal
$ zip -qr '<zip file>' dir2 dir3 ...
```

* -q 表示安静地工作
* -r 表示对目录递归地工作

[版本2](code/backup_ver2.py 'backup_ver2.py')

```python
os.exists(dir_str)  # 检测 dir_str 目录是否存在
os.mkdir(dir_str)  # 创建目录
os.sep  # 根据操作系统给出目录分隔符 在Linux、Unix下它是'/'，在Windows下它是'\\'，而在Mac OS下它是':'
```

版本3（不工作） 没有指明两个物理行属于同一逻辑行
[版本4（修订）](code/backup_ver4.py 'backup_ver4.py')
在第一个物理行结尾添加反斜杠表示逻辑行未结束

改进：
使用 `tar` 命令替代 `zip` 命令

```terminal
$ tar -cvzf target dir1 dir2 ... -X exclude_file
```

* -c 创建 一个归档
* -v 表示交互，即命令更具交互性
* -z 使用 gzip 滤波器
* -f 强迫创建归档，即如果已经有一个同名文件，它会被替换
* -X 表示文件会被排除在外

更好的方式是使用 Python 标准库中的 zipfile 和 tarfile

### 软件开发过程

1. 什么（分析）
1. 如何（设计）
1. 编写（实施）
1. 测试（测试与调试）
1. 使用（实施或开发）
1. 维护（优化）

开始时实施一个简单的版本。对它进行测试与调试。使用它以确信它如预期那样地工作。再增加任何你想要的特性，根据需要一次次重复这个编写－测试－使用的周期。记住“**软件是长出来的，而不是建造的**”

## 第16章 接下来学习什么?

### 图形软件

Python 的GUI:

* **PyQt**

	Qt工具包的Python绑定

	在Linux下免费使用它，但是在Windows下使用要付费。使用PyQt，可以在Linux/Unix上开发免费的（GPL约定的）软件，而开发具产权的软件则需要付费
	《使用Python语言的GUI编程：Qt版》
* [**PyGObject** *原PyGTK*](https://pygobject.readthedocs.io/en/latest/)

	GTK+工具包的Python绑定, GTK+工具包是构建GNOME的基石

	Glade图形界面设计器是必不可少的，而文档还有待改善。GTK+在Linux上工作得很好，而它的Windows接口还不完整。你可以使用GTK+开发免费和具有产权的软件
* [**wxPython**](https://www.wxpython.org/)

	wxWidgets工具包的Python绑定

	可移植性极佳，可以在Linux、Windows、Mac甚至嵌入式平台上运行。有很多wxPython的IDE，其中包括GUI设计器以及如SPE（Santi's Python Editor）和wxGlade那样的GUI开发器。你可以使用wxPython开发免费和具有产权的软件
* **TkInter**

	现存最老的GUI工具包之一, 具备可移植性, 是标准 Python 发行版的一部分

	[TkInter 文档](http://effbot.org/tkinterbook/)
* 更多选择 [Python.org 上的GUI编程wiki页](http://www.python.org/cgi-bin/moinmoin/GuiProgramming)

选择工具考虑:

1. 是否愿意为GUI工具付费
2. 程序运行的环境是Linux Win 还是多平台上
3. 根据你是Linux下的KDE用户还是GNOME用户来定

### 更多内容

* 《Python实用大全》是一个极有价值的秘诀和技巧集合，它帮助你解决某些使用Python的问题。这是每个Python用户必读的一本书。
* 《迷人的Python》是David Mertz编著的一系列优秀的Python相关文章。
* 《深入理解Python》是给有经验的Python程序员的一本很优秀的书。如果你已经完整地阅读了本书，那么我强烈建议你接下来阅读《深入理解Python》。它覆盖了包括XML处理、单元测试和功能性编程在内的广泛的主题。
* Jython是用Java语言实现的Python解释器。这意味着你可以用Python语言编写程序而同时使用Java库！Jython是一个稳定成熟的软件。如果你也是一个Java程序员，我强烈建议你尝试一下Jython。
* IronPython是用C#语言实现的Python解释器，可以运行在.NET、Mono和DotGNU平台上。这意味着你可以用Python语言编写程序而使用.NET库以及其他由这三种平台提供的库！IronPython还只是一个前期alpha测试软件，现在还只适合用来进行试验。Jim Hugunin，IronPython的开发者，已经加入了微软公司，将在将来全力开发一个完整版本的IronPython。
* Lython是Python语言的Lisp前段。它类似于普通的Lisp语言，会被直接编译为Python字节码，这意味着它能与我们普通的Python代码协同工作。