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
Python有6个序列的内置类型，但最常见的是列表和元组
序列都可以进行的操作包括索引，切片，加，乘，检查成员。
此外，Python已经内置确定序列的长度以及确定最大和最小的元素的方法。
列表是最常用的Python数据类型，它可以作为一个方括号内的逗号分隔值出现。
列表的数据项不需要具有相同的类型

+ 更新列表
list = []          ## 空列表
list.append('Google')   ## 使用 append() 添加元素
list.append('Runoob')
print list
['Google', 'Runoob']


+ 删除列表元素
list1 = ['physics', 'chemistry', 1997, 2000]
print list1
del list1[2]
print "After deleting value at index 2 : "
print list1
->
['physics', 'chemistry', 1997, 2000]
After deleting value at index 2 :
['physics', 'chemistry', 2000]

+ Python列表脚本操作符
列表对 + 和 * 的操作符与字符串相似。+ 号用于组合列表，* 号用于重复列表。


+ Python列表截取
>>>L = ['Google', 'Runoob', 'Taobao']
>>> L[2]
'Taobao'
>>> L[-2]
'Runoob'
>>> L[1:]
['Runoob', 'Taobao']
>>>

+ Python列表函数&方法
- List len()方法
list1, list2 = [123, 'xyz', 'zara'], [456, 'abc']
print "First list length : ", len(list1);
print "Second list length : ", len(list2);
First list length :  3
Second lsit length :  2

- List max()方法
list1, list2 = [123, 'xyz', 'zara', 'abc'], [456, 700, 200]
print "Max value element : ", max(list1);
print "Max value element : ", max(list2);
Max value element :  zara
Max value element :  700

- List min()方法

- List list()方法
元组与列表是非常类似的，区别在于元组的元素值不能修改，元组是放在括号中，列表是放于方括号中。
list( tup )
aTuple = (123, 'xyz', 'zara', 'abc');
aList = list(aTuple)
print "列表元素 : ", aList
列表元素 :  [123, 'xyz', 'zara', 'abc']

- List append()方法
list.append(obj)
obj -- 添加到列表末尾的对象。
aList = [123, 'xyz', 'zara', 'abc'];
aList.append( 2009 );
print "Updated List : ", aList;

- List count()方法
返回元素在列表中出现的次数。
aList = [123, 'xyz', 'zara', 'abc', 123];
print ("Count for 123 : ", aList.count(123));
print ("Count for zara : ", aList.count('zara'));
->
Count for 123 :  2
Count for zara :  1

- List extend()方法
list.extend(seq)
aList = [123, 'xyz', 'zara', 'abc', 123];
bList = [2009, 'manni'];
aList.extend(bList)
print "Extended List : ", aList ;
Extended List :  [123, 'xyz', 'zara', 'abc', 123, 2009, 'manni']


- List index()方法
aList = [123, 'xyz', 'zara', 'abc'];
print "Index for xyz : ", aList.index( 'xyz' ) ;
print "Index for zara : ", aList.index( 'zara' ) ;
Index for xyz :  1
Index for zara :  2


- List insert()方法
list.insert(index, obj)
aList = [123, 'xyz', 'zara', 'abc']
aList.insert( 3, 2009)
print "Final List : ", aList
->
Final List : [123, 'xyz', 'zara', 2009, 'abc']


- List pop()方法
pop() 函数用于移除列表中的一个元素（默认最后一个元素），并且返回该元素的值。
list.pop([index=-1])
obj -- 可选参数，要移除列表元素的索引值，不能超过列表总长度，默认为 index=-1，删除最后一个列表值。
list1 = ['Google', 'Runoob', 'Taobao']
list_pop=list1.pop(1)
print "删除的项为 :", list_pop
print "列表现在为 : ", list1
删除的项为 : Runoob
列表现在为 :  ['Google', 'Taobao']


