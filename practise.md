# PythonNotes
//	取整除 - 返回商的整数部分（向下取整)

0. 取整
import math
#向上取整
print "math.ceil---"
print "math.ceil(2.3) => ", math.ceil(2.3)
print "math.ceil(2.6) => ", math.ceil(2.6)

#向下取整
print "\nmath.floor---"
print "math.floor(2.3) => ", math.floor(2.3)
print "math.floor(2.6) => ", math.floor(2.6)

#四舍五入
print "\nround---"
print "round(2.3) => ", round(2.3)
print "round(2.6) => ", round(2.6)

#这三个的返回结果都是浮点型
print "\n\nNOTE:every result is type of float"
print "math.ceil(2) => ", math.ceil(2)
print "math.floor(2) => ", math.floor(2)
print "round(2) => ", round(2)




1. 取奇偶
numbers = [1,2,3,4,5,6]
even = []
odd = []
while len(numbers)>0:
    number = numbers.pop()
    if(number%2==o):
        even.append(number)
    else:
        odd.append(number)
####http://www.runoob.com/python/python-while-loop.html
####loop循环7次，最后一次判断len()>0, Faulse




