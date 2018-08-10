# Python 教程

[TOC]
来自 [GitHub PythonShare](https://github.com/Yixiaohan/codeparkshare) 中的 [简明 Python 教程](https://woodpecker.org.cn/abyteofpython_cn/chinese/)

## Python 自带帮助文档

```terminal
$ pydoc -p 8000  # python3 对应 pydoc3
pydoc server ready at http://localhost:8000/
```

pydoc 与 pydoc3 位于 /usr/bin 中，分别链接到 pydoc2.7 和 pydoc3.6。如若需要可以自行更改链接使 pydoc 链接到 pydoc3.6

[Python 官方首页](https://www.python.org/)
[Python wiki](https://wiki.python.org/moin/)
[Python 标准文档](https://docs.python.org/3/)

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

使用 Python 命令运行程序时，后面跟着的内容被作为参数传递给程序，Python 为我们把它们存储在字符串列表变量 sys.argv 中

### 字节编译的 .pyc 文件

字节编译的文件与Python变换程序的中间状态有关，字节编译的文件也是与平台无关的

### from..import 语句

如果想在程序中直接输入 argv 而省略 sys. 可以使用 `from sys import argv` 语句
如果想输入所有 sys 模块使用的名字,可以使用 `from sys import *` 语句
一般应该避免使用 from..import 而使用 import 语句，以使你的程序更加易读，也可以避免名称的冲突

### 模块的 `__name__`

[使用模块的 __name__](code/using_name.py)
每个 Python 模块都有它的__name__，如果它是`'__main__'`，这说明这个模块被用户单独运行

### 制造自己的模块

[mymodule.py](code/mymodule.py)
[demo1](code/mymodule_demo.py) [demo2](code/mymodule_demo2.py)

### dir() 函数 del 语句

使用内建的 dir 函数来列出模块定义的标识符（包括函数、类和变量）
del 语句用来 **删除** 一个变量/名称

## 数据结构

### 列表 list

list 是处理一组有序项目的数据结构，是 **可变的** 数据结构，而字符串是不可变的
列表中的项目应该包括在 **方括号** 中，用逗号隔开，且项目数据类型可以不同
[使用列表](code/using_list.py 'using_list.py')
用到的方法有 `len(list)` `list.append(item)` `list.sort()` `list[index]`

* 技巧：在 print 语句结尾使用一个 **逗号** 来消除每个 print 语句自动打印的换行符

### 元组 tuple

tuple 和列表相类似，但是 **不可变的**，通过 **圆括号** 中用逗号分割项目
[使用元组](code/using_tuple.py 'using_tuple.py')
元组也可以通过 len 函数获取长度，说明它也是一个 **序列**

**含有0个或1个项目的元组**：空的元组由一对空的圆括号组成，只有一个元素的元组需要在项目后跟一个 逗号 以区分元组和表达式中带圆括号的对象

print 语句可以使用跟着%符号的项目元组的字符串，这些字符串具备定制的功能，让输出满足某种特定的格式，元组必须按照相同的顺序来对应这些定制。

### 字典 dict

类似于C++中的Map，有 **键** 和 **值**，键必须是唯一的，而且只能用不可变的对象来作为字典的键
键值对标记方式：

```python
d = {key1 : value1, key2 : value2 }
```

注意字典中的键值对是没有顺序的，字典是 dict 类的实例/对象
[使用字典](code/using_dict.py 'using_dict.py')
添加 key/value pair：`dict[key] = value`
删除：`del dict[key]`

`dict.items()` 返回一个元组的列表，其中每个元组包含一对项目
使用 in 操作符或使用 dict.has_key(key) 方法检验一个键值对是否存在
**关键字参数**与字典有联系或相通的地方

### 序列

**列表、元组和字符串都是序列**，序列的两个主要特点是**索引**操作符和**切片**操作符
[使用序列](code/seq.py 'seq.py')
索引为负数时从序列尾开始计算位置，如-1表示最后一个元素
切片操作符：`seq[index1:index2]` 其中 index1/2 是可选的，不指定默认表示从开头开始/到结尾结束

### 参考

变量仅仅 参考 创建的对象,变量名指向存储对象的内存.这被称作名称到对象的绑定
[对象与参考](code/reference.py 'reference.py')
> 注意：赋值一个序列或者其他复杂的对象，应该使用切片操作符来取得拷贝；单纯用等号连接只表示引用同一个对象

### 字符串 str

[字符串的方法](code/str_methods.py 'str_methods.py')
`str.startswith(str)`
`str.find(str)` 返回-1表示找不到子字符串
`str.join(list)` 用 str 连接 list 中项目返回生成的字符串

## 面向对象的编程

### 简介

**类**创建一个新类型，而**对象**这个类的 *实例* 
属于一个对象或类的变量被称为**域**
属于类的函数称为类的**方法**
域和方法合称为类的**属性**
域有两种类型——属于每个实例/类的对象或属于类本身。它们分别被称为**实例变量**和**类变量**
类使用 `class` 关键字创建

### self

类的方法必须有额外的第一个参数名称，一般使用 self 这个名称，但是在调用方法时不为这个参数赋值，Python 自动提供Object 值

### 类

[创建一个类](code/simplestclass.py 'simplestclass.py')
[使用对象的方法](code/method.py 'method.py')

### `__init__` 方法 `__del__` 方法

[使用 `__init__` 方法](code/class_init.py 'class_init.py')
`__init__` 方法类似于C++中的 constructor

### 类与对象的方法

两种类型的域：类的变量和对象的变量
[使用类与对象的变量](code/objvar.py 'objvar.py')
只能使用 self 变量来参考同一个对象的变量和方法，这称作 **属性参考**
用类名参考的变量是类的变量

`__del__` 方法在对象消逝的时候被调用，类似于 destructor 的概念

> 注：Python 中所有的类成员都是 公共 的，所有的方法都是有效的
只有一个例外：以双下划线前缀的数据成员名称会被 Python 的名称管理体系作为私有变量
惯例：以单下划线前缀 标注只想在类或对象中使用的变量

### 继承

重用
多态现象：一个子类型在任何需要父类型的场合可以被替换成父类型，即对象可以被视作是父类的实例
**基本类** 或 **超类** 与 **导出类** 或 **子类**
[使用继承](code/inherit.py 'inherit.py')

```python
class Base:
	define1
	def __init__(self)

class Derived(Base):
	define2
	def __init__(self)
		Base.__init__(self)
		define3
```

Python 不会自动调用基本类的 constructor
基本类是在类定义的时候，在元组之中指明的。
如果在继承元组中列了一个以上的类，那么它就被称作 **多重继承** 。

## 输入/输出

### 文件

file 类方法

* read(file-name-str,mode-str)  # 'r' 读模式(默认模式), 'w' 写模式, 'a' 追加模式 ...
* readline()  # 读取文件的一行,包括行末换行符,长度为0表示 EOF
* write
* close

[使用文件](code/using_file.py 'using_file.py')

### 储存器

Python 提供一个可以在文件中储存任何 Python 对象的标准模块，称为 pickle。之后又可以完整地读取数据，这称为 **持久地** 储存对象
另一个 cPickle 模块功能与 Pickle 模块完全相同，不过用C语言编写，快得多。把这两个模块都简称为 pickle 模块
[储存与取储存](code/pickling.py 'pickling.py')

```python
import A as B  # 用 B 代替 模块名 A
```

cPickle

* dump(object, file)  # dump the object to a file (**储存**)
* load(file)  # read from the file, return the object (**取储存**)

## 异常

### 错误

**错误处理器**: SyntaxError 被引发, 并且检测到的错误位置也将被打印出来
[处理异常](code/try_except.py 'try_except.py')

### try .. except 处理异常

```python
try:
	state1
except error1:
except :
```

except 从句可以专门处理单一的错误或异常，或者一组包括在圆括号内的错误/异常。如果没有给出错误或异常的名称，它会处理 *所有的* 错误和异常

如果某个错误或异常没有被处理，默认的Python处理器就会被调用。它会终止程序的运行，并且打印一个消息

try..catch块可以关联上一个else从句。当没有异常发生的时候，else从句将被执行

### 引发异常

使用 `raise` 语句 引发异常, 要指明错误/异常的名称和伴随异常触发的异常对象
错误和异常应该分别是一个 Error 或 Exception 类的直接或间接的导出类
[引发异常](code/raising.py 'raising.py')

### try .. finally

无论异常发生与否, 都执行 finally 块
若同时使用 except 从句和 finally 块, 需要把一个嵌入另外一个
[使用finally](code/finally.py 'finally.py')

## Python 标准库

### sys 模块

[使用 sys.argv](code/cat.py 'cat.py')
sys|说明
:-:|:-:
sys.argv 列表|命令行参数
sys.stdin|程序的标准输入
sys.stdout|标准输出
sys.stderr|标准错误流
sys.exit()|退出正在运行的程序
sys.version|提供安装的 Python 版本信息
sys.version_info|元组类型

cat: *concatenate*

### os 模块

包含普遍的操作系统功能, 与平台无关

os模块|说明
:-:|-
name 字符串|指示正在使用的平台 Win-'nt' Linux/Unix-'posix'
getcwd( )|返回当前 Python 脚本工作目录路径
getenv( ) putenv( )|分别读取和设置环境变量
listdir( )|返回指定目录下的所有文件和目录名
remove( )|删除一个文件
system( )|运行 shell 命令
linesep 字符串|当前平台使用的行终止符 Win-'\r\n' Linux-'\n' Mac-'\r'
path.split( )|返回一个路径的目录名和文件名 (元组)
path.isfile( ) path.isdir( )|分别检验给出的路径是一个文件还是目录
path.existe( )|检验给出的路径是真得存在