---
title: python学习笔记
date: 2018/6/16 09:55:22
updated: 2018/12/20 21:26:00
categories:
- python
---

单纯记录一些python学习笔记。

<!-- more -->
# Python Data Structure
1. list
2. dictionary

# 代码规范
1. 输入输出
    - print()会依次打印每个字符串，遇到逗号“,”会输出一个空格
        >print('The quick brown fox', 'jumps over', 'the lazy dog')
    
    - input()输入参数为str类型，如果需要整数型，需要转换
        >     a_str = input()
        >     a_int = int(a)
    
2. 代码格式
    - 每一行都是一个语句，当语句以冒号:结尾时，*缩进的语句视为代码块*。
        >     # print absolute value of an integer:
        >     a = 100
        >	  if a >= 0:
        >     	print(a)
        >     else:
        >     	print(-a)
    - Python程序是大小写敏感的
3. 转义
    - 如果字符串内部既包含'又包含"怎么办？可以用转义字符\\来标识
        >print('I\'m ok.')
    - Python还允许用r''表示''内部的字符串默认不转义
        >     >>> print(r'\\\t\\')
        >     \\\t\\
    - 为了简化，Python允许用'''...'''的格式表示多行内容
        >     print('''line1
        >     line2
        >     line3''')
        >
        >     line1
        >     line2
        >     line3

4. 布尔值
    - 在Python中，可以直接用True、False表示布尔值
        >     >>> 3 > 2
        >     True
        >     >>> 3 > 5
        >     False
    
    - 布尔值可以用and、or和not运算
    - **动态语言/静态语言**，变量本身类型不固定的语言称之为动态语言
     
5. 除法/ 和 //
    -  / 除法计算结果是浮点数，即使是两个整数恰好整除，结果也是浮点数
    - //称为地板除，两个整数的除法仍然是整数

6. Python的整数没有大小限制

7. 数组list tuple
    1. list
        - 如果要取最后一个元素，除了计算索引位置外，还可以用-1做索引，直接获取最后一个元素
    2. tuple一旦初始化就不能修改
    3. 数组/字符串切片
        1. 后10个数：
            >     >>> L[-10:]
            >     [90, 91, 92, 93, 94, 95, 96, 97, 98, 99]
        2. 取前3个元素
            >     >>> L[0:3]
            >     ['Michael', 'Sarah', 'Tracy']
        3. 前10个数，每两个取一个：
            >     >>> L[:10:2]
            >     [0, 2, 4, 6, 8]
        4. 字符串'xxx'也可以看成是一种list
            >     >>> 'ABCDEFG'[:3]
            >     'ABC'
            >     >>> 'ABCDEFG'[::2]
            >     'ACEG'

# 代码结构
1. IF判断
    1. if语句执行有个特点，它是从上往下判断，如果在某个判断上是True，把该判断对应的语句执行后，就忽略掉剩下的elif和else
        >     age = 20
        >     if age >= 6:
        >         print('teenager')
        >     elif age >= 18:
        >         print('adult')
        >     else:
        >         print('kid')

2. For循环迭代
    
    1. 能否迭代判断，通过collections模块的Iterable类型判断：
        >     >>> from collections import Iterable
        >     >>> isinstance('abc', Iterable) # str是否可迭代
        >     True
        >     >>> isinstance([1,2,3], Iterable) # list是否可迭代
        >     True
        >     >>> isinstance(123, Iterable) # 整数是否可迭代
        >     False
    2. 简洁迭代方法：Comprehension推导式

        可以简单漂亮的写出python风格的语法。这些方法很好用，代码会更加简洁漂亮。
        - 第一种方法，使用for循环进行数组填充 
            
            > number_list = []
            > for number in range(1, 6):
            >     number_list.append(number)
            > print(number_list) 
            
        - 第二种方法，使用list进行填充    
            
            > print(list(range(1, 6)))
            
        - 第三种方法，使用推导式
            
            > print([number for number in range(1,6)])
             
        1. list推导式
   
            > **listObj = [expression for item in iterable if condition]**
            
            > print([number*2 - 3 for number in range(2,5)])
            > print([number for number in range(1,6) if number >% 2 == 1])
            
        2. dictionary推导式
            > **dictionaryObj = { key_expression : value_expression for expression in iterable if condition}** 
            
            >   word = 'letters'
            >   letter_counts = {letter: word.count(letter) for letter in set(word)  if letter.lower() not in 'aeiou'}
            >   print(letter_counts)
            
        3. set推导式

            > **set_Obj = {expression for expression in iterable if condition}** 
            
            > print({number for number in range(1,6) if number % 3 == 1})
            
        4. generator 推导式
   
            >   tuples没有推导式的用法，使用()包起來是generator推导式的用法,简单来说就是可以产生像是range()的Object，亦表示可以直接对齐迭代
            
            >   number_thing = (number*3-2 for number in range(1, >6))
            >   print((1,))
            >   print(number_thing)
            >   for number in number_thing:
            >       print(number)

            >   \#或者转为list使用
            >   number_list = list(number_thing)
            >   print(number_list)
            >   print('因为只能使用一次，所以上面这边找不到东西了')

            >   number_thing = (number*3-2 for number in range(1, >6))
            >   number_list = list(number_thing)
            >   print(number_list)
            

