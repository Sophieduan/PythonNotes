# PythonNotes

1. Operator

如果变量写在同一行,将会指向同一个对象

>>> a=4444; b=4444;   # 写在同一行
>>> a is b
True
>>> a == b
True

>>> c = 5555   # 写在不同一行
>>> d = 5555   # 写在不同一行
>>> c is d
False
>>> c == d
True
>>> 
以上情况在交互模式会出现，使用脚本运行，不管是否同一行，都是指向同一个地址：
a = 4444; b = 4444
print(a is b)          # true

c = 5555
d = 5555
print(c is d)          # true


type还可以用 isinstance 来判断：

a = 111
isinstance(a, int)
True

isinstance 和 type 的区别在于：

>>> class A:
...     pass
... 
>>> class B(A):
...     pass
... 
>>> isinstance(A(), A)
True
>>> type(A()) == A
False
>>> isinstance(B(), A)
True
>>> type(B()) == A 
False
区别就是:

 type()不会认为子类是一种父类类型。
 isinstance()会认为子类是一种父类类型。


2. Loop
while 循环	在给定的判断条件为 true 时执行循环体，否则退出循环体。
for 循环	重复执行语句
嵌套循环	你可以在while循环体中嵌套for循环

break 语句	在语句块执行过程中终止循环，并且跳出整个循环
continue 语句	在语句块执行过程中终止当前循环，跳出该次循环，执行下一次循环。
pass 语句	pass是空语句，是为了保持程序结构的完整性。


2.1. While
http://www.runoob.com/python/python-while-loop.html
+ continue
+ break
+ 无限循环
+ while...else...
-> 同行：
flag = 1
 
while (flag): print 'Given flag is really true!'
 
print "Good bye!"


2.2. for
http://www.runoob.com/python/python-for-loop.html
以上实例我们使用了内置函数 len() 和 range(),函数 len() 返回列表的长度，即元素的个数。 range返回一个序列的数。
EG: 
for letter in 'Python':     # 第一个实例
   print '当前字母 :', letter
 
fruits = ['banana', 'apple',  'mango']
for fruit in fruits:        # 第二个实例
   print '当前水果 :', fruit
 
print "Good bye!"

->
当前字母 : P
当前字母 : y
当前字母 : t
当前字母 : h
当前字母 : o
当前字母 : n
当前水果 : banana
当前水果 : apple
当前水果 : mango
Good bye!

通过序列索引迭代
fruits = ['banana', 'apple',  'mango']
for index in range(len(fruits)):
   print '当前水果 :', fruits[index]
 
print "Good bye!"
->
当前水果 : banana
当前水果 : apple
当前水果 : mango
Good bye!


+ else
else 中的语句会在循环正常执行完（即 for 不是通过 break 跳出而中断的）的情况下执行，while … else 也是一样。
for num in range(10,20):  # 迭代 10 到 20 之间的数字
   for i in range(2,num): # 根据因子迭代
      if num%i == 0:      # 确定第一个因子
         j=num/i          # 计算第二个因子
         print '%d 等于 %d * %d' % (num,i,j)
         break            # 跳出当前循环
   else:                  # 循环的 else 部分
      print num, '是一个质数'
->
10 等于 2 * 5
11 是一个质数
12 等于 2 * 6
13 是一个质数
14 等于 2 * 7
15 等于 3 * 5
16 等于 2 * 8
17 是一个质数
18 等于 2 * 9
19 是一个质数

+ 使用内置 enumerate 函数进行遍历:

for index, item in enumerate(sequence):
    process(index, item)
=>
>>> sequence = [12, 34, 34, 23, 45, 76, 89]
>>> for i, j in enumerate(sequence):
...     print i,j
->
0 12
1 34
2 34
3 23
4 45
5 76
6 89

+ for循环只能执行range内两数字相减次数
for i in range(1,10):     # 只能执行9次,判断循环终止条件是 >= 第二个数字 10 就不再执行 和 其他语言的 i=1 to 10 不同
    print 'i=:', i
for i in range(1,1)这样是不会进入循环的
 
+ for实现step效果递增
for i in xrange(0,10,2):
    print(i)
+ for实现step效果递减
for i in xrange(10,0,-2):
    print(i)



2.3. 循环嵌套
见practise

#break 语句
break语句，就像在C语言中，打破了最小封闭for或while循环。
break语句用来终止循环语句，即循环条件没有False条件或者序列还没被完全递归完，也会停止执行循环语句。
break语句用在while和for循环中。
如果您使用嵌套循环，break语句将停止执行最深层的循环，并开始执行下一行代码。
EG：
for letter in 'Python':     # 第一个实例
   if letter == 'h':
      break
   print '当前字母 :', letter
  
var = 10                    # 第二个实例
while var > 0:              
   print '当前变量值 :', var
   var = var -1
   if var == 5:   # 当变量 var 等于 5 时退出循环
      break
 
