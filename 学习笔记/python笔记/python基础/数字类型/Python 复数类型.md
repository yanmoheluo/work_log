### 前言

复数（Complex）是 Python 的内置类型，直接书写即可。换句话说，Python 语言本身就支持复数，而不依赖于标准库或者第三方库。

复数由实部（real）和虚部（imag）构成，在 Python 中，复数的虚部以j或者J作为后缀，具体格式为：

```python
a + bj
```

a 表示实部，b 表示虚部。

### 【实例】Python 复数的使用：

```python
    c1 = 12 + 0.2j
    print("c1Value: ", c1)
    print("c1Type", type(c1))
    c2 = 6 - 1.2j
    print("c2Value: ", c2)
    #对复数进行简单计算
    print("c1+c2: ", c1+c2)
    print("c1*c2: ", c1*c2)
```

### 运行结果：

```python
c1Value:  (12+0.2j)
c1Type <class 'complex'>
c2Value:  (6-1.2j)
c1+c2:  (18-1j)
c1*c2:  (72.24-13.2j)
```

可以发现，复数在 Python 内部的类型是 complex，Python 默认支持对复数的简单计算。