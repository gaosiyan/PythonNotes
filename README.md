

- [Notebook](#notebook)
- [NumPy](#numpy)
    - [ndarray对象](#ndarray%E5%AF%B9%E8%B1%A1)

# Ipython
&emsp;&emsp;`函数名/模块名??`   显示相关的帮助信息,注意函数名在这里不能带括号`ESC`退出

# Notebook

# NumPy
&emsp;&emsp;Python中的列表对象(list)可以用来保存一组值,用作数组.但实际上列表中可以保存任何对象(不止是数值对象),列表的元素保存的是对象的指针,这样用来保存`[1,2,3]`,就需要3个指针和3个int对象.例如64位平台的64位Python解释器,`a = [1,2,3]`占用88字节,如下的代码:
```
a = [1,2,3]

sys.getsizeof(a)
Out[3]: 88
```
&emsp;&emsp;Python中还提供了array模块,用于直接保存数字,而不是对象指针.但是array不支持多维结构,只能提供一维结构,相当于C中的一维数组.也没有相应的运算函数.NumPy弥补了这些不足.NumPy提供了ndarray对象用于保存数组,和ufunc对象用于ndarray对象上的矢量运算.NumPy一般用下列语句导入:

&emsp;&emsp;`import numpy as np`

## ndarray对象
&emsp;&emsp;通过给`array()`传递Python的列表对象来创建数组,代码如下:
```
import numpy as np

a = np.array([1,2,3,4]) # 一维数组
b = np.array([5,6,7,8]) # 一维数组
c = np.array([[1,2,3,4],[4,5,6,7],[7,8,9,10]]) # 多维数组,注意这里两个中括号

a
Out[27]: array([1, 2, 3, 4])

b
Out[28]: array([5, 6, 7, 8])

c
Out[29]: 
array([[ 1,  2,  3,  4],
       [ 4,  5,  6,  7],
       [ 7,  8,  9, 10]])
```
&emsp;&emsp;数组的形状可以用`shape`属性得到,返回一个描述各轴长度的元组(tuple):
```
a.shape
Out[30]: (4,)

b.shape
Out[31]: (4,)

c.shape
Out[32]: (3, 4)
```
