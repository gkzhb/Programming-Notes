# Python 教程

[TOC]
来自 [GitHub PythonShare](https://github.com/Yixiaohan/codeparkshare) 中的 [简明 Python 教程](https://woodpecker.org.cn/abyteofpython_cn/chinese/)

## HelloWorld 实例

```python
#!/usr/bin/python
# Filename : helloworld.py
print 'Hello World'
```

* `#`后面的内容表示注释( bash 命令行中同样地用`#`表示注释)
* Python至少应当有第一行那样的特殊形式的注释。它被称作 **组织行** ——源文件的头两个字符是#!，后面跟着一个程序。这行告诉你的Linux/Unix系统当你 **执行** 你的程序的时候，它应该运行哪个解释器。

## 运行 HelloWorld 程序

在 linux 系统中，通过

```terminal
$ chmod a+x helloworld.py
$ ./helloworld.py
```

chmod命令用来改变文件的模式，给系统中所有用户这个源文件的执行许可。

* 文件名改为 `helloworld` 也能执行，因为系统知道它必须用源文件第一行指定的那个**解释器**来运行程序

## 配置环境

```terminal
$ echo $PATH
```

我们能够用 `echo` 命令来显示 PATH变量，用 `$` 给变量名加前缀以向 shell 表示我们需要这个变量的值。我们看到 */home/swaroop/bin* 是PATH变量中的目录之一。swaroop是我的系统中使用的用户名。通常，在你的系统中也会有一个相似的目录。你也可以把你选择的目录添加到PATH变量中去——这可以通过运行 `PATH=$PATH:/home/swaroop/mydir` 完成，其中 */home/swaroop/mydir* 是我想要添加到PATH变量中的目录。

## 获取帮助

通过 `help(Para)` 命令在 Python 命令行中获取 Para 的帮助
eg.

```terminal
>>> help('print')
```

获取 `print` 的帮助
注意到在“print”上使用了引号，那样Python就可以理解我是希望获取关于“print”的帮助而不是想要它打印东西。
> 注：按 `q` 退出帮助
如果你想要获取操作符的帮助，那么你需要正确的设置PYTHONDOCS环境变量。这可以在Linux/Unix中轻松地通过env命令完成。

```terminal
$ env PYTHONDOCS=/usr/share/doc/python-docs-2.3.4/html/ python
```

> 注：在不同发行版中帮助文档位置可能不同

## 基本概念

### 字符串

* 使用单引号(`'`)
* 使用双引号(`"`)
* 使用三引号(`'''`或`"""`)
* 转义符(`\`)，同C语言
	注：在字符串中，行末单独的反斜杠表示字符串在下一行继续，而不是开始一个新的行
* 自然字符串：指示不需要如转义符那样特别处理的字符串
	在字符串前加前缀 `r` 或 `R` 来指定自然字符串
	eg. `r"Newlines are indicated by \n"`
* Unicode 字符串：Unicode 是书写国际文本的标准方法。
	在字符串前加前缀 `u` 或 `U`
* 字符串是不可变的
* 按字面意义级连字符串(同C语言)
	即中间用空白字符隔开的字符串自动合并

> 注：
Python 中没有 char 数据类型
推荐使用自然字符串处理正则表达式 以免去使用很多反斜杠

### 变量

#### 标识符的命名

* 标识符的第一个字符必须是字母表中的字母或者一个下划线
* 标识符名称其他部分可以由字母、下划线或数字组成
* 标识符名称是对大小写敏感的

### 对象

Python 把在程序中用到的任何东西都称为 **对象**
Python 是极其完全地面向对象的
使用变量时只需要给它们赋一个值，不需要声明或定义数据类型
[使用变量和字面意义上的常量](code/var.py 'var.py')

### 逻辑行与物理行

**物理行** 是在编写程序时所看见的
**逻辑行** 是 Python 看见的单个语句
Python 假定每个 物理行 对应一个 逻辑行
如果在一个物理行中使用多于一个逻辑行，则需要使用分号来表明这种用法。分号表示一个逻辑行/语句的结束

> 强烈建议 每个物理行只写一句逻辑行
仅仅当逻辑行太长的时候,在多于一个物理行写一个逻辑行
这些都是为了尽可能避免使用分号，从而让代码更加易读

下面是一个在多个物理行中写一个逻辑行的例子。它被称为 **明确的行连接**

```python
s = 'This is a string. \
This continues the string.'
print s
```

类似地

```python
print \
i
```

效果同以下写法

```python
print i
```

逻辑行中使用了圆括号、方括号或波形括号的时候，可以不需要使用反斜杠，这被称为 **暗示的行连接**

### 缩进

同一层次的语句必须有相同的缩进，每一组这样的语句称为一个 **块**

> 注：错误的缩进会引发错误（如 不能随意地开始新的语句块）

**强烈建议** 在每个缩进层次使用 *单个制表符* 或 *连个或四个空格*
更加重要的是，选择一种风格，然后*一贯地*使用它,即只使用这一种风格

## 运算符与表达式

### 运算符

运算符|名称|说明
:-:|:-:|-
`+`|加|
`-`|减|
`*`|乘|
`**`|幂|
`/`|除|
`//`|取整除|
`%`|取模|
`<<`|左移|位操作
`>>`|右移|
`&`|按位与|
`|`|按位或|
`^`|按位异或|
`~`|按位翻转|
`<`|小于|
`>`|大于|
`<=`|小于等于|
`>=`|大于等于|
`==`|等于|
`!=`|不等于|
`not`|布尔“非”|即C语言中`!`
`and`|布尔“与”|短路计算
`or`|布尔“或”|

### 运算符优先级(从低到高)

运算符|描述
:-:|-
`lamda`|Lamda表达式
`or`|
`and`|
`not x`|
`in`, `not in`|成员测试
`is`, `is not`|同一性测试
`<`, `<=`, `>`, `>=`, `!=`, `==`|比较
`|`|位操作
`^`|
`&`|
`<<`, `>>`|移位
`+`, `-`|
`*`, `/`, `%`|
`+x`, `-x`|正负号
`~x`|按位翻转
`**`|指数
`x.attribute`|属性参考
`x[index]`|下标
`x[index:index]`|寻址段
`f(arguments...)`|函数调用
`(expression,...)`|绑定或元组显示
`[expression,...]`|列表显示
`{key:datum,...}`|字典显示
`'expression,...'`|字符串转换

* 结合规律

	(同级)运算符通常由左向右结合,一些如赋值运算符那样的运算符是由右向左结合的

### 表达式

[使用表达式](code/expression.py 'expression.py')

## 控制流

### if 语句

[使用 if 语句](code/if.py 'if.py')

```python
if expression :
	statement 1
else:
	statement 2
```

```python
if expression 1 :
	statement 1
elif expression 2 :
	statement 2
else:
	statement 3
```

> 注：在 Python 中没有 switch 语句。可以使用 if .. elif .. else 或 使用 字典 来完成同样的工作

### while 语句

while 语句有一个可选的 else 语句，else 块事实上是多余的，把语句跟在 while 语句后，可以取得同样的效果
[使用 while 语句](code/while.py 'while.py')

```python
while expression :
	statement 1
else:	# else 语句是可选的
	statement 2
```

### for 循环

`for .. in` 是另外一个循环语句，它在一**序列**的对象上 **递归** 即逐一使用队列中的每个项目。
[使用 for 语句](code/for.py 'for.py')

```python
for var in range
	statement 1
else:	# else 语句可选
	statement 2
```

> 注：Python 的 for 循环从根本上不同于C的 for 循环

### break 语句

> 注：如果从 for 或 while 循环中 终止，任何对应的循环 else 块将 不 执行

[使用 break 语句](code/break.py 'break.py')

### continue 语句

continue 语句被用来告诉 Python 跳过当前循环块中的剩余语句，然后**继续**进行下一轮循环
[使用 continue 语句](code/continue.py 'continue.py')

## 函数

### 简介

```python
def fun(param...):
	statement
```

[定义函数](code/function1.py 'function1.py')

### 函数形参 和 实参

[使用函数形参](code/func_param.py 'func_param.py')

### 局部变量

[使用局部变量](code/func_local.py 'func_local.py')

* global 语句

[使用 global 语句](code/func_global.py 'func_global.py')

* 如果你想要为一个定义在函数外的变量赋值，那么你就得告诉Python这个变量名不是局部的，而是 **全局** 的。我们使用 `global` 语句完成这一功能。没有 global 语句，是不可能为定义在函数外的变量赋值的。
* 可以使用一个 global 语句指定多个全局变量

<!-- * 你可以使用定义在函数外的变量的值（假设在函数内没有同名的变量）。然而，我并不鼓励你这样做，并且你应该尽量避免这样做，因为这使得程序的读者会不清楚这个变量是在哪里定义的。使用global语句可以清楚地表明变量是在外面的块定义的。 # 测试发现 无法使用外部变量-->

### 默认参数值

在函数定义的形参名后加上赋值运算符和默认值，从而给形参指定默认参数值
但注意，默认参数值应该是不可变的
[使用默认参数值](code/func_default.py 'func_default.py')

> 重要：只有在形参表末尾的那些参数可以有默认参数值

### 关键参数

使用名字（关键字）来给函数指定实参
eg.

```python
def func(a, b=5, c=10):
	statement

func(3, 7)
func(25, c=24)
func(c=25, a=100)
```

优势：

1. 不必担心参数的顺序，使用函数变得更加简单了
2. 假设其他参数都有默认值，我们可以只给想要的那些参数赋值

[使用关键参数](code/func_key.py 'func_key.py')

### return 语句	pass 语句

return 语句用来 **跳出函数**，或从函数 **返回** 一个值
没有返回值的 return 语句等价于 `return None`。`None` 是 Python 中表示没有任何东西的特殊类型。
除非提供 return 语句，每个函数在结尾都暗含有 return None 语句。

pass 语句在 Python 中表示一个空的语句块。

### DocString

**文档字符串**，简称 docstrings，它帮助程序文档更加简单易懂，应尽量使用它。甚至可以在程序运行时，从函数恢复文档字符串
[使用 DocStrings](code/func_doc.py 'func_doc.py')

函数的第一个逻辑行的字符串是这个函数的 **文档字符串**，它同样适用于 **模块** 和 **类**

文档字符串的惯例：

* 是一个多行字符串
* 首行以大写字母开始，句号结尾
* 第二行是空行
* 从第三行开始是详细的描述

使用 `__doc__` (前后都是双下划线)调用函数的文档字符串属性(属于函数的名称)
`help()` 就是抓取函数的 __doc__ 属性,然后整洁地展示出来
**强烈建议** 对所写的任何正式函数编写文档字符串
随你的Python发行版附带的 pydoc 命令，与 help() 类似地使用DocStrings。

## 模块

### 使用 sys 模块(标准库模块)

[使用 sys 模块](code/using_sys.py 'using_sys.py')

