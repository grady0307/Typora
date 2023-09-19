# Python

## 基本语法

### 保留字

```
['False', 'None', 'True', 'and', 'as', 'assert', 'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 'lambda', 'nonlocal', 'not', 'or', 'pass', 'raise', 'return', 'try', 'while', 'with', 'yield']
```

### 注释

- 单行注释#123
- 多行注释
  - **'''** 和 **"""**

### 行与缩进

~~~python
以下代码最后一行语句缩进数的空格数不一致，会导致运行错误：

实例
if True:
    print ("Answer")
    print ("True")
else:
    print ("Answer")
  print ("False")    # 缩进不一致，会导致运行错误
~~~

~~~py
total = item_one + \
        item_two + \
        item_three
#实现多行语句

在 [], {}, 或 () 中的多行语句，不需要使用反斜杠 \，例如：

total = ['item_one', 'item_two', 'item_three',
        'item_four', 'item_five']
~~~

函数之间或类的方法之间用空行分隔，表示一段新的代码的开始。类和函数入口之间也用一行空行分隔，以突出函数入口的开始

### 数字类型

只有

int,bool,float,complex

### 输入

`input("\n\n按下 enter 键后退出。")`

input("\n\n按下 enter 键后退出。")

- **print** 默认输出是换行的，如果要实现不换行需要在变量末尾加上 **end=""**
- `a,b = map( int ,input().split())`
- `a= list( map (int ,input().split()))`

### import

- 将整个模块(somemodule)导入，格式为： **import somemodule**
- 从某个模块中导入某个函数,格式为： **from somemodule import somefunction**

### end

关键字end可以用于将结果输出到同一行，或者在输出的末尾添加不同的字符，实例如下：

~~~python
#!/usr/bin/python3
 
# Fibonacci series: 斐波纳契数列
# 两个元素的总和确定了下一个数
a, b = 0, 1
while b < 1000:
    print(b, end=',')
    a, b = b, a+b
~~~

执行以上程序，输出结果为：

```python
1,1,2,3,5,8,13,21,34,55,89,144,233,377,610,987,
```

### 时间与日期

~~~python
import time
localtime = time.asctime( time.localtime(time.time()) )
print "本地时间为 :", localtime
#时间戳转化为时间元组再转化为格式化的时间
~~~

~~~python
#通过输入日期判断是第几周周几
import datetime

def main():
    date_str = input("请输入日期(02/17):")
    date_str='2020/'+date_str
    date = datetime.datetime.strptime(date_str,"%Y/%m/%d")
    d= date.isocalendar()
    print(d)
~~~



### 实现静态变量

[(28条消息) python实现静态变量_DawnRanger的博客-CSDN博客_python 静态变量](https://blog.csdn.net/dawnranger/article/details/78306878)

## 数据类型

Python 中的变量不需要声明。每个变量在使用前都必须赋值，变量赋值以后该变量才会被创建。

基本数据类型

- Number（数字）
- String（字符串）
- List（列表）
- Tuple（元组）
- Set（集合）
- Dictionary（字典）
- **不可变数据（3 个）：**Number（数字）、String（字符串）、Tuple（元组）；
- **可变数据（3 个）：**List（列表）、Dictionary（字典）、Set（集合）。

### Number

类型判断

- type()不会认为子类是一种父类类型。
- isinstance()会认为子类是一种父类类型。

ps

- 数值的除法包含两个运算符：**/** 返回一个浮点数，**//** 返回一个整数。
- 在混合计算时，Python会把整型转换成为浮点数

- 可以用 **a + bj**，或者 **complex(a,b)** 表示， 复数的实部 **a** 和虚部 **b** 都是浮点型。

### String

- ‘’用法与“”相同

- 使用三引号(**'''** 或 **"""**)可以指定一个多行字符串

- Python 没有单独的字符类型，一个字符就是长度为1的字符串。

- Python 中的字符串有两种索引方式，从左往右以 **0** 开始，从右往左以 **-1** 开始。

- Python 字符串不能被改变。向一个索引位置赋值，比如 **word[0] = 'm'** 会导致错误。

- 字符串的截取的语法格式如下：**变量[头下标:尾下标:步长]**（头包含，尾不包含)

  - \# 第一个参数 -1 表示最后一个元素
      \# 第二个参数为空，表示移动到列表末尾
      \# 第三个参数为步长，-1 表示逆向

- ~~~py
  print('hello\nrunoob')      # 使用反斜杠(\)+n转义特殊字符
  print(r'hello\nrunoob')     # 在字符串前面添加一个 r，表示原始字符串，不会发生转义
  ~~~

### List

- 列表中元素的类型可以不相同，它支持数字，字符串甚至可以包含列表（所谓嵌套）

- `**print** (list)       # 输出完整列表`

- List中的元素是可以改变的。

- ~~~py
  #翻转字符串
  inputWords=inputWords[-1::-1]
  ~~~

### Tuple

- 元组的元素不能修改。元组写在小括号 **()** 里

- 虽然tuple的元素不可改变，但它可以包含可变的对象，比如list列表。

- 构造包含 0 个或 1 个元素的元组比较特殊，所以有一些额外的语法规则：

  ```py
  tup1 = ()    # 空元组
  tup2 = (20,) # 一个元素，需要在元素后添加逗号
  tup3 = (1)  #表示一个int元素
  ```

### Set

- 可以使用大括号 **{ }** 或者 **set()** 函数创建集合，注意：创建一个空集合必须用 **set()** 而不是 **{ }**，因为 **{ }** 是用来创建一个空字典。

- set可以进行集合运算

  - ~~~py
    print(a - b)     # a 和 b 的差集
    print(a | b)     # a 和 b 的并集
    print(a & b)     # a 和 b 的交集
    print(a ^ b)     # a 和 b 中不同时存在的元素
    ~~~

### Dictionary

- 列表是有序的对象集合，字典是无序的对象集合
- 字典当中的元素是通过键来存取的，而不是通过偏移存取
- **{ }** 标识，它是一个无序的 **键(key) : 值(value)** 的集合
- dir.keys()
- dir.items()

| [chr(x)](https://www.runoob.com/python3/python-func-chr.html) | 将一个整数转换为一个字符   |
| ------------------------------------------------------------ | -------------------------- |
| [ord(x)](https://www.runoob.com/python3/python-func-ord.html) | 将一个字符转换为它的整数值 |

- 对多个字典的排序
  - `a.sort(key=operator.itemgetter('age'))`

## 语法

### print

#### %用法

`print('%f' % 1.11)`

`%10s——右对齐，占位符10位
%-10s——左对齐，占位符10位
%.2s——截取2位字符串`

- 打印列表
  - `print(*list1,sep=' ')`

#### format用法

- 位置匹配

  - `'{2}, {1}, {0}'.format(*'abc')  *# 可打乱顺序*`
  - `'c, b, a'`

- 格式转换

  - ~~~python
    print('{:f}'.format(20))
    20.000000
    ~~~

- ==用法变形==

  - ~~~python
    
    # a.format(b)
    >>> "{0} {1}".format("hello","world")
    'hello world'
     
     
    # f"xxxx"
    # 可在字符串前加f以达到格式化的目的，在{}里加入对象，此为format的另一种形式：
     
    a = "hello"
    b = "world"
    f"{a} {b}"
    'hello world'
    ~~~

  - 

### 列表解析式

常规

~~~python
numbers = [number for number in range(10)]
print(numbers)

#生成十个随机数
a=[ random.randint(0,100) for i in range(10)]
~~~

条件判断

~~~python
numbers = [number for number in range(20) if number % 2 == 0]
print(numbers)
~~~

拓展

- 集合解析式

  - ~~~python
    #不包含重复项
    string = "Excellent"
    unique_string = {letter for letter in string}
    print(unique_string)
    ~~~

    

- 字典解析式

  - ~~~python
    string = "Words are but wind"
    word_order = {el: ind+1 for ind, el in enumerate(string.split())}
    print(word_order)
    ~~~

- **海象运算符**

  - 本质上就是一个“赋值表达式”，一边完成赋值工作，一边返回刚刚赋值完的变量。

    1. 无法单独成为一行

    2. 无法单独被赋值语句使用

  - 主要用于

    - ~~~python
      if a:=1 > 0:
      	print("1>0")
      ~~~

    - ~~~python
      numbers = [1, 2, 3, 4, 0, 1]
      i = 0
      while number:=numbers[i] != 0:
      	print("我不是0，循环可以继续")
      	i += 1
      ~~~

    - ~~~python
      b = [(a:=0)+1, a-1, a*1, a/1]
      ~~~

- 嵌套

  - ~~~python
    cities = ['New York', 'Oklahoma', 'Toronto', 'Los Angeles', 'Miami']
    budgets = {city: [0 for x in range(12)] for city in cities}
    print(budgets)
    
    {
        "NewYork": [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
        "Oklahoma": [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
        "Toronto": [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
        "LosAngeles": [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
        "Miami": [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]
    }
    
    ~~~

  - ~~~python
    #常用于创建矩阵
    matrix = [[x for x in range(7)] for y in range(6)]
    print(matrix)
    
    [
        [0, 1, 2, 3, 4, 5, 6],
        [0, 1, 2, 3, 4, 5, 6],
        [0, 1, 2, 3, 4, 5, 6],
        [0, 1, 2, 3, 4, 5, 6],
        [0, 1, 2, 3, 4, 5, 6],
        [0, 1, 2, 3, 4, 5, 6]
    ]
    
    ~~~

  - 

### if

Python 中用 **elif** 代替了 **else if**，所以if语句的关键字为：**if – elif – else**。

**注意：**

- 1、每个条件后面要使用冒号 **:**，表示接下来是满足条件后要执行的语句块。
- 2、使用缩进来划分语句块，相同缩进数的语句在一起组成一个语句块。
- 3、在Python中没有switch – case语句。

### 循环

#### while

```python
while <expr>:
    <statement(s)>
else:
    <additional_statement(s)>
```

#### for

Python for 循环可以遍历任何可迭代对象，如一个列表或者一个字符串。

#### range()

~~~python
>>>for i in range(-10, -100, -30) :
    print(i)
-10
-40
-70
>>>for i,j in range(0,10)
		print(i,j)
    #会报错
~~~

还可以使用range()函数来创建一个列表：

`>>>list(range(5)) [0, 1, 2, 3, 4] >>>`

- break,continue

#### pass

Python pass是空语句，是为了保持程序结构的完整性。

pass 不做任何事情，一般用做占位语句

`...`也行

### 迭代器与生成器

~~~python
list=[1,2,3,4]
it = iter(list)    # 创建迭代器对象
for x in it:
    print (x, end=" ")
~~~

- 对于字典只能迭代 key或value

把一个类作为一个迭代器使用需要在类中实现两个方法 __iter__() 与 __next__() 。

`__iter__`() 方法返回一个特殊的迭代器对象， 这个迭代器对象实现了 `__next__`() 方法并通过 StopIteration 异常标识迭代的完成。

`__next__`() 方法（Python 2 里是 next()）会返回下一个迭代器对象。

- StopIteration 异常用于标识迭代的完成，防止出现无限循环的情况，在 __next__() 方法中我们可以设置在完成指定循环次数后触发 StopIteration 异常来结束迭代。

- `except StopIteration:        sys.exit()`

- 生成器

  - 使用了 yield 的函数被称为生成器（generator）

  - ~~~python
    def foo():
        print("starting...")
        while True:
            res = yield 4
            print("res:",res)
    g = foo()
    print(next(g))
    print("*"*20)
    print(g.send(7))
    
    
    #starting...
    #4
    #********************
    #res: 7
    #48
    #程序执行g.send(7)，程序会从yield关键字那一行继续向下运行，send会把7这个值赋值给res变量
    ~~~

  - 带yield的函数是一个生成器，而不是一个函数了，这个生成器有一个函数就是next函数，next就相当于“下一步”生成哪个数，这一次的next开始的地方是接着上一次的next停止的地方执行的，所以调用next的时候，生成器并不会从foo函数的开始执行，只是接着上一步停止的地方开始，然后遇到yield后，return出要生成的数

### 函数

```python
def 函数名（参数列表）:
    函数体
    
```

- **不可变类型：**类似 C++ 的值传递，如整数、字符串、元组。如 fun(a)，传递的只是 a 的值，没有影响 a 对象本身。如果在 fun(a) 内部修改 a 的值，则是新生成一个 a 的对象。
- **可变类型：**类似 C++ 的引用传递，如 列表，字典。如 fun(la)，则是将 la 真正的传过去，修改后 fun 外部的 la 也会受影响
- 使用关键字参数允许函数调用时参数的顺序与声明时不一致
  - `使用关键字参数允许函数调用时参数的顺序与声明时不一致`
- 默认参数
  - `def printinfo( name, age = 35 ):`
- 不定长参数
  - `def printinfo( arg1, *vartuple ):`
  - 加了星号 ***** 的参数会以元组(tuple)的形式导入，存放所有未命名的变量参数。
  - 加了两个星号 ***\*** 的参数会以字典的形式导入。
  - 如果单独出现星号 *****，则星号 ***** 后的参数必须用关键字传入：

- 匿名函数

  - 使用 **lambda** 来创建匿名函数

  - ```python
    lambda [arg1 [,arg2,.....argn]]:expression
    ```

  - `x = lambda a : a + 10 print(x(5))`


### random

~~~python
import random
random.randint(1,100)# 返回1到100的整数

random.seed(10)
random.random()#使用种子来创建随机数
a= [ random.randint(1,10) for i in range(10)]
~~~

### split()

**split()** 通过指定分隔符对字符串进行切片，并返回分割后的字符串列表（list）

print str.split( );

可用于输入

~~~python
a,b,c  = input().split()
a = int(a)
b= int(b)
c = int(c)
~~~

### assert()

assert（断言）用于判断一个表达式，在表达式条件为 false 的时候触发异常。

`assert 1==2,'1不等于2'`

- 用于单元测试和框架

### map()

- ### 描述

**map()** 会根据提供的函数对指定序列做映射。

第一个参数 function 以参数序列中的每一个元素调用 function 函数，返回包含每次 function 函数返回值的新列表。

- ### 语法

map() 函数语法：

```python
map(function, iterable, ...)''
#一般结合lambda表达式使用
list(map(lambda x : x*x,[1,2,3]))
```

### filter()

**filter()** 函数用于==过滤==序列，过滤掉不符合条件的元素，返回由符合条件元素组成的新列表。

该接收两个参数，第一个为函数，第二个为序列，序列的每个元素作为参数传递给函数进行判断，然后返回 True 或 False，最后将返回 True 的元素放到新列表中。

- function -- 判断函数。
- iterable -- 可迭代对象。

```python
filter(function, iterable)
```

### reduce()

用传给 reduce 中的函数 function（有两个参数）先对集合中的第 1、2 个元素进行操作，得到的结果再与第三个数据用 function 函数运算，最后得到一个结果；

需引入`from functools import reduce`

### sorted()

```python
sorted(iterable, cmp=None, key=None, reverse=False)
```

- iterable -- 可迭代对象。
- cmp -- 比较的函数，这个具有两个参数，参数的值都是从可迭代对象中取出，此函数必须遵守的规则为，大于则返回1，小于则返回-1，等于则返回0。
- key -- 主要是用来进行比较的元素，只有一个参数，具体的函数的参数就是取自于可迭代对象中，指定可迭代对象中的一个元素来进行排序。
- reverse -- 排序规则，reverse = True 降序 ， reverse = False 升序（默认）。

~~~python
students = [('john', 'A', 15), ('jane', 'B', 12), ('dave', 'B', 10)]
sorted(students, key=lambda s: s[2])            # 按年龄排序
[('dave', 'B', 10), ('jane', 'B', 12), ('john', 'A', 15)]
~~~

### eval()

- eval是Python的一个[内置函数](https://so.csdn.net/so/search?q=内置函数&spm=1001.2101.3001.7020)，功能十分强大，这个函数的作用是**，返回传入字符串的表达式的结果。就是说：将字符串当成有效的表达式 来求值 并 返回计算结果。**

- **eval函数就是实现list、dict、tuple与str之间的转化，同样str函数把list，dict，tuple转为为字符串**

- ~~~python
  content = eval(input())
  ~~~

### strip()

- strip() 方法用于移除字符串头尾指定的字符（默认为空格或换行符）或字符序列。

- 只能删除头尾不能删除中间
- `line.strip()`

### getattr()

`getattr()` 是 Python 内置函数之一，用于获取对象的属性值。

~~~python
getattr(object, name[, default])
~~~



## 命名空间和作用域

- **内置名称（built-in names**）， Python 语言内置的名称，比如函数名 abs、char 和异常名称 BaseException、Exception 等等。
- **全局名称（global names）**，模块中定义的名称，记录了模块的变量，包括函数、类、其它导入的模块、模块级的变量和常量。
- **局部名称（local names）**，函数中定义的名称，记录了函数的变量，包括函数的参数和局部定义的变量。（类中定义的也是）

![img](Python.assets/types_namespace-1.png)

作用域

- **L（Local）**：最内层，包含局部变量，比如一个函数/方法内部。
- **E（Enclosing）**：包含了非局部(non-local)也非全局(non-global)的变量。比如两个嵌套函数，一个函数（或类） A 里面又包含了一个函数 B ，那么对于 B 中的名称来说 A 中的作用域就为 nonlocal。
- **G（Global）**：当前脚本的最外层，比如当前模块的全局变量。
- **B（Built-in）**： 包含了内建的变量/关键字等，最后被搜索

## 程序入口

if `__name__ == '__main__'` 就相当于是 Python **模拟的程序入口**。

调用模块时如果运行文件名是当前文件，则从这个入口开始执行；如果模块是被导入的，则不执行

- python -m module_name
  - 将模块当作脚本运行
  - 等同于python /path/to/module.py

## 模块

- 引入
  -  import
  - from ... import ...

- dir()
  - 内置的函数 dir() 可以找到模块内定义的所有名称。以一个字符串列表的形式返回:

- 包

  - 目录只有包含一个叫做 __init__.py 的文件才会被认作是一个包，主要是为了避免一些滥俗的名字（比如叫做 string）不小心的影响搜索路径中的有效模块。

  - 从一个包中导入*

    - 可以在`__init__中修改__all__中的值`

    - ```python
      __all__ = ["echo", "surround", "reverse"]
      #这表示当你使用from sound.effects import *这种用法时，你只会导入包里面这三个子模块。
      ```

### 常用模块

#### pickle

#### cn2an

引入cn2an后，可将阿拉伯数字和中文数字相互转换

~~~python
import cn2an

print(cn2an.cn2an("一百二十三"))  # 默认为strict模式，需要严格符合数字拼写才可以转化
# 123

print(cn2an.cn2an("一二三", "normal"))  # normal模式，可以转化一二三
# 123

print(cn2an.cn2an("1百23", "smart"))  # smart模式，可以转化混合拼写的1百23
# 123

print(cn2an.cn2an("负一百二十三", "strict"))  # 以上三种模式均支持负数
# -123

print(cn2an.cn2an("一点二三", "strict"))  # 以上三种模式均支持小数
# 1.23

import cn2an

print(cn2an.an2cn("123"))  # 默认为low模式，转化为小写中文数字
# 一百二十三

print(cn2an.an2cn("123", "up"))  # up模式，转化为大写中文数字
# 壹佰贰拾叁

print(cn2an.an2cn("123", "rmb"))  # rmb模式，转化为人民币描述
# 壹佰贰拾叁元整

print(cn2an.an2cn("-123", "low"))  # 以上三种模式均支持负数
# 负一百二十三

print(cn2an.an2cn("1.23", "low"))  # 以上三种模式均支持小数
# 一点二三
~~~

#### Counter

~~~python
#用于统计字符出现的个数
>>> from collections import Counter
>>> c = Counter()
>>> for ch in 'programming':
...     c[ch] = c[ch] + 1
...
>>> c
Counter({'g': 2, 'm': 2, 'r': 2, 'a': 1, 'i': 1, 'o': 1, 'n': 1, 'p': 1})

collections.Counter(list)#返回
~~~

#### hashlib

~~~python
#用于密码加密
import hashlib
    m = hashlib.md5()
    m.update(str.encode("utf8"))
    print(m.hexdigest())
~~~



## 文件与IO操作

os操作参考[Python3 OS 文件/目录方法 | 菜鸟教程 (runoob.com)](https://www.runoob.com/python3/python3-os-file-methods.html)

File

- open()
  - `open(file, mode='r')`

- with关键字

  - ~~~python
    with open('./test_runoob.txt', 'w') as file:
        file.write('hello world !')
    #等价于
    file = open('./test_runoob.txt', 'w')
    try:
        file.write('hello world')
    finally:
        file.close()
    #即使用 with 关键字系统会自动调用 f.close() 方法， with 的作用等效于 try/finally 语句是一样的
    ~~~

    ~~~python
    f=os.path.basename(path) #获取文件名或目录名，如若path='d://c//a.txt'，那么f='a.txt'
    f=os.path.join(path,filename)#合成路径
    os.path.isfile(path)#判断是否是普通文件，还是路径，若是普通文件返回True
    files = os.listdir(path)#获取path路径下的所有文件和文件路径，返回列表
    mt =time.ctime(os.path.getmtime(path))#获取文件时间
    
    fs = os.stat(path)
    size = size +fs.st_size#获取wen'j
    ~~~
    
    

## 高级函数

1.函数接受的参数是一个函数名或者多个函数名; 

2.函数的返回值是一个函数名;

- 变量可以指向函数
- 函数名可以作为变量

## 闭包（Closure)

~~~python
def lazy_sum(*args):
    def sum():
        ax = 0
        for n in args:
            ax = ax + n
        return ax
    return sum
~~~

- **内部函数****sum****可以引用外部函数****lazy_sum****的参数和局部变量**，当lazy_sum返回函数sum时，相关参数和变量都保存在返回的函数中

- 当我们调用lazy_sum()时，每次调用都会返回一个新的函数，即使传入相同的参数

- **函数本身作为返回值,相当于,我们返回的是一个==计算规则==;** 

  **这个规则在定义的时候,不占用太多资源；**

  **只有在调用时,才加载资源; 通常称这种方式为"懒惰加载";**

- 内部函数是闭包函数

闭包机制产生的条件：

**1 在一个外函数中定义了一个内函数。**

**2 内函数里运用了外函数的临时变量。**

**3 并且外函数的返回值是内函数的引用。**

- 如果外函数在结束的时候发现有自己的临时变量将来会在内部函数中用到，就把这个临时变量绑定给了内部函数，然后自己再结束
- 返回的函数并没有立刻执行，而是直到调用了f()才执行
- 返回函数不要引用任何循环变量，或者后续会发生变化的变量

### 装饰器

~~~python
#对于有参宇返回值的装饰器
def timmer(func):
    @wraps(func)
    def wrapper(*args,**kwargs):
        start_time = time.time()
        res=func(*args,**kwargs)         #res来接收home函数的返回值
        stop_time=time.time()
        print('run time is %s' %(stop_time-start_time))
        return res  
    return wrapper
~~~

- 多个装饰器装饰一个函数,**其执行顺序是从下往上**
- 通过使用 `@wraps(func)` 装饰器，你可以确保装饰后的函数保留原始函数的所有重要元信息。这样做的好处有：
  1. 保留函数签名：可以保持被装饰函数的参数列表，使得它可以正确地被其他代码调用。
  2. 保留函数名称：使得装饰后的函数在调试和日志记录时能够显示正确的函数名，而不是装饰器函数的名称。
  3. 保留文档字符串：使得装饰后的函数在文档生成工具中可以正确地显示原始函数的文档注释。

## 面向对象

### 类的方法

在类的内部，使用 **def** 关键字来定义一个方法，与一般函数定义不同，类方法必须包含参数 self, 且为第一个参数，self 代表的是类的实例。

~~~python
class people:
    name = ''
    def __init__ (self,n):
		self.name =  n
    def pt(self):
        print(f'{name}')
~~~

### 类的继承

~~~python
class student(peoople):
    def __init__(self,n):
		people.__init__(self,n)
~~~

`super().myMethod() #用子类对象调用父类已被覆盖的方法`

### 类属性与方法

- 私有属性
  - __private_sttrs
  - 在类内部使用时self.__private_attrs
    - __开头即为私有
- 私有方法
  - __private_method

## 数据库操作

~~~python
#链接
db = MySQLdb.connect(
    host='localhost',
    port=3306,
    db='student',
    user='root',
    passwd='123456'
)
cursor = db.cursor()#游标对象
cursor.execute("select * from student")#执行sql语句
res = cursor.fetchall()#获取执行查询后的所有结果
~~~

- `db.commit()`：提交事务，将更改保存到数据库中。

- ```python
  #连接数据库
  engine = create_engine(
      "mysql+pymysql://root:123456@127.0.0.1:3306/studymysql?charset=utf8mb4",
      max_overflow=5)
  ```

- `data = cursor.fetchone()`，它用于从数据库结果集中获取一行数据。

- `max_overflow` 的值为 5，则最多可以创建额外的 5 个连接。


### ORM映射类

作用：用于将关系型数据库中的表和行映射到面向对象的编程语言中的类和对象

![img](Python.assets/v2-984901c2903ec83589d641fb930ed738_r.jpg)

创建

~~~python
from sqlalchemy import Column, Integer, String
from sqlalchemy.ext.declarative import declarative_base

Base = declarative_base()
class Students(Base):
    __tablename__ = 'students'  # 表的名称

    # 表的结构
    id = Column(String(20), primary_key=True)
    name = Column(String(20))
	classID = Column(Integer)

# 创建一个DBSession类型
DBSession = sessionmaker(bind=engine)
~~~

自定义类方法

~~~python
class Students(Base):
    __tablename__ = 'student'  # 表的名称

    # 表的结构
    id = Column(String(20), primary_key=True)
    name = Column(String(20))

    @classmethod
    def add(cls, **kwargs):

        try:
            student = Students(
                id=kwargs.get('id'),
                name=kwargs.get('name')
            )
            session.add(student)
            session.commit()
        except Exception as e:
            session.rollback()
            return {'code': 2001, 'message': "数据库操作异常", 'error': str(e)}
~~~

- `cls` 是一个惯用的命名约定，表示当前类（Class）。在类方法中，第一个参数通常被命名为 `cls`，用于引用类本身。
- `**kwargs` 是一种特殊的参数传递方式，用于接收关键字参数（Keyword Arguments）。`kwargs` 是一个字典（dictionary），其中的键（key）是关键字参数的名称，对应的值（value）是关键字参数的值。

~~~python
def _asdict(self):
    return {c.key: getattr(self, c.key)
            for c in inspect(self).mapper.column_attrs}
~~~

- `inspect(self)`：使用 `inspect()` 函数来获取 ORM 映射类实例对象的映射信息

### 数据库会话

~~~python
from sqlalchemy import create_engine
from sqlalchemy.orm import sessionmaker

engine = create_engine('数据库连接字符串')
Session = sessionmaker(bind=engine)
session = Session()

new_student = Students(id='22222222',name='wanglaowu')
session.add(new_student)
session.commit()

session.query(Students).filter(Students.id =="22222222").delete()
session.commit()
session.close()
~~~

- 当在会话中执行多个数据库操作时，如果其中一个操作出现错误或异常，您可以使用 `session.rollback()` 方法将事务回滚到操作开始前的状态，撤销之前的所有修改。
- `outerjoin()` 是一个 SQLAlchemy 查询构造器方法，用于执行外连接操作。它将 `ClassInfo` 表与 `Students` 表进行外连接，并使用 `and_()` 来指定连接条件。
- `with_for_update()` 是 SQLAlchemy 中的一个查询构造器方法，用于在查询期间对结果集加锁，以防止并发修改。
  - `res = session.query(cls).filter(*filter_list).with_for_update()`
  - delete和update要上锁

controller建立会话

models建立ORM映射类

### ROW类

在 SQLAlchemy 中，`Row` 类型是一个特殊的类，用于表示查询结果的行（row）数据。

当执行查询操作时，SQLAlchemy 返回的结果集通常是一组行的集合。每一行都被表示为一个 `Row` 对象，其中包含查询结果中每个列的值。

`Row` 类型是 SQLAlchemy 在低级别 API 中的一种轻量级对象表示方式，与 ORM 映射类的实例对象有所不同。它是一种临时的数据结构，主要用于处理查询结果而不需要完整的 ORM 映射类定义。

### 封装成controller

- get

  - ~~~python
        def get(cls, **kwargs):        
            try:
                filter_list = []
                if kwargs.get('studentID'):
                    filter_list.append(cls.studentID == kwargs.get('studentID'))
                if kwargs.get('name'):
                    filter_list.append(cls.name == kwargs.get('name'))
                if kwargs.get('classID') is not None:
                    filter_list.append(cls.classID == kwargs.get('classID'))
                if kwargs.get('age') is not None:
                    filter_list.append(cls.age == kwargs.get('age'))
                
                page = int(kwargs.get('Page', 1))
                size = int(kwargs.get('Size', 10))
    
                student_info = session.query(cls).filter(*filter_list)
    
                count = student_info.count()
                pages = math.ceil(count / size)
                student_info = student_info.limit(size).offset((page - 1) * size).all()
    
                results = cls.to_dict(student_info)
                return {'code': "200", 'message': "成功！", 'totalCount': count, 'totalPage': pages, 'data': results}
    
            except Exception as e:
                return {'code': "5001", 'message': "数据库错误", 'data': {'error': str(e)}}
            finally:
                session.close()
    ~~~

  - 要进行分页操作