- List remove()方法
remove() 函数用于移除列表中某个值的第一个匹配项。
list.remove(obj)
aList = [123, 'xyz', 'zara', 'abc', 'xyz'];
aList.remove('xyz');
print "List : ", aList;
aList.remove('abc');
print "List : ", aList;
->
List :  [123, 'zara', 'abc', 'xyz']
List :  [123, 'zara', 'xyz']

- List reverse()方法
reverse() 函数用于反向列表中元素。
list.reverse()
aList = [123, 'xyz', 'zara', 'abc', 'xyz']
aList.reverse()
print ("List : ", aList)
-> 
List :  ['xyz', 'abc', 'zara', 'xyz', 123]


- List sort()方法
sort() 函数用于对原列表进行排序，如果指定参数，则使用比较函数指定的比较函数。
list.sort(cmp=None, key=None, reverse=False)
cmp -- 可选参数, 如果指定了该参数会使用该参数的方法进行排序。
key -- 主要是用来进行比较的元素，只有一个参数，具体的函数的参数就是取自于可迭代对象中，指定可迭代对象中的一个元素来进行排序。
reverse -- 排序规则，reverse = True 降序， reverse = False 升序（默认）。
EG:
aList = [123, 'Google', 'Runoob', 'Taobao', 'Facebook'];
aList.sort();
print "List : ", aList
->List :  [123, 'Facebook', 'Google', 'Runoob', 'Taobao']

vowels = ['e', 'a', 'u', 'o', 'i']
vowels.sort(reverse=True)
print '降序输出:', vowels
降序输出: ['u', 'o', 'i', 'e', 'a']

指定列表中的元素排序来输出列表：
def takeSecond(elem):
    return elem[1]
random = [(2, 2), (3, 4), (4, 1), (1, 3)]
random.sort(key=takeSecond) #指定第二个元素排序
print '排序列表：', random
排序列表：[(4, 1), (2, 2), (1, 3), (3, 4)]

- 
>>> list4=[123,["das","aaa"],234]
>>> list4
>>> "aaa" in list4                  #in只能判断一个层次的元素
False
>>> "aaa" in list4[1]           #选中列表中的列表进行判断
True
>>> list4[1][1]
'aaa'

- [:-1] 表示从第一个元素遍历到倒数第二个元素

list1 = [1,2,3,4,5,]
print list1
#列表截取
print list1[:-1]
->
[1, 2, 3, 4, 5]
[1, 2, 3, 4]


- id(), a 与 a[:]
列表里 a 与 a[:] 不同。
我们可以通过函数 id() 来查看：
a = [1, 2, 3]
id(a)
id(a[:])

会发现得到的两个值不同。
或者直接运行：
a is a[:]
返回值将是：False。
简单来说，a[:] 是创建 a 的一个副本，这样我们在代码中对 a[:] 进行操作后，就不会改变 a 的值了。而若直接对 a 进行操作，那么 a 的值会收到一些操作的影响，如 append() 等。

- 针对列表无法正常输出汉字的解决方法：
import json
list_words = [ '你', '我', '他' ]
print( list_words )                                        # 无法正常显示汉字 ['\xe4\xbd\xa0', '\xe6\x88\x91', '\xe4\xbb\x96']
print( str(list_words).decode( 'string_escape' ) )         # 正常显示汉字   ['你', '我', '他']

list_words_result = json.dumps( list_words, encoding='UTF-8', ensure_ascii=False )
print( list_words_result )


- remove 和 del 之间的区别
>>> a=[1,2,3,5,4,2,6]
>>> a.remove(a[5])
>>> a
[1, 3, 5, 4, 2, 6]
->  remove 移除的是列表中元素的位置
>>> a=[1,2,3,5,4,2,6]
>>> del(a[5])
>>> a
[1, 2, 3, 5, 4, 6]
-> 说明 del 删除是按索引来的，索引起始位置为 0。

- 清空列表中的多项空值：
test = ['a','','b','','c','','']
test = [i for i in test if i != '']
print(test)
-> ['a', 'b', 'c']