3. 双参数迭代
    >     >>> for x, y in [(1, 1), (2, 4), (3, 9)]:
    >     ...     print(x, y)
    >     ...
    >     1 1
    >     2 4
    >     3 9

# python 常用库
- numpy
- matplotlib
- pandas
- xlwt
- xlrd 

# 函数

1. 类型转换函数：hex,int,str,bool,float

2. 数据类型检查函数:isinstance()

    >     def my_abs(x):
    >         if not isinstance(x, (int, float)):
    >             raise TypeError('bad operand type')
    >         if x >= 0:
    >             return x
    >         else:
    >             return -x

3. 返回多个值：
    >     import math
    >     
    >     def move(x, y, step, angle=0):
    >         nx = x + step * math.cos(angle)
    >         ny = y - step * math.sin(angle)
    >         return nx, ny

    >     >>> x, y = move(100, 100, 60, math.pi / 6)
    >     >>> print(x, y)
    >     151.96152422706632 70.0

4. 其实3中只是一种假象，Python函数返回的仍然是单一值。
    >     >>> r = move(100, 100, 60, math.pi / 6)
    >     >>> print(r)
    >     (151.96152422706632, 70.0)



5. 默认参数

    当我们调用power(5)时，相当于调用power(5, 2)

    > def power(x, n=2):



6. 好处

    大多数学生注册时不需要提供年龄和城市，只提供必须的两个参数：
    >     def enroll(name, gender, age=6, city='Beijing'):
    >     enroll('Bob', 'M', 7)
    >     enroll('Adam', 'M', city='Tianjin')

7. 默认参数必须指向不变对象！

    >     def add_end(L=[]):
    >         L.append('END')
    >         return L

    >     >>> add_end()
    >     ['END']
    >     >>> add_end()
    >     ['END', 'END']

8. 避免错误：L指向None,不变对象

    >     def add_end(L=None):
    >         if L is None:
    >             L = []
    >         L.append('END')
    >         return L

9. 可变参数

    >     def calc(numbers):
    >         sum = 0
    >         for n in numbers:
    >             sum = sum + n * n
    >         return sum

    >     >>> calc([1, 2, 3])
    >     14
    >     >>> calc((1, 3, 5, 7))
    >     84

10. 以Python允许你在list或tuple前面加一个*号，把list或tuple的元素变成可变参数传进去：

    >     def calc(*numbers):
    >         sum = 0
    >         for n in numbers:
    >             sum = sum + n * n
    >         return sum

    >     >>> calc(1, 2)
    >     5
    >     >>> calc()
    >     0

    >     >>> nums = [1, 2, 3]
    >     >>> calc(*nums)
    >     14

11. 关键字参数 && 命名关键字参数
 
# 高级特性
1. 列表生成式
    - 建立类似于x个x*x的list
        >     >>>[x * x for x in range(1, 11)]
        >     [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
    - 从XYZ与ABC两组数组组合全排列的
        >     >>>[m + n for m in 'ABC' for n in 'XYZ']
        >     ['AX', 'AY', 'AZ', 'BX', 'BY', 'BZ', 'CX', 'CY', 'CZ']
2. 切片
    1. 切片取值
        - L[m:n]:从列表的第m个元素开始取，一直取到第n个为止(不包括n)
    2. 切片赋值
        - L[1:1] = L2：将L2列表插入到L第一个元素后面 
        >       >>>l1,l2 = [1,2,3] ,[4,5,6]
        >       >>>l1[1:1] = l2
        >       >>>print(l1)
        >       [1,2,4,5,6,3]

# 字符串操作
- 检查是否为字符串
    >     >>> x = 'abc'
    >     >>> y = 123
    >     >>> isinstance(x, str)
    >     True
    >     >>> isinstance(y, str)
    >     False

- 字符串大写变小写s.lower()
    >     >>> L = ['Hello', 'World', 'IBM', 'Apple']
    >     >>> [s.lower() for s in L]
    >     ['hello', 'world', 'ibm', 'apple']