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


2. 猜大小
import random
s = int(random.uniform(1,10))
#print(s)
m = int(input('输入整数:'))
while m != s:
    if m > s:
        print('大了')
        m = int(input('输入整数:'))
    if m < s:
        print('小了')
        m = int(input('输入整数:'))
    if m == s:
        print('OK')
        break;




3. 猜拳小游戏
import random
while 1:
    s = int(random.randint(1, 3))
    if s == 1:
        ind = "石头"
    elif s == 2:
        ind = "剪子"
    elif s == 3:
        ind = "布"
    m = raw_input('输入 石头、剪子、布,输入"end"结束游戏:')
    blist = ['石头', "剪子", "布"]
    if (m not in blist) and (m != 'end'):
        print "输入错误，请重新输入！"
    elif (m not in blist) and (m == 'end'):
        print "\n游戏退出中..."
        break
    elif m == ind :
        print "电脑出了： " + ind + "，平局！"
    elif (m == '石头' and ind =='剪子') or (m == '剪子' and ind =='布') or (m == '布' and ind =='石头'):
        print "电脑出了： " + ind +"，你赢了！"
    elif (m == '石头' and ind =='布') or (m == '剪子' and ind =='石头') or (m == '布' and ind =='剪子'):
        print "电脑出了： " + ind +"，你输了！"
##输入 石头、剪子、布,输入"end"结束游戏:石头
##电脑出了： 石头，平局！
##输入 石头、剪子、布,输入"end"结束游戏:石头    
##电脑出了： 剪子，你赢了！
##输入 石头、剪子、布,输入"end"结束游戏: 

4. 摇筛子
import random
import sys
import time

result = []
while True:
    result.append(int(random.uniform(1,7)))
    result.append(int(random.uniform(1,7)))
    result.append(int(random.uniform(1,7)))
    print result
    count = 0
    index = 2
    pointStr = ""
    while index >= 0:
        currPoint = result[index]
        count += currPoint
        index -= 1
        pointStr += " "
        pointStr += str(currPoint)
    if count <= 11:
        sys.stdout.write(pointStr + " -> " + "小" + "\n")
        time.sleep( 1 )   # 睡眠一秒
    else:
        sys.stdout.write(pointStr + " -> " + "大" + "\n")
        time.sleep( 1 )   # 睡眠一秒
    result = []
    
    
    
 5. 十进制转二进制
denum = input("输入十进制数:")
print denum,"(10)",
binnum = []
#二进制
while denum > 0:
    binnum.append(str(denum % 2)) # 栈压入
    denum //= 2
print '= ',
while len(binnum)>0:
    import sys
    sys.stdout.write(binnum.pop()) # 无空格输出print ' (2)'
    
    
    
6. while循环 - 九九乘法表
i = 1
while i :
    j = 1
    while j:
        print j ,"*", i ," = " , i * j , '  ',
        if i == j :
            break

        j += 1
        if j >= 10:
            break
    
    print "\n"
    i += 1
    if i >= 10:
        break



7. Pyhton 去除字符串首尾的空格
def trim(s):
    while s[:1] == ' ':
        s = s[1:]
    while s[-1:] == ' ':
        s = s[:-1]
    return s

str = '   Runoob     '
print(trim(str))




8. 取质数
list.append()
#输出2到100的质数
prime = []
for num in range(2,100):  # 迭代 2 到 100 之间的数字
   for i in range(2,num): # 根据因子迭代
      if num%i == 0:      # 确定第一个因子
         break            # 跳出当前循环
   else:                  # 循环的 else 部分
      prime.append(num)
print prime


9. 打印1-9三角形阵列
for i in range(1,11):
    for k in range(1,i):
        print k,
    print "\n"
->
1 
1 2 
1 2 3 
1 2 3 4 
1 2 3 4 5 
1 2 3 4 5 6 
1 2 3 4 5 6 7 
1 2 3 4 5 6 7 8 
1 2 3 4 5 6 7 8 9 


10.按大小重新排序 ==冒泡排序
arays = [1,8,2,6,3,9,4]
for i in range(len(arays)):
    for j in range(i+1):
        if arays[i] < arays[j]:
            # 实现连个变量的互换
            arays[i],arays[j] = arays[j],arays[i]
print arays
-> [1, 2, 3, 4, 6, 8, 9]


11.




