- Python 列表切片应用
s = 'abcdefg'
#返回从起始位置到索引位置 2 处的字符串切片
print(s[:3]) # 输出 'abc'

#返回从第三个索引位置到结尾的字符串切片
print(s[3:]) # 输出 'defg'

#字符串逆序输出
print(s[::-1]) # 输出 'gfedcba'

#输出从开始位置间隔一个字符组成的字符串
print(s[::2]) # 输出 'aceg'
print(range(10)[::2])  # 输出偶数：[0, 2, 4, 6, 8]

#它们也可以相互结合使用。
#从索引位置 6 到索引位置 2，逆向间隔一个字符
print(s[6:2:-2]) # 输出'ge'
s[6:2:1] #''

- 记忆小方法：str.join(元组、列表、字典、字符串) 之后生成的只能是字符串。

所以很多地方很多时候生成了元组、列表、字典后，可以用 join() 来转化为字符串
list=['1','2','3','4','5']
print(''.join(list))
-> 12345
seq = {'hello':'nihao','good':2,'boy':3,'doiido':4}
print('-'.join(seq))        #字典只对键进行连接
-> hello-good-boy-doiido


5. 元组 Tuple
元组与列表类似，不同之处在于元组的元素不能修改。
元组使用小括号，列表使用方括号。
元组与字符串类似，下标索引从0开始，可以进行截取，组合等。
元组创建很简单，只需要在括号中添加元素，并使用逗号隔开即可。
tup1 = ('physics', 'chemistry', 1997, 2000)
tup2 = (1, 2, 3, 4, 5 )
tup3 = "a", "b", "c", "d"
tup1 = (50,)

tup1 = (12, 34.56)
tup2 = ('abc', 'xyz')
#以下修改元组元素操作是非法的。
#tup1[0] = 100
 
#创建一个新的元组
tup3 = tup1 + tup2
print tup3
-> (12, 34.56, 'abc', 'xyz')
#删除元组
元组中的元素值是不允许删除的，但我们可以使用del语句来删除整个元组
tup = ('physics', 'chemistry', 1997, 2000)
print tup
del tup
print "After deleting tup : "
print tup

#元组索引，截取
因为元组也是一个序列，所以我们可以访问元组中的指定位置的元素，也可以截取索引中的一段元素
L = ('spam', 'Spam', 'SPAM!')
L[1:]	
('Spam', 'SPAM!')	截取元素


#无关闭分隔符
任意无符号的对象，以逗号隔开，默认为元组
print 'abc', -4.24e93, 18+6.6j, 'xyz'
x, y = 1, 2
print "Value of x , y : ", x,y
->
abc -4.24e+93 (18+6.6j) xyz
Value of x , y : 1 2

#内置函数
- len(tuple)
计算元组元素个数。

- tuple( seq )
>>>tuple([1,2,3,4])
-> (1, 2, 3, 4)
>>> tuple({1:2,3:4})    #针对字典 会返回字典的key组成的tuple
(1, 3)
>>> tuple((1,2,3,4))    #元组会返回元组自身
(1, 2, 3, 4)

- 
aList = [123, 'xyz', 'zara', 'abc'];
aTuple = tuple(aList) 
print ("Tuple elements : ", aTuple)
-> Tuple elements :  (123, 'xyz', 'zara', 'abc')

- 
>>> tup1 = ("all")
>>> print tup1    #type(tup1) = str
-> all 
输出字符串 all，这是因为括号()既可以表示tuple，又可以表示数学公式中的小括号。
所以，如果元组只有1个元素，就必须加一个逗号，防止被当作括号运算：
>>> tup1 = ("all",)
>>> print tup1
-> ('all',)


####元组与列表的区别，元组它的关键是不可变性。
如果在程序中以列表的形式传递一个对象的集合，它可能在任何地方改变；
如果使用元组的话，则不能。
元组提供了一种完整的约束。

