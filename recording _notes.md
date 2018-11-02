# PythonNotes
python全栈开发（入门到放弃）

####19.Intro_code

interaction
  cmd-->cd c:\ -->dir
  cd = change directory 
  dir = directory
  cd..返回上一层
  cd../..返回上上一层
  
  D:\>"D:...\...exe" c:\hello.txt
  环境变量
      default path：like Rstudio_lib
  
####20.Variable:
    STORE infor. to referneced and manipulated & provide labeling data,
    print()in one function could be multiple times.
    PRINCIPLE_OF_NAMING:
    1. descriptive
    2. number, name, _,capital letter
    3. Cannot_Started_With Number／Capital_letter
    4. 保留字符不能使用
    
    In python，all factors can be changed, like PIE, capital letter will be presented constant常量
    
 
 
####21.Assignment赋值
      name = “A”
      name2 = name
      print （name2，name）
      => A,A
      
      name = "B"
      print （name2，name)
      => B,A
      
####22.
    python 不用的statement自动清除
    
    
####23.Coding——ASSIIC 
    8 digit, Mandarin 1980->GB2312,Now->GB18030 over 27000charactor,
    unicode -> 万国码，二进制，2**16，一字符占2digit，
    UTF-8 ->压缩优化 unicode,可变长的字符编码集, for Morph lang.
    Window default = GB18030
    python3 = unicode
    python2 =
    ###to change coding system, saving as what labtop works.
        :#-*-coding:utf-8 -*-
        print(u"Mandarin Charactor")
        bc: unicode向下兼容，兼容gbk
        
    
####24.discription
    # 
    '''...''': docstring 
    
    ####print cannot culculate string+int, =>print ("..", str(int))
        input()accept all type saving as str.
        eg:
        d_age = 80
        age = input("your age")
        print ("...",d_age-int(age))
        pring ("..." + str(d_age-int(age)))
        
    
####26. if else















