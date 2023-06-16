Python int()使用小结

int()的基本语法格式是int(x,[base=10])，其中base可以省略

int()的作用是把不同进制的数字或数字字符串转为十进制整数。使用中，其行为，参数有一些tricky,需要特别注意。

不带参数返回0,即int()

```python
>>> int()
0
```

取整是简单截断，不是四舍五入,如int(1.5) = 1

```python
>>> int(1.5)
1
```

参数可以是整数，浮点数，或算术表达式如100/3,但不能是复数，如1+2j

```python
>>> int(3)
3
>>> int(3.5)
3
>>> int(100/3)
33
>>> int(1+2j)
Traceback (most recent call last):
  File "<pyshell#0>", line 1, in <module>
    int(1+2j)
TypeError: can't convert complex to int
```

数字字符串可以是整数字符串如’123’，但不能是算术表达式字符串如’100/3’，或字符形式的浮点数如’1.5’

```python
>>> int('123')
123
>>> int(100/3)
33
>>> int('100/3')
Traceback (most recent call last):
  File "<pyshell#2>", line 1, in <module>
    int('100/3')
ValueError: invalid literal for int() with base 10: '100/3'
>>> int('1.5')
Traceback (most recent call last):
  File "<pyshell#6>", line 1, in <module>
    int('1.5')
ValueError: invalid literal for int() with base 10: '1.5'
```

base缺省值是10，表示十进制，如果包括base参数，则前面的x必须是符合当前进制的数字字符串  
此时int的作用是把base进制代表的数字字符串x，转换为10进制数

```python
>>> int('45',8)# 把8进制'45'转换为十进制数37
37

>>> int('ab',16) #
171

>>> int(45,8)
Traceback (most recent call last):
  File "<pyshell#8>", line 1, in <module>
    int(45,8)
TypeError: int() can't convert non-string with explicit base
>>> int(ab,16)
Traceback (most recent call last):
  File "<pyshell#9>", line 1, in <module>
    int(ab,16)
NameError: name 'ab' is not defined
```