- 切片的方式更新元组
>>> temp=(1, 2, 4, 5)
>>> temp=temp[:2]+(3,)+temp[2:]
>>> temp
-> (1, 2, 3, 4, 5)


- 元组的一级元素不可被修改增加删除但可以修改二级后的。
如修改元祖中列表，字典等内容
>>> tu = ("alex", [11, 22, {"k1": 'v1', "k2": ["age", "name"], "k3": (11,22,33)}, 44])
>>> tu[1][2]["k2"].append("seven")
>>> print(tu[1][2]["k2"])
-> ['age', 'name', 'seven']


- 切片虽然可以重新组成新的元组，但是要注意截取一个元素时候不能和新的元组相 + 
>>> a=(1,2,3,4,5,6)
>>> c=a[1:4]+a[5]    # 报错, a[5] 被当成了整型
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: can only concatenate tuple (not "int") to tuple

>>> c=a[1:4]+a[2:4]   # 这样可以
>>> c
(2, 3, 4, 3, 4)


- 截取的是一个元素
>>> T = ('aa','bb','cc','dd','ee')
>>> T = T[0:3]+T[4:]
>>> print(T)
('aa', 'bb', 'cc', 'ee')
T[4] 得到的是字符串 'ee', 而 T[4:] 得到的是新元组 ('ee',)，所以元组拼接时用 T[4] 会报错。
ps：T[4:4] 获取的值为空。





6.字典(Dictionary)
字典是另一种可变容器模型，且可存储任意类型对象。
字典的每个键值 key=>value 对用冒号 : 分割，每个键值对之间用逗号 , 分割，整个字典包括在花括号 {} 中 ,格式如下所示：
d = {key1 : value1, key2 : value2 }   #键一般是唯一的，如果重复最后的一个键值对会替换前面的，值不需要唯一。

>>>dict = {'a': 1, 'b': 2, 'b': '3'};
>>> dict['b']
'3'
>>> dict
{'a': 1, 'b': '3'}

#值可以取任何数据类型，但键必须是不可变的，如字符串，数字或元组。
dict2 = { 'abc': 123, 98.6: 37 };
把相应的键放入熟悉的方括弧，如下实例:
dict = {'Name': 'Zara', 'Age': 7, 'Class': 'First'};
print "dict['Name']: ", dict['Name'];
print "dict['Age']: ", dict['Age'];
-> 
dict['Name']:  Zara
dict['Age']:  7

如果用字典里没有的键访问数据 :
dict['Alice']: 
Traceback (most recent call last):
  File "test.py", line 5, in <module>
    print "dict['Alice']: ", dict['Alice'];
KeyError: 'Alice'

#修改字典
向字典添加新内容的方法是增加新的键/值对，修改或删除已有键/值对如下实例
dict = {'Name': 'Zara', 'Age': 7, 'Class': 'First'};
dict['Age'] = 8; # update existing entry
dict['School'] = "DPS School"; # Add new entry
print "dict['Age']: ", dict['Age'];
print "dict['School']: ", dict['School'];
-> dict['Age']:  8
-> dict['School']:  DPS School

#删除字典元素
能删单一的元素也能清空字典，清空只需一项操作。
显示删除一个字典用del命令，如下实例：
dict = {'Name': 'Zara', 'Age': 7, 'Class': 'First'}; 
del dict['Name']; # 删除键是'Name'的条目
dict.clear();     # 清空词典所有条目
del dict ;        # 删除词典
print "dict['Age']: ", dict['Age'];
print "dict['School']: ", dict['School'];

但这会引发一个异常，因为用del后字典不再存在


#字典键的特性
1）不允许同一个键出现两次。创建时如果同一个键被赋值两次，后一个值会被记住
dict = {'Name': 'Zara', 'Age': 7, 'Name': 'Manni'};
print "dict['Name']: ", dict['Name'];
-> dict['Name']:  Manni

