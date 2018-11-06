# PythonNotes

# Lab5
The purpose of this week’s lab is to:
review two of python’s built-in sequence types - strings and lists;
iterate over sequences using the for loop; and
investigate some of the built-in methods for strings.

1. unicode encoding system
codes = [86,101,114,121,32,72,97,114,100,32,69,120,97,109]
string = ''
for charcode in codes:
    string = string + chr(charcode)
print(string)
-> Very Hard Exam

Generlised indexing (using an array of indices to index an array) works on NumPy arrays, but not on lists.
If x = [1,2,3,4,5] and y = [0, 2, 4] are lists, then x[y] = [1,3,5]  -> Faulse

If x = numpy.array([[1, 2, 3], [4, 5, 6]]), then type(x[i]) == list.
Not true. Indexing an n-dimensional array returns an (n-1)-dimensional array. (For example, if i == 0, x[i] == array([1,2,3]).)

s = "problem".
s[1:4] = 'rob'. The slice is from index 1 ('r') up to but not including index 4 ('l').

s[0:len(s):-1] = ''. 
When slicing with negative steps, the role of start and end is also reversed. 
Thus, to reverse the string, you need to slice it with s[-1 : (len(s)+1) : -1], 
that is, from the last character to before the first character. 
(The defaults for start and end can are also reversed, so s[::-1] also works.)



# Lab7

a_list = [[1, 2, 3], [4, 5, 6], [7, 8, 9]].
a_list[1:][1]


list.extend(seq) ->没有返回值，但会在已存在的列表中添加新的列表内容。


# Lab8
a.  A file is a sequence of bytes, but python's file object is not a sequence type.


b. This code
fileobj = open("my_file.txt")
for line in fileobj.readlines()[::-1]:
    print(line)
fileobj.close()
will print the lines in a file in reverse order. CorrectTrue. The readlines() method reads all lines in a text file and returns them in a list. That list can be reversed with a slice expression.


File objects in python are of two kinds: text and binary. Which kind of file object is created when a file is opened depends on the arguments given to open, not on the file itself. CorrectTrue. The type of file object depends only on the access mode string given to open. A text file can be opened as binary, and a binary file as a text file (though reading from it may fail, if the contents cannot be decoded into text).

When you open a file in write-only mode (with open("filename.txt", "w")) any existing data in the file, if it exists, is cleared.

c. Suppose that "haiku.txt" contains three lines of text.
fileobj = open("haiku.txt")
for line in fileobj:
    print(line)
next_line = fileobj.readline()  # line 4
The for loop will print each of the three lines in the file. But what happens when the call to readline on line 4, after the loop, is executed? Select the right alternative:
fileobj.readline() returns an empty string.


d. The path ../comp1730/lab8/ is an example of a relative path., 
It is possible to have two different files named Example.py and example.py in the same directory (that is, Example.py and example.py are different file names).

The part of a filename after the full stop (such as .txt or .py), often called the file's extension, is part of the file name; exercise.txt and exercise.py are simply two different names.


Let function f be defined as

def f(x):
    y = list(x)
    y.reverse()
    for i in range( len( y ) ):
        y[i] = chr(ord(y[i])+1)
    return ''.join( y )
If the function returns hojsuT!b!tj!tjiU, what argument was it called with?
(To find out, write a function that performs the inverse of the operations done by f. You may want to look up the documentation of the two methods list.reverse and str.join. To understand what the function f is doing, run it a few times providing different input strings. You may also want to print out the values of its local variables at various points.)The following function will find it:

def inv_of_f(z):
    # create an empty list:
    y=[]
    for i in z:
        # subtract 1 from char code and append to list:
        y.append(chr(ord( i ) - 1))
    # reverse order:
    y.reverse()
    # join characters in list together as a string:
    return ''.join( y )