print "Good bye!"


2.4. continue 语句
continue 语句是一个删除的效果，他的存在是为了删除满足循环条件下的某些不需要的成分
语句用来告诉Python跳过当前循环的剩余语句，然后继续进行下一轮循环。
continue语句用在while和for循环中。
EG：
for letter in 'Python':     # 第一个实例
   if letter == 'h':
      continue
   print '当前字母 :', letter
 
var = 10                    # 第二个实例
while var > 0:              
   var = var -1
   if var == 5:
      continue
   print '当前变量值 :', var
print "Good bye!"
->
当前字母 : P
当前字母 : y
当前字母 : t
当前字母 : o
当前字母 : n
当前变量值 : 9
当前变量值 : 8
当前变量值 : 7
当前变量值 : 6
当前变量值 : 4
当前变量值 : 3
当前变量值 : 2
当前变量值 : 1
当前变量值 : 0
Good bye!



2.5. pass 语句
Python pass是空语句，是为了保持程序结构的完整性。
pass 不做任何事情，一般用做占位语句。

for letter in 'Python':
   if letter == 'h':
      pass
      print '这是 pass 块'
   print '当前字母 :', letter

print "Good bye!"
->
当前字母 : P
当前字母 : y
当前字母 : t
这是 pass 块
当前字母 : h
当前字母 : o
当前字母 : n
Good bye!


3. Number(数字)
Number 数据类型用于存储数值。
数据类型是不允许改变的,这就意味着如果改变 Number 数据类型的值，将重新分配内存空间。
以下实例在变量赋值时 Number 对象将被创建：

del语句删除一些 Number 对象引用。
del var
del var_a, var_b

+ Python 支持四种不同的数值类型：

整型(Int) - 通常被称为是整型或整数，是正或负整数，不带小数点。
长整型(long integers) - 无限大小的整数，整数最后是一个大写或小写的L。
浮点型(floating point real values) - 浮点型由整数部分与小数部分组成，浮点型也可以使用科学计数法表示（2.5e2 = 2.5 x 102 = 250）
复数(complex numbers) - 复数由实数部分和虚数部分构成，可以用a + bj,或者complex(a,b)表示， 复数的实部a和虚部b都是浮点型。

Python还支持复数，复数由实数部分和虚数部分构成，可以用a + bj,或者complex(a,b)表示， 复数的实部a和虚部b都是浮点型

+ Python math 模块、cmath 模块
Python math 模块提供了许多对浮点数的数学运算函数。
Python cmath 模块包含了一些用于复数运算的函数。
cmath 模块的函数跟 math 模块函数基本一致，区别是 cmath 模块运算的是复数，math 模块运算的是数学运算。
->
abs(x)	返回数字的绝对值，如abs(-10) 返回 10
ceil(x)	返回数字的上入整数，如math.ceil(4.1) 返回 5
cmp(x, y)	如果 x < y 返回 -1, 如果 x == y 返回 0, 如果 x > y 返回 1；cmp(x, y) 函数在 python3.x 中不可用，可用以下函数替代：operator.lt(a, b)           lt(a, b) 相当于 a < b
fabs(x)	返回数字的绝对值，如math.fabs(-10) 返回10.0
floor(x)	返回数字的下舍整数，如math.floor(4.9)返回 4
max(x1, x2,...)	返回给定参数的最大值，参数可以为序列。
min(x1, x2,...)	返回给定参数的最小值，参数可以为序列。
modf(x)	返回x的整数部分与小数部分，两部分的数值符号与x相同，整数部分以浮点型表示。
round(x [,n])	返回浮点数x的四舍五入值，如给出n值，则代表舍入到小数点后的位数。
->
 abs() 是一个内置函数，而 fabs() 在 math 模块中定义的。
 fabs() 函数只适用于 float 和 integer 类型，而 abs() 也适用于复数。
+ Python随机数函数
choice(seq)	从序列的元素中随机挑选一个元素，比如random.choice(range(10))，从0到9中随机挑选一个整数。
random()	随机生成下一个实数，它在[0,1)范围内。
shuffle(lst)	将序列的所有元素随机排序
uniform(x, y)	随机生成下一个实数，它在[x,y]范围内。

+ range()函数
>>> range(1,5)        # 代表从1到5(不包含5)
[1, 2, 3, 4]
>>> range(1,5,2)      # 代表从1到5，间隔2(不包含5)
[1, 3]
>>> range(5)          # 代表从0到5(不包含5)
[0, 1, 2, 3, 4]
->
import random

print( random.randint(1,10) )        # 产生 1 到 10 的一个整数型随机数  
print( random.random() )             # 产生 0 到 1 之间的随机浮点数
print( random.uniform(1.1,5.4) )     # 产生  1.1 到 5.4 之间的随机浮点数，区间可以不是整数
print( random.choice('tomorrow') )   # 从序列中随机选取一个元素
print( random.randrange(1,100,2) )   # 生成从1到100的间隔为2的随机整数