2）键必须不可变，所以可以用数字，字符串或元组充当，所以用列表就不行

dict = {['Name']: 'Zara', 'Age': 7};
print "dict['Name']: ", dict['Name'];


#字典内置函数&方法
- len(dict)
- type(dict)
- dict.clear() # NA
- dict.copy() 返回一个字典的浅复制 # NA； 直接赋值和 copy 的区别：  浅拷贝dict2 = dict1: 引用对象； dict3 = dict1.copy()# 深拷贝父对象（一级目录），子对象（二级目录）不拷贝，还是引用
- dict.fromkeys(seq[, value]) #创建一个新字典，以序列 seq 中元素做字典的键，val 为字典所有键对应的初始值
Eg :
seq = ('Google', 'Runoob', 'Taobao')
dict = dict.fromkeys(seq)
print "新字典为 : %s" %  str(dict) -> 新字典为 : {'Google': None, 'Taobao': None, 'Runoob': None}
 
dict = dict.fromkeys(seq, 10)
print "新字典为 : %s" %  str(dict) -> 新字典为 : {'Google': 10, 'Taobao': 10, 'Runoob': 10}

- dict.get(key, default=None) #返回指定键的值，如果值不在字典中返回默认值。
dict = {'Name': 'Zara', 'Age': 27}
print "Value : %s" %  dict.get('Age') ->Value : 27
print "Value : %s" %  dict.get('Sex', "Never") -> Value : Never

- 	dict.has_key(key) #判断键是否存在于字典中，如果键在字典dict里返回true，否则返回false。
-  dict.items() #以列表返回可遍历的(键, 值) 元组数组。
dict = {'Google': 'www.google.com', 'Runoob': 'www.runoob.com', 'taobao': 'www.taobao.com'}
print "字典值 : %s" %  dict.items()
#遍历字典列表
for key,values in  dict.items():
    print key,values
-> 字典值 : [('Google', 'www.google.com'), ('taobao', 'www.taobao.com'), ('Runoob', 'www.runoob.com')]
Google www.google.com
taobao www.taobao.com
Runoob www.runoob.com

-  dict.keys() #以列表返回一个字典所有的键
dict = {'Name': 'Zara', 'Age': 7}
print "Value : %s" %  dict.keys() ->Value : ['Age', 'Name']



- dict.setdefault(key, default=None) #如果键不存在于字典中，将会添加键并将值设为默认值。
dict = {'runoob': '菜鸟教程', 'google': 'Google 搜索'}
print "Value : %s" %  dict.setdefault('runoob', None) -> Value : 菜鸟教程
print "Value : %s" %  dict.setdefault('Taobao', '淘宝') ->Value : 淘宝


-dict.update(dict2) #函数把字典dict2的键/值对更新到dict里。
dict = {'Name': 'Zara', 'Age': 7}
dict2 = {'Sex': 'female' }
dict.update(dict2) 
print "Value : %s" %   dict -> Value : {'Age': 7, 'Name': 'Zara', 'Sex': 'female'}

- dict.values() # 函数以列表返回字典中的所有值。
dict = {'Name': 'Zara', 'Age': 7}
print "Value : %s" %  dict.values() -> Value : [7, 'Zara']


- pop(key[,default]) #删除字典给定键 key 及对应的值，返回值为被删除的值。key 值必须给出。 否则，返回 default 值。
site= {'name': '菜鸟教程', 'alexa': 10000, 'url': 'www.runoob.com'}
pop_obj=site.pop('name')
print pop_obj    # 输出 ：菜鸟教程

- popitem() #随机返回并删除字典中的一对键和值。如果字典已经为空，却调用了此方法，就报出KeyError异常。
site= {'name': '菜鸟教程', 'alexa': 10000, 'url': 'www.runoob.com'}
pop_obj=site.popitem()
print(pop_obj) -> ('url', 'www.runoob.com')
print(site) -> {'alexa': 10000, 'name': '\xe8\x8f\x9c\xe9\xb8\x9f\xe6\x95\x99\xe7\xa8\x8b'}

