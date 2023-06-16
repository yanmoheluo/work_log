# 描述

pow()函数是Python的内置函数，它计算并返回x的y次方的值。

# 语法和参数

```python
pow(x, y, z)
```

|   |   |   |
|---|---|---|
|名称|备注|说明|
|x|底数|不可省略的参数|
|y|指数|不可省略的参数|
|z|取余数字|可省略的参数。当z存在时，函数返回值等于 pow(x, y)%z|

# 举例说明

## 1. 参数z省略时

当省略取余数字z时，pow函数返回x的y次方的值。

```python
>>> pow(2, 3)8>>> pow(4, 0.5)2.0
```

## 2. 参数z存在时

当参数z存在，pow(x, y, z)的返回结果就等于pow(x, y)的结果对z求余。

```python
>>> pow(8, 2, 5)4
```

# 注意事项

## 1. z参数省略时，返回值是x的y次方

```python
>>> pow(2, 4)16
```

## 2. z参数省略时，x和y的值可以是整数和浮点数

当x或y存在浮点数时，pow()函数的返回结果也是浮点数，否则为整数。

```python
>>> pow(4, 0.5)2.0>>> type(pow(4, -0.5))<class 'float'>>>> pow(4, 2)16>>> type(pow(4, 2))<class 'int'>
```

## 3. 参数z不能为0

当参数z为0时，Python会抛出异常。

```python
>>> pow(4, 2, 0)Traceback (most recent call last):  File "<stdin>", line 1, in <module>ValueError: pow() 3rd argument cannot be 0
```

## 4. 参数z存在时，x和y只能是整数

当z存在时，x和y必须时整数。否则Python会抛出异常。

```python
>>> pow(3, 0.7, 1)Traceback (most recent call last):  File "<stdin>", line 1, in <module>TypeError: pow() 3rd argument not allowed unless all arguments are integers
```

# 自行实现

根据pow函数的功能特性，自行实现的代码如下（函数 my_pow()模拟实现了pow()函数）：

```python
def _pow(x, y):    if x == 0:        if y < 0:            raise ZeroDivisionError("0.0 cannot be raised to a negative power")            return        elif y == 0:            return 1        else:            return 0    else:        if y == 0:            return 1        if y < 0:            result = x            for i in range(1, abs(y)):                result *= x            return 1 / result         result = x        for i in range(1, y):            result *= x        return result def my_pow(x, y, z=None):    if z is None:        return _pow(x, y)    else:        if (type(x) != int) or (type(y) != int):            raise TypeError("pow() 3rd argument not"                  " allowed unless all arguments are integers")            return        else:            return _pow(x, y) % z
```