a=[1,3,5,6,7]                # 将序列a中的元素顺序打乱
random.shuffle(a)
print(a)


4. 字符串
+ Python访问字符串中的值

+ Python字符串更新
var1 = 'Hello World!' 
print "更新字符串 :- ", var1[:6] + 'Runoob!'
->
更新字符串 :-  Hello Runoob!

+ Python转义字符
\(在行尾时)	续行符
\\	反斜杠符号
\'	单引号
\"	双引号
\a	响铃
\b	退格(Backspace)
\e	转义
\000	空
\n	换行
\r	回车


+ Python字符串运算符
a = "Hello"
b = "Python"
 
print "a + b 输出结果：", a + b 
print "a * 2 输出结果：", a * 2 
print "a[1] 输出结果：", a[1] 
print "a[1:4] 输出结果：", a[1:4] 
 
if( "H" in a) :
    print "H 在变量 a 中" 
else :
    print "H 不在变量 a 中" 
 
if( "M" not in a) :
    print "M 不在变量 a 中" 
else :
    print "M 在变量 a 中"
 
print r'\n'
print R'\n'

+ Python 字符串格式化
尽管这样可能会用到非常复杂的表达式，但最基本的用法是将一个值插入到一个有字符串格式符 %s 的字符串中。
 %s	 格式化字符串
 *	定义宽度或者小数点精度
 %d	 格式化整数
 %f	 格式化浮点数字，可指定小数点后的精度
 <sp>	在正数前面显示空格
print "My name is %s and weight is %d kg!" % ('Zara', 21) 
->
My name is Zara and weight is 21 kg!
>>> print("%6.3f" % 2.3)
->
 2.300
第一个 % 后面的内容为显示的格式说明，6 为显示宽度，3 为小数点位数，f 为浮点数类型
第二个 % 后面为显示的内容来源，输出结果右对齐，2.300 长度为 5，故前面有一空格 
 
+ format 格式化函数
基本语法是通过 {} 和 : 来代替以前的 % 。
format 函数可以接受不限个参数，位置可以不按顺序。
>>>"{} {}".format("hello", "world")    # 不设置指定位置，按默认顺序
'hello world'
>>> "{0} {1}".format("hello", "world")  # 设置指定位置
'hello world'
>>> "{1} {0} {1}".format("hello", "world")  # 设置指定位置
'world hello world'

通过字典设置参数
site = {"name": "菜鸟教程", "url": "www.runoob.com"}
print("网站名：{name}, 地址 {url}".format(**site))
 
通过列表索引设置参数
my_list = ['菜鸟教程', 'www.runoob.com']
print("网站名：{0[0]}, 地址 {0[1]}".format(my_list))  # "0" 是必须的
->
网站名：菜鸟教程, 地址 www.runoob.com

如果在 str.format() 调用时使用关键字参数，可以通过参数名来引用值:

>>> print('This {food} is {adjective}.'.format(
...       food='spam', adjective='absolutely horrible'))
This spam is absolutely horrible.

位置参数和关键字参数可以随意组合:
>>> print('The story of {0}, {1}, and {other}.'.format('Bill', 'Manfred', other='Georg')) 
The story of Bill, Manfred, and Georg.

字段名后允许可选的 : 和格式指令。这允许对值的格式化加以更深入的控制。下例将 Pi 转为三位精度。
>>> import math
>>> print('The value of PI is approximately {0:.3f}.'.format(math.pi))
The value of PI is approximately 3.142.

在字段后的 : 后面加一个整数会限定该字段的最小宽度，这在美化表格时很有用:
>>> table = {'Sjoerd': 4127, 'Jack': 4098, 'Dcab': 7678}
>>> for name, phone in table.items():
...     print('{0:10} ==> {1:10d}'.format(name, phone))
...
Jack       ==>       4098
Dcab       ==>       7678
Sjoerd     ==>       4127

如果你有个实在是很长的格式化字符串，不想分割它。如果你可以用命名来引用被格式化的变量而不是位置就好了。有个简单的方法，可以传入一个字典，用中括号( [] )访问它的键:
>>> table = {'Sjoerd': 4127, 'Jack': 4098, 'Dcab': 8637678}
>>> print('Jack: {0[Jack]:d}; Sjoerd: {0[Sjoerd]:d}; '
          'Dcab: {0[Dcab]:d}'.format(table))
Jack: 4098; Sjoerd: 4127; Dcab: 8637678


+ Python三引号（triple quotes）
python中三引号可以将复杂的字符串进行复制:
python三引号允许一个字符串跨多行，字符串中可以包含换行符、制表符以及其他特殊字符。
三引号的语法是一对连续的单引号或者双引号（通常都是成对的用）。
 >>> hi = '''hi 
there'''
>>> hi   # repr()
'hi\nthere'
>>> print hi  # str()
hi 
there




5. List

















