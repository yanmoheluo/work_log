abs函数 

描述

返回数字的绝对值。

  
语法  
 abs(number)

 number 参数可以是任意有效的数值表达式。如果 number 包含 Null，则返回 Null；如果是未初始化变量，则返回 0。

  
  说明  
  1）数字的绝对值是其无符号的数值大小。例如，Abs(-1) 和 Abs(1) 都返回 1 。  
  而对于在matlab中相似的函数double，double（-1）则返回-1，也就是说abs（X）返回的是X的绝对值(absolute)，而double（X）返回的则是X的精确值（presision vlaue）  
  2）在C++中，相应的函数为 abs()  
  头文件可以是 cstdlib，或是 cmath  
  但是用cmath时，abs( int i )会出现二义性（在gcc的编译器上），所以还是用cstdlib做为头文件好  
  3）在matlab中有时会遇到函数abs（1，x）这样的函数，这个比一般abs多一个输入量， 他表示函数abs（x）的导数  
  因为abs（x）在0点的导数是不存在的，而对于x为复数 abs（x）是不解析的，所以他的取值只能是正数或者负数