-字典的键可以使用布尔类型的，True 默认代表 1，False 默认代表 0，如果包含 0 或 1 就无法使用布尔类型
>>> test = {0:"1", 1:"2", True:"3", False:"4"}
>>> print(test)
-> {0: '4', 1: '3'}
没有 0 或 1 的情况下：
>>> test = {"a":"1", "b" :"2", True:"3", False:"4"}
>>> print(test)
-> {'a': '1', True: '3', 'b': '2', False: '4'}

- dict.has_key() 被移除了。改成用 in 或者 not in：
>>> dict = {'Name': 'Zara', 'Age': 7}
>>> print ('Height' in dict)
False
>>> print ('Height' not in dict)
True

- 如果直接用 [] 访问，在没有找到对应键的情况下会报错，一个更输出'default'好的替代方案是用内置的 get 方法来取键值，这时候如果不存在也不会报错。>>>test = {'key1':'value1','key2':'value2'}
>>>test['key3'] 报错：KeyError:'key3'
>>>test.get('key3') 无输出
>>>test.get('key3','default') 








7.函数
- return语句[表达式]退出函数，选择性地向调用方返回一个表达式。不带参数值的return语句返回None。
- 全局变量和局部变量
total = 0; # 这是一个全局变量
#可写函数说明
def sum( arg1, arg2 ):
   #返回2个参数的和."
   total = arg1 + arg2; # total在这里是局部变量.
   print "函数内是局部变量 : ", total
   return total;
 
#调用sum函数
sum( 10, 20 );
print "函数外是全局变量 : ", total

lobals() 和 locals() 函数可被用来返回全局和局部命名空间里的名字。

全局变量想作用于函数内，需加 global: 1、global---将变量定义为全局变量。可以通过定义为全局变量，实现在函数内部改变变量值。 2、一个global语句可以同时定义多个变量，如 global x, y, z。
globvar = 0
def set_globvar_to_one():
    global globvar    # 使用 global 声明全局变量
    globvar = 1
def print_globvar():
    print(globvar)     # 没有使用 global
set_globvar_to_one()
print  globvar        # 输出 1
print_globvar()       # 输出 1，函数内的 globvar 已经是全局变量





8. 模块
一个模块只会被导入一次，不管你执行了多少次import。这样可以防止导入模块被一遍又一遍地执行。
from 语句让你从模块中导入一个指定的部分到当前命名空间中。语法如下：

from fib import fibonacci #它只会将 fib 里的 fibonacci 单个引入到执行这个声明的模块的全局符号表。




9. 文件I/O

- print "Python 是一个非常棒的语言，不是吗？"
你可以给它传递零个或多个用逗号隔开的表达式

- 内置函数从标准输入读入一行文本
#raw_input函数 ： raw_input([prompt]) 函数从标准输入读取一个行，并返回一个字符串（去掉结尾的换行符）
str = raw_input("请输入：")
print "你输入的内容是: ", str
-> 请输入：Hello Python！
你输入的内容是:  Hello Python！

#input([prompt]) 函数和 raw_input([prompt]) 函数基本类似，但是 input 可以接收一个Python表达式作为输入，并将运算结果返回。
str = input("请输入：")
print "你输入的内容是: ", str
-> 请输入：[x*5 for x in range(2,10,2)]
你输入的内容是:  [10, 20, 30, 40]


- 打开和关闭文件
#open 函数
file object = open(file_name [, access_mode][, buffering])
-> file_name：file_name变量是一个包含了你要访问的文件名称的字符串值。
-> access_mode：access_mode决定了打开文件的模式：只读，写入，追加等。所有可取值见如下的完全列表。这个参数是非强制的，默认文件访问模式为只读(r)。
-> buffering:如果buffering的值被设为0，就不会有寄存。如果buffering的值取1，访问文件时会寄存行。如果将buffering的值设为大于1的整数，表明了这就是的寄存区的缓冲大小。如果取负值，寄存区的缓冲大小则为系统默认。

