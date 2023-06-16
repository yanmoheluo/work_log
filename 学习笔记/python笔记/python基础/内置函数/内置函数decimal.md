decimal 模块](https://www.jianshu.com/p/9f771f99adca)：decimal意思为十进制，这个模块提供了十进制浮点运算支持
1.可以传递给Decimal整型或者字符串参数，但不能是浮点数据，因为浮点数据本身就不准确。
2.要从浮点数据转换为Decimal类型
from decimal import *  
Decimal.from_float(12.222)  
# 结果为Decimal('12.2219999999999995310417943983338773250579833984375')  

3.通过设定有效数字，限定结果样式

from decimal import *  
getcontext().prec = 6  
Decimal(1)/Decimal(7)  
# 结果为Decimal('0.142857')，六个有效数字  

4.四舍五入，保留几位小数

from decimal import *  
Decimal('50.5679').quantize(Decimal('0.00'))  
# 结果为Decimal('50.57')，结果四舍五入保留了两位小数  

5.Decimal 结果转化为string

from decimal import *  
str(Decimal('3.40').quantize(Decimal('0.0')))  
# 结果为'3.4'，字符串类型
	import decimal
	a=decimal.Decimal('0.1')
	b=decimal.Decimal('0.2')
	print(a+b)
	0.3