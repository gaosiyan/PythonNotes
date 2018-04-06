

- [Ipython](#ipython)
- [Notebook](#notebook)
- [NumPy](#numpy)
    - [ndarray对象](#ndarray%E5%AF%B9%E8%B1%A1)
        - [shape属性](#shape%E5%B1%9E%E6%80%A7)
        - [reshape方法](#reshape%E6%96%B9%E6%B3%95)
        - [数组元素类型](#%E6%95%B0%E7%BB%84%E5%85%83%E7%B4%A0%E7%B1%BB%E5%9E%8B)
        - [直接创建数组](#%E7%9B%B4%E6%8E%A5%E5%88%9B%E5%BB%BA%E6%95%B0%E7%BB%84)
        - [存取元素](#%E5%AD%98%E5%8F%96%E5%85%83%E7%B4%A0)
    - [ufunc函数](#ufunc%E5%87%BD%E6%95%B0)
- [matplotlib](#matplotlib)
    - [pylot模块](#pylot%E6%A8%A1%E5%9D%97)

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
&emsp;&emsp;Python中还提供了array模块,用于直接保存数字,而不是对象指针.但是array不支持多维结构,只能提供一维结构,相当于C中的一维数组.也没有相应的运算函数.NumPy弥补了这些不足.NumPy提供了ndarray对象用于保存数组,和ufunc函数用于ndarray对象上的矢量运算.NumPy一般用下列语句导入:

&emsp;&emsp;`import numpy as np`

## ndarray对象
&emsp;&emsp;通过给`array()`传递Python的列表对象来创建数组,代码如下:
```
# -*- coding:utf-8 -*-
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

### 直接创建数组
&emsp;&emsp;`arange`方法类似于`range`函数,通过指定开始值,结束值和步长来创建等差数列的一维数组.第一个参数是起始值,第二个参数是结束值,第三个参数是步长,如下(注意不包括终点1):
```
np.arange(0,1,0.1)
Out[46]: array([0. , 0.1, 0.2, 0.3, 0.4, 0.5, 0.6, 0.7, 0.8, 0.9])
```

&emsp;&emsp;`linspace`方法通过指定开始值和结束值以及元素个数来创建一维数组,第一个参数是起始值,第二个参数是结束值,第三个参数是元素个数,并且可以用endpoint关键字参数来控制是否包含终点,默认包含终点,即`endpoint = True`,示例代码如下:
```
np.linspace(0,1,10) #步长为1/9
Out[48]: 
array([0.        , 0.11111111, 0.22222222, 0.33333333, 0.44444444,
       0.55555556, 0.66666667, 0.77777778, 0.88888889, 1.        ])

np.linspace(0,1,10,endpoint = False) #步长为1/10
Out[49]: array([0. , 0.1, 0.2, 0.3, 0.4, 0.5, 0.6, 0.7, 0.8, 0.9])
```
&emsp;&emsp;与`linspace`方法类似的有`logspace`方法用于创建等比数列的一维数组:
```
np.logspace(0,2,5)
Out[50]: 
array([  1.        ,   3.16227766,  10.        ,  31.6227766 , 100.])
```
&emsp;&emsp;从`10^0`到`10^2`创建5个等比数值.关键字参数`base`参数指定底数,默认为10,关键字`endpoint`参数同`linspace`方法.

&emsp;&emsp;`zeros,ones,empty`方法可以创建指定形状和类型的数组,`empty`方法只分配内存:
```
np.empty((2,3),dtype = np.float)
Out[51]: 
array([[0., 0., 0.],
       [0., 0., 0.]])
```
&emsp;&emsp;`zeros`方法创建元素全为0的数组,`ones`方法创建元素全为1的数组.另外还有`zeros_like,ones_like,empty_like`等方法基于现存数组对象创建对应的新数组对象.`zeros_like(a)`等价于`zeros_like(a.shape,dtype = a.dtype)`

### 存取元素
&emsp;&emsp;对于一维数组a,可以用`a[数组索引]`来存取,和C语言类似,索引从0开始,这里还可以用类似切片的方式`a[3:5]`读取`a[3]`,`a[4]`但是没有`a[5]`.需要注意的是标准列表获取的是一个新数组,这里的切片并不是新数组,它和原始数组共享内存.

## ufunc函数
&emsp;&emsp;ufunc函数可以理解为一个特殊函数,不过这个函数输入的是`ndarray`对象,它对数组中每一个元素执行相同的运算,不用在函数内部执行循环遍历数组,矢量运算.例如下面的`np.sin`函数就是自带的ufunc函数(可以自定义ufunc函数):
```
x = np.linspace(0,2*np.pi,10)
y = np.sin(x)

y
Out[55]: 
array([ 0.00000000e+00,  6.42787610e-01,  9.84807753e-01,  8.66025404e-01,
        3.42020143e-01, -3.42020143e-01, -8.66025404e-01, -9.84807753e-01,
       -6.42787610e-01, -2.44929360e-16])
```
&emsp;&emsp;可以将结果直接输出到x,如下面的代码:
```
x = np.linspace(0,2*np.pi,10)
y = np.sin(x,out = x)

x
Out[61]: 
array([ 0.00000000e+00,  5.64171154e-01,  7.40064184e-01,  6.90196075e-01,
        3.29138324e-01, -3.29138324e-01, -6.90196075e-01, -7.40064184e-01,
       -5.64171154e-01, -2.44929360e-16])

id(x) == id(y)
Out[62]: True
```
&emsp;&emsp;用`np.sin`计算要比用`for`循环调用`math.sin`计算快一个数量级.常用的内置`ufunc`函数有:
```
add(x,y)        #数组加法
subtract(x,y)   #数组减法
multiply(x,y)   #数组乘法
divide(x,y)     #数组除法,如果x和y都是整数,那么执行整数除法
true_divide(x,y)  #数组除法,返回精确值
floor_divide(x,y) #数组除法,取整
negative(x)       #返回-x
power(x,y)        #返回x^y
remainder(x,y)    #返回x%y
equal(x,y)           #判断对应元素是否相等,返回对应的bool数组
not_equal(x,y)       #判断对应元素是否不相等,返回对应的bool数组
less(x,y)            #判断对应x<y,返回对应的bool数组
less_equal(x,y)      #判断对应x<=y,返回对应的bool数组
greater(x,y)         #判断对应x>y,返回对应的bool数组
greater_equal(x,y)   #判断对应x>=y,返回对应的bool数组
np.logical_and       #相当于Python中的and逻辑与
np.logical_or        #相当于Python中的or逻辑或
np.logical_not       #相当于Python中的not逻辑非
np.logical_xor       #相当于Python中的xor逻辑异或
```

# matplotlib
&emsp;&emsp;matplotlib是Python的绘图库,提供了类似matlab的绘图功能,采用面向对象技术实现.在大型程序中更加有效.

## pylot模块 
&emsp;&emsp;对面向对象技术进行了一定的封装,简化了绘图过程.示例代码如下:
```
# -*- coding:utf-8 -*-
from matplotlib import pyplot as plt # 常用plt重命名pyplot模块

plt.plot([0,1],[0,1])    # 画(0,0)到(1,1)的直线
plt.show()
```
&emsp;&emsp;图像如下:

![matplotlib_1](https://github.com/gaosiyan/PythonNotes/blob/master/Image/matplotlib_1.png?raw=true)

&emsp;&emsp;`plot`方法的第一个参数是x序列,第二个参数是y序列,这里可以直接输入Python中的列表序列,也可以输Numpy的数组.`plot(x,y)`将用x和y的对应元素画图.`plt.show()`将用阻塞的方式显示图像.

&emsp;&emsp;下面的方法先创建一个`Figure`图表对象,并将`Figure`图表对象当成当前对象进行作图:
```
# -*- coding:utf-8 -*-
import numpy as np
from matplotlib import pyplot as plt

x = np.linspace(0,10,1000)  #包含终点的1000个元素的等差数组
y = np.sin(x)
z = np.cos(x**2)

plt.figure(figsize=(8,4)) # 创建Figure对象,并作为当前的默认对象

plt.plot(x,y,label="$sin(x)$",color="red",linewidth=2)
plt.plot(x,z,"b--",label = "$cons(x)$")

plt.xlabel("Time(s)")
plt.ylabel("Volt")
plt.title("Pyplot")
plt.ylim(-1.2,1.2)
plt.legend()

plt.show()
```
&emsp;&emsp;图像如下:

![matplotlib_2](https://github.com/gaosiyan/PythonNotes/blob/master/Image/matplotlib_2.png?raw=true)

&emsp;&emsp;如果没有创建`Figure`图表对象,那么matplotlib将自动创建一个`Figure`图表对象,上面的`plt.figure(figsize=(8,4))`语句用于创建`Figure`图表对象,8和4分别是宽度和高度,单位是英寸(默认每英寸100像素),`plt.figure(figsize=(8,4))`就是800*400.`plot`的前两个参数分别表示x和y轴,关键字参数`label`用于设置标签









