

- [Ipython](#ipython)
- [Notebook](#notebook)
- [NumPy](#numpy)
    - [ndarray对象](#ndarray%E5%AF%B9%E8%B1%A1)
        - [shape属性](#shape%E5%B1%9E%E6%80%A7)
        - [reshape方法](#reshape%E6%96%B9%E6%B3%95)
        - [数组元素类型](#%E6%95%B0%E7%BB%84%E5%85%83%E7%B4%A0%E7%B1%BB%E5%9E%8B)

# Ipython
&emsp;&emsp;`函数名/模块名?`   显示相关的帮助信息,注意函数名在这里不能带括号`ESC`退出

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
c = np.array([[1,2,3,4],[4,5,6,7],[7,8,9,10]]) # 多维数组,注意这里两个中括号,访问方式和C中一样,可以用c[0][0]访问和修改

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

### shape属性
&emsp;&emsp;数组的形状可以用`shape`属性得到,返回一个描述各轴长度的元组(tuple):
```
a.shape
Out[30]: (4,)

b.shape
Out[31]: (4,)

c.shape
Out[32]: (3, 4)
```
&emsp;&emsp;`shape`可以修改,这样将重新排列多维数组,但是具体数据在内存中的位置不变,只改变解释方式:
```
c.shape = 4,3

c
Out[34]: 
array([[ 1,  2,  3],
       [ 4,  4,  5],
       [ 6,  7,  7],
       [ 8,  9, 10]])
```
&emsp;&emsp;需要注意的是修改`shape`属性时元素的总个数不能改变,否则会报错,`c.shape = 2,-1`用这种方法-1的那个轴会自动计算长度.

### reshape方法
&emsp;&emsp;`shape`属性直接修改数组的解释方式.可以用`reshape`方法基于原始数组修改解释方式创建新数组`d = c.reshape(4,3)`,这样c数组的`shape`属性不变.但是c和d时共享内存的,修改`c[0][0]`后d中对应的元素也修改了.

### 数组元素类型
&emsp;&emsp;数组元素类型可以用dtype属性获取:
```
c.dtype
Out[40]: dtype('int32')
```
&emsp;&emsp;可以在创建数组时指定元素类型,例如:
`a = np.array([1,2,3,4],dtype = np.float)`

&emsp;&emsp;完整的元素类型列表可以用下面的方式得到:
```
set(np.typeDict.values())
Out[42]: 
{numpy.bool_,
 numpy.bytes_,
 numpy.complex128,
 numpy.complex128,
 numpy.complex64,
 numpy.datetime64,
 numpy.float16,
 numpy.float32,
 numpy.float64,
 numpy.float64,
 numpy.int16,
 numpy.int32,
 numpy.int32,
 numpy.int64,
 numpy.int8,
 numpy.object_,
 numpy.str_,
 numpy.timedelta64,
 numpy.uint16,
 numpy.uint32,
 numpy.uint32,
 numpy.uint64,
 numpy.uint8,
 numpy.void}
```
&emsp;&emsp;注意这里的元素类型有很多别名,例如`float,d,double`都是64bit的双精度浮点:
```
np.typeDict['float']
Out[43]: numpy.float64

np.typeDict['d']
Out[44]: numpy.float64

np.typeDict['double']
Out[45]: numpy.float64
```


