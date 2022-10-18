

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

```
1,1,2,3,5,8,13,21,34,55,89,144,233,377,610,987,
```

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

| [chr(x)](https://www.runoob.com/python3/python-func-chr.html) | 将一个整数转换为一个字符   |
| ------------------------------------------------------------ | -------------------------- |
| [ord(x)](https://www.runoob.com/python3/python-func-ord.html) | 将一个字符转换为它的整数值 |

## 语法

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
>>>
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
-  不定长参数
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