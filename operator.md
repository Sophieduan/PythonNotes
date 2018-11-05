# PythonNotes

####Operator
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