#File对象的属性

file.closed	返回true如果文件已被关闭，否则返回false。
file.mode	返回被打开文件的访问模式。
file.name	返回文件的名称。
file.softspace	如果用print输出后，必须跟一个空格符，则返回false。否则返回true


#close()方法
File 对象的 close（）方法刷新缓冲区里任何还没写入的信息，并关闭该文件，这之后便不能再进行写入。
当一个文件对象的引用被重新指定给另一个文件时，Python 会关闭之前的文件。用 close（）方法关闭文件是一个很好的习惯。
fileObject.close()


#write()方法
write()方法可将任何字符串写入一个打开的文件。需要重点注意的是，Python字符串可以是二进制数据，而不是仅仅是文字。
write()方法不会在字符串的结尾添加换行符('\n')：
fileObject.write(string)

在这里，被传递的参数是要写入到已打开文件的内容。
#打开一个文件
fo = open("foo.txt", "w")
fo.write( "www.runoob.com!\nVery good site!\n")
#关闭打开的文件
fo.close()

上述方法会创建foo.txt文件，并将收到的内容写入该文件，并最终关闭文件。如果你打开这个文件，将看到以下内容
$ cat foo.txt 
www.runoob.com!
Very good site!



#read()方法
从一个打开的文件中读取一个字符串。需要重点注意的是，Python字符串可以是二进制数据，而不是仅仅是文字。
fileObject.read([count])
被传递的参数是要从已打开文件中读取的字节计数。该方法从文件的开头开始读入，如果没有传入count，它会尝试尽可能多地读取更多的内容，很可能是直到文件的末尾。

#打开一个文件
fo = open("foo.txt", "r+")
str = fo.read(10)
print "读取的字符串是 : ", str
#关闭打开的文件
fo.close()
->读取的字符串是 :  www.runoob


#文件定位
tell()方法告诉你文件内的当前位置, 换句话说，下一次的读写会发生在文件开头这么多字节之后。



- Python里的目录
#mkdir()方法
当前目录下创建新的目录们。你需要提供一个包含了要创建的目录名称的参数。
os.mkdir("newdir")

#chdir()方法
改变当前的目录。chdir()方法需要的一个参数是你想设成当前目录的目录名称。
import os
#将当前目录改为"/home/newdir"
os.chdir("/home/newdir")

#getcwd()方法：
print os.getcwd()

#rmdir()方法
rmdir()方法删除目录，目录名称以参数传递。
在删除这个目录之前，它的所有内容应该先被清除。
import os
#删除”/tmp/test”目录
os.rmdir( "/tmp/test"  )

10. File 方法
在 write 内容后，直接 read 文件输出会为空，是因为指针已经在内容末尾。
两种解决方式: 其一，先 close 文件，open 后再读取，其二，可以设置指针回到文件最初后再 read
import os;

document = open("testfile.txt", "w+");
print （"文件名: ", document.name）
document.write("这是我创建的第一个测试文件！\nwelcome!");
print document.tell();
#输出当前指针位置
document.seek(os.SEEK_SET);
#设置指针回到文件最初
context = document.read();
print context;
document.close();


#Python 在 Windows 环境下(在 linux 环境下不存在此问题),在 write 后，直接 read， 会出现乱码问题
fo = open("foo.txt", "w+")
fo.write('www.runoob.com')
print fo.read()
-> 而是 EOF 的问题，也就是指针的位置问题，当我们以 w+ 开启文件读写模式的时候，由于是 w，所以文件会被清空，也就是文件为空，初始状态指针为 0 ，也就是初始即为 EOF 位置。
-> 
fo = open("foo.txt", "w+")
fo.write('www.runoob.com')
fo.flush()
fo.seek(0)#指定指针为止为文件开头
print fo.read()








11. 异常处理
