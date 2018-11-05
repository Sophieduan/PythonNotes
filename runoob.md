# PythonNotes

#Operator

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

# -*- coding: utf-8 -*-

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


#Loop
while 循环	在给定的判断条件为 true 时执行循环体，否则退出循环体。
for 循环	重复执行语句
嵌套循环	你可以在while循环体中嵌套for循环

break 语句	在语句块执行过程中终止循环，并且跳出整个循环
continue 语句	在语句块执行过程中终止当前循环，跳出该次循环，执行下一次循环。
pass 语句	pass是空语句，是为了保持程序结构的完整性。


##While
http://www.runoob.com/python/python-while-loop.html
+ continue
+ break
+ 无限循环
+ while...else...
-> 同行：
flag = 1
 
while (flag): print 'Given flag is really true!'
 
print "Good bye!"


##for
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



#循环嵌套







