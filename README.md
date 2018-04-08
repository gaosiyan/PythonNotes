- [pip命令](#pip命令)
- [os模块](#os模块)
- [sys模块](#sys模块)
- [常用函数](#常用函数)
- [math模块](#math模块)
- [shutil模块](#shutil模块)
- [运算符](#运算符)
- [字符串操作](#字符串操作)
- [字符串的编码和解码](#字符串的编码和解码)
- [正则表达式](#正则表达式)
- [Python代码基本框架](#python代码基本框架)
- [参考代码段](#参考代码段)
    - [文件迭代](#文件迭代)
    - [设置豆瓣源的Python脚本](#设置豆瓣源的python脚本)
    - [判断操作系统是32位还是64位](#判断操作系统是32位还是64位)
- [pyuic5.exe的使用](#pyuic5exe的使用)
- [Pylint的基本使用方法](#pylint的基本使用方法)
- [autopep8的使用](#autopep8的使用)
- [cx_Freeze 使用](#cxfreeze-使用)
- [PyQt5](#pyqt5)
    - [QCheckBox复选框对象](#qcheckbox复选框对象)
- [ctypes使用](#ctypes使用)
    - [ctypes类型和C类型对应表](#ctypes类型和c类型对应表)
    - [结构体](#结构体)
    - [指针](#指针)
    - [共享空间的传递](#共享空间的传递)
- [Ipython](#ipython)
- [Notebook](#notebook)
- [NumPy](#numpy)
    - [ndarray对象](#ndarray对象)
        - [shape属性](#shape属性)
        - [reshape方法](#reshape方法)
        - [数组元素类型](#数组元素类型)
        - [直接创建数组](#直接创建数组)
        - [存取元素](#存取元素)
    - [ufunc函数](#ufunc函数)
- [matplotlib](#matplotlib)
    - [pylot模块](#pylot模块)
    - [绘制子图](#绘制子图)
    - [matplotlib的配置文件](#matplotlib的配置文件)
    - [面向对象绘图](#面向对象绘图)
        - [Artist对象](#artist对象)
            - [Artist对象属性](#artist对象属性)
            - [Figure容器](#figure容器)
            - [Axes容器](#axes容器)
            - [Axis容器](#axis容器)
        - [面向对象的其它操作](#面向对象的其它操作)
    - [其它绘图函数](#其它绘图函数)
    - [完整代码](#完整代码)

# pip命令

&emsp;&emsp;pip 是Python的包管理工具

&emsp;&emsp;用pip更新自身`pip install -U pip`

&emsp;&emsp;在pip源中查找对应包`pip search PackageName`

&emsp;&emsp;用pip安装包`pip install PackageName`

&emsp;&emsp;用pip更新包`pip install -U PackageName`

&emsp;&emsp;用pip卸载包`pip uninstall PackageName`

&emsp;&emsp;列出当前安装的包`pip list`

&emsp;&emsp;列出所有过期的包`pip list --outdated`

&emsp;&emsp;使用豆瓣源安装`pip  install PackageName  -i  https://pypi.doubanio.com/simple/`

&emsp;&emsp;下载的whl文件也可以用上面的pip命令安装，带setup.py的文件执行`python setup.py install`

# os模块
`os.getcwd()    #返回当前目录`

`os.chdir(path) #改变当前路径`

`os.listdir(path)    #列举path目录下的所有文件和文件夹,包含隐藏文件，返回的是列表，不列出子目录中相关信息`

`os.path.getsize(path)  #返回文件的字节大小，若是文件夹返回0`

`os.path.isdir(path)     #存在的路径是否是目录，返回True或False，不存在返回False`

`os.path.isfile(filename)   #存在的路径是否是文件判断，返回True或False，不存在返回False`

`os.path.exists(path)   #文件或文件夹是否存在，返回True或False`

`os.path.split('D:\\pythontest\\ostest\\Hello.py')   #返回的是元组('D:\\pythontest\\ostest', 'Hello.py')`

`os.path.split('D:\\pythontest\\ostest\\') #返回的是元组('D:\\pythontest\\ostest', '')`

`os.path.split('D:\\pythontest\\ostest')   #返回的是元组('D:\\pythontest', 'ostest')`

`os.path.splitext("D:\\pythontest\\ostest\\test.exe")#分离文件名与扩展名,返回(D:\\pythontest\\ostest\\test,exe)元组,可做分片操作`

`os.path.join('D:\\pythontest', 'ostest')   #路径连接返回D:\\pythontest\\ostest`

`os.path.dirname('D:\\pythontest\\ostest\\hello.py')    #返回D:\\pythontest\\ostest`

`os.path.dirname('D:\\pythontest\\ostest\\')    #返回'D:\\pythontest\\ostest'`

`os.path.dirname('D:\\pythontest\\ostest')  #返回'D:\\pythontest'`

`os.path.basename('D:\\pythontest\\ostest\\hello.py')   #返回hello.py`

`os.path.basename('D:\\pythontest\\ostest\\')   #返回空字符`

`os.path.basename('D:\\pythontest\\ostest') #返回ostest`

`os.path.normpath(path) #路径规范`

`os.path.getmtime(path) #文件或文件夹的最后修改时间，从新纪元(1970年1月1日0时0分0秒)到访问时的秒数`

`os.path.getatime(path) #文件或文件夹的最后访问时间，从新纪元(1970年1月1日0时0分0秒)到访问时的秒数`

`os.path.getctime(path) #文件或文件夹的创建时间，从新纪元(1970年1月1日0时0分0秒)到访问时的秒数`

`os.stat(文件/目录) #os.stat(文件/目录).st_mtime属性是最后修改时间,st_mtime是创建时间`       

`os.remove()    #删除文件,不能用于文件夹删除`

`os.rmdir() #删除空目录`

`os.mkdir() #创建目录,只能创建一级目录`

`os.makedirs()  #创建多级目录`

`os.sep #属性,是路径分割符，对应于具体的操作系统\\或/,用于生成路径,str = dir + os.sep + filename`

`os.name    #属性,操作系统的相关信息`

`os.lineseq #属性,当前平台的行结束符,windows下是"\r\n",linux下是'\r'`

`os.environ #属性,以字典的形式返回当前系统的环境变量os.environ['path']相当于sys.path`

# sys模块
`sys.version_info   #属性,返回解释器的相关属性信息`

`sys.version    #属性,返回解释器的相关属性信息`

`sys.platform   #属性,操作系统相关信息`

`sys.executable #属性,Python解释器的绝对路径`

`sys.argv   #属性,命令行相关参数,是一个字符串列表sys.argv[0]是脚本路径,sys.argv[1]是第一个参数,多个参数用空格间隔,不能用逗号`

`sys.path   #属性,是字符串列表,返回当前的搜索路径[0]是当前脚本路径,用sys.path.append('path')用来追加路径`

`sys.stdin  #属性,当前的标准输入`

`sys.stdout #属性,当前的标准输出`

`sys.stderr #属性,当前的标准错误文件流`

`sys.modules    #属性,返回当前已经加载的模块名称,返回一个字典,模块名是键,路径是值`

`sys.maxsize    #属性返回平台自然表示的最大有符号整数返回,64位是2^63 - 1,32位是2^31 - 1`

`sys.exit() #结束方法,可以返回参数sys.exit(0)`

# 常用函数

`dir(模块名/类名) #返回可见的方法和属性,例如dir()返回当前模块的所有属性和方法,dir(str)返回str对象的所有属性和方法`

`hex(int对象)    #转换成16进制返回的是字符串`

`oct(int对象)    #转换成8进制返回的是字符串`

`bin(int对象)    #转换成2进制返回的是字符串`

`int(字符串对象)  #int转换成10进制时,注意两处,第一是要加双引号,第二是要注明输入的进制int('0x10',16),默认输入是10进制`

`print(end="\n",file=stdout)  #可以修改参数不输出换行或者重定向到文件`

`pow(x,y)           #x^y等同于x**y`

`abs()              #绝对值`

`round()            #返回数轴上最近的整数,round(number[,ndigits]),ndigits是保留的小数位数`

`pass               #空操作`

`input("请输入")    #命令行输入`

`cmp(x,y)           #x<y返回-1,x==y返回1,x>y返回1`

`range(3)           #返回迭代对象[0,1,2],可以指定开始位置range(1,3)返回[1,2],一般用于for语句迭代`
```
#循环打印0,1,2
for i in range(3):
    print(i)
```

`len(list/str)      #返回列表或者字符串的个数,对于列表返回最外层`

`repr(str)        #返回代引号的字符串"str"`

# math模块
&emsp;&emsp;Python自带的math模块,常用的方法如下:

&emsp;&emsp;`math.floor(5.2)`向下取整,返回5.0

&emsp;&emsp;`math.ceil(5.2)`向上取整,返回6.0

&emsp;&emsp;`math.sqrt(5.2)`算术平方根,返回浮点数,这里注意cmath模块的`cmath.sqrt()`执行的是复数运算

&emsp;&emsp;`math.log10(10)`以10为底的对数运算,这里返回1.0

&emsp;&emsp;`math.log(1024,2)`以2为底的对数运算,这里返回10,相当于log2 10

# shutil模块
&emsp;&emsp;Python自带shutil模块,常用的方法如下:

&emsp;&emsp;`shutil.copytree(src,dst)`文件夹拷贝

&emsp;&emsp;`shutil.rmtree(path)`文件夹删除

------
# 运算符
* C中的逻辑且`&&`在Python中是`and`;
* C中的逻辑或`||`在Python中是`or`;
* C中取反`!`在Python中是`not`;
* 支持位运算符,比如`&`(与),`|`(或),`^`(异或),`~`(非,按位取反);
* 支持+=等操作符,但是不支持自加等运算符;
* `>>`和`<<`是算术移位,符号位扩展;

# 字符串操作  

`str.strip()               #返回去掉泛空格后的字符串，可以指定字符`

`str.lstrip()              #左边`

`str.rstrip()              #右边`

`str.startswith("*")       #是否以*开始`

`str.endswith("*")         #是否以*结束`

`str.replace(old,new)      #字符串替换`

`str.split("tag")          #用tag分割字符串，返回分割后的列表`

`str.find("substr")        #返回首个匹配的位置,从0开始,找不到返回-1`

`str.isalpht()             #是否是字母`

`str.isdigit()             #是否是数字`

`in                        #字串判断操作符 substr in str 子串在str中返回true`

`str.split(分割符)         #用分割符分割字符串,参数为空时是空格,返回列表`

`join                      #字符串连接,"\\".join(["C:","test"])  C:\\test`

`list(str)                 #将字符串中的每个元素按照列表返回`

`int('42')                 #将字符串对象转换成int对象 42`

`str(42)                   #将int对象转换成字符串对象'42'`

------
# 字符串的编码和解码
&emsp;&emsp;源代码中`# -*- coding:utf-8 -*-`是告诉Python解释器,源文件中的字符串用UTF-8编码(是unicode编码的一种实现),这是一种推荐的源文件编码方式.类似的还有`gbk,utf-16,ascii`,`gbk`是中文编码,它是`gb2312`的一个超集,`# -*- coding:gbk -*-`

&emsp;&emsp;对于字符串的传输,要按照设计的编码标准来进行传输,传输前或者接收后需要将字符串按照特定方式进行编解码,字符串对应提供了对应的编解码方法:

`str.decode('gb2312') #将str按照gb2312解码,返回对应的unicode编码`

`str.encode('gb2312') #将str(unicode编码)转码成gb2312编码`

&emsp;&emsp;decode的作用是其它编码的字符串解码成unicode,encode作用是将unicode编码的字符串重新编码,过程如下:

&emsp;&emsp;&emsp;&emsp;decode(特定编码)&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;encode(特定编码)        
&emsp;&emsp;特定编码--------------->unicode编码--------------->特定编码

&emsp;&emsp;Python中的str对象都是unicode编码的,非unicode是bytes对象可以用type进行测试,对于字符串明确需要存放为bytes对应而不是str需要加b前缀,如下:
```
str1 = "Hello"

type(str1)
Out[2]: str

str1 = b"Hello"

type(str1)
Out[4]: bytes
```

&emsp;&emsp;Python中打开文件报UnicodeDecodeError的解决方案:

* 方案1 `file = open(file,encoding='utf-8')`
* 方案2 `file = open(file,'rb')`

# 正则表达式
&emsp;&emsp;正则表达式(regex)是由一些字符和特殊符号组成的字符串，能够按照一定的模式匹配一系列相似的字符串。Python通过标准库的re模块，来支持正则表达式。Python中可以立即执行匹配,也可以将模式字符串编译成模式对象后,将模式对象与字符串匹配.

* 立即执行匹配

```
import re

text1 = 'Hello spam...World'
text2 = 'Hello spam..other'

#正则表达式'Hello(.*)World'表示寻找Hello和World之间的所有字符
matchobj = re.match('Hello(.*)World',text2)
print(matchobj)
#匹配失败,这里返回None,这里的matchobj在if语句中对应False
```
&emsp;&emsp;上面的`match`方法第一个参数是模式字符串,Hello和World代表字符串本身,`(.*)`,代表任何字符匹配0到多次.其中的`.`表示任何字符但是不包含\n,其中的`*`表示匹配0次或多次前面出现的正则表达式.两边的括号,代表保留匹配上的字串,另存为子组,下面的代码是成功匹配的示例:

```
import re

text1 = 'Hello spam...World'
text2 = 'Hello spam..other'

#正则表达式'Hello(.*)World'表示寻找Hello和World之间的所有字符
matchobj = re.match('Hello(.*)World',text1)

if matchobj:
    print("匹配成功")
```
&emsp;&emsp;上面的代码匹配成功,`matchobj`是一个匹配对象,可以用if语句测试是`True`. `matchobj.group()`返回匹配上的整个字符串,也可以用`matchobj.group(0)`,这里是`'Hello spam...World'`.`matchobj.group(1)`返回匹配上的第一个子串,这里是`spam...".group(num=0)`匹配的整个表达式的字符串,`group()` 可以一次输入多个组号，在这种情况下它将返回一个包含那些组所对应值的元组。groups()	返回一个包含所有小组字符串的元组，从 1 到 所含的小组号。预编译匹配的版本如下:

* 预编译匹配

```
import re

text1 = 'Hello spam...World'
text2 = 'Hello spam..other'

pattobj = re.compile('Hello(.*)World')

matchobj = pattobj.match(text1)

if matchobj:
    print("匹配成功")
```
&emsp;&emsp;对于一个模式的多次匹配建议预编译,这样会大幅提高匹配速度`.[]`代表字符集匹配,比如`[\t]*`表示匹配0次或多次空格或者制表符,正则表达式示例：
 ``` 
foo 无特殊符号，只能匹配 foo
foo|bar 匹配foo或bar
b.b 其中的.匹配除了\n外的所有单个字符
^Dear 其中的^表示匹配起始位置
sh$ 表示匹配以sh结尾的字符
* 匹配0次或多次前面出现的正则表达式
+ 匹配1次或多次前面出现的正则表达式
? 匹配0次或1次前面出现的正则表达式
{N}匹配N次前面出现的正则表达式
{M,N}匹配M~N次前面出现的正则表达式
[...]匹配字符集中的单个字符
[x-y]匹配x-y内的单个字符
[^...]不匹配字符集中的字符
\d 匹配任何十进制数字与[0-9]类似，\D与\d相反
\w匹配任何字母和数字，\W相反
\s匹配任何泛空格字符，回车，制表，空格，\S与之相反
 ``` 
 
# Python代码基本框架
``` 
# -*- coding:utf-8 -*-
if __name__ == '__main__':
    import os
    import sys
 ``` 

# 参考代码段
## 文件迭代
```python
# -*- coding: utf-8 -*-
"""
os.walk()的使用,用于迭代目录下的所有文件
目录结构:
rootdir ---> dir0 -> 1.txt,2.txt
         |-> dir1 -> 3.txt
         |-> dir2 -> 空目录
         |-> 4.txt
os.walk('rootdir') 返回一个三元元组(root,dirs,files),下面的代码用于迭代所有文件:
    第一次迭代(root,dirs,files) = (rootdir,[dir0,dir1,dir2],[4.txt])
    第二次迭代(root,dirs,files) = (rootdir\dir0,[],[1.txt,2.txt])
    第三次迭代(root,dirs,files) = (rootdir\dir1,[],[3.txt])
    第三次迭代(root,dirs,files) = (rootdir\dir2,[],[])
"""
for(root,dirs,files) in os.walk('rootdir'):
    print(root + os.sep + dirs + os.sep + files)
```

## 设置豆瓣源的Python脚本
```  
# -*- coding:utf-8 -*-
import os
ini="""[global]
index-url = https://pypi.doubanio.com/simple/
[install]
trusted-host=pypi.doubanio.com
"""
pippath=os.environ["USERPROFILE"]+"\\pip\\"
if not os.path.exists(pippath)
    os.mkdir(pippath)
with open(pippath+"pip.ini","w+") as f:
    f.write(ini)
```  

## 判断操作系统是32位还是64位
&emsp;&emsp;这里推荐这种方法,sys或者os模块的其他方法是判断Python解释器的版本,在64位机器上安装的32位解释器的话,会判断错误
```  
# -*- coding:utf-8 -*-
def Is64Windows():
    #64位返回true
    return 'PROGRAMFILES(X86)' in os.environ
```

# pyuic5.exe的使用
&emsp;&emsp;pyuic5.exe用于将Qt Designe生成的*.ui文件编译成Python代码，在cmd中执行下面的命令将生成的ui文件重定向输出到py:文件`pyuic5 *.ui > 1.py `   

# Pylint的基本使用方法
&emsp;&emsp;Pylint是Python源代码的静态检查工具

&emsp;&emsp;`pylint *.py`   处理*.py文件

&emsp;&emsp;违反编码习惯-C

&emsp;&emsp;代码需要重构,相当差-R

&emsp;&emsp;警告-W

&emsp;&emsp;错误-E

&emsp;&emsp;致命错误-F

# autopep8的使用
&emsp;&emsp;autopep8是第3方模块,主要用于按照pep8规范排版,下面的命令将源文件重新排版

&emsp;&emsp;`autopep8.exe --in-place *.py`

# cx_Freeze 使用
&emsp;&emsp;cx_Freeze可以将Python编译成windows的exe可执行文件，需要安装VC2015运行时，安装完成后执行 `python cxfreeze-postinstall`

&emsp;&emsp;控制台程序编译

&emsp;&emsp;`cxfreeze *.py` 生成dist目录；

&emsp;&emsp;GUI程序编译

&emsp;&emsp;`cxfreeze *.py --base-name=win32gui`

# PyQt5
## QCheckBox复选框对象
&emsp;&emsp;对象的创建

&emsp;&emsp;`self.checkBox = QtWidgets.QCheckBox(父容器)`这里的父容器可以是对话框对象,主窗口对象等

&emsp;&emsp;常用方法

&emsp;&emsp;`self.checkBox.checked()`返回True表示被勾选,False没有被勾选

&emsp;&emsp;`self.checkBox.setEnabled(False)`显示但是不使能,显示是灰色

&emsp;&emsp;`self.checkBox.setCheckable(False)`显示并且不是灰色,但是不能操作

&emsp;&emsp;`self.checkBox.setChecked(True)`可以操作的情况下,设置默认选中

&emsp;&emsp;`self.checkBox.setText(text)`设置复选框显示的文本

# ctypes使用
&emsp;&emsp;Python 可以通过使用 ctypes 模块调用 c 函数，这其中包括可以定义 c 的变量类型（包括结构体类型、指针类型）,可以和共享库以及Dll中的C函数进行通信.它是Python的标准模块,建议用`from ctypes import *`进行导入.

&emsp;&emsp;C类型定义
```
i = c_int(45)   #定义一个 int 型变量，值为 45,这里的i可以直接传给C函数int类型的入参

i.value         #打印变量的值
Out[3]: 45

i.value = 56    #修改变量的值

i.value
Out[5]: 56
```

## ctypes类型和C类型对应表

| ctypes type  |           C type           |       标准Python类型 |
|--------------|:--------------------------:|-----------------:|
| c_bool       |            _Bool           |          bool(1) |
| c_char       |            char            |     1个字节的bytes对象 |
| c_wchar      |           wchar_t          |   1个字符的unicode对象 |
| c_byte       |            char            |              int |
| c_ubyte      |        unsigned char       |              int |
| c_short      |            short           |              int |
| c_ushort     |       unsigned short       |              int |
| c_int        |             int            |              int |
| c_uint       |        unsigned int        |              int |
| c_long       |            long            |              int |
| c_ulong      |        unsigned long       |              int |
| c_float      |            float           |            float |
| c_double     |           double           |            float |
| c_longdouble |         long double        |            float |
| c_char_p     |   char * (NUL terminated)  |   string or None |
| c_wchar_p    | wchar_t * (NUL terminated) |  unicode or None |
| c_void_p     |           void *           | int/long or None |

## 结构体
&emsp;&emsp;Python中如何定义C中对应的结构体,如C中下面的结构体
```
struct MyStruct
{
    float x;
    float y;
};
```
&emsp;&emsp;对应于Python中的类,必须继承自`ctypes.Structure`
```
class MyStruct(Structure):
    _fields_ = [("x", c_float), 
                ("y", c_float)]

MyStruct1 = MyStruct()  #创建对应的类/结构体
MyStruct1.x = c_float(1.2)  #结构体元素赋值
MyStruct1.y = c_float(1.5)  
ptMyStruct = pointer(MyStruct1)  #创建并返回一个指向MyStruct1的指针实例,这里的MyStruct1必须是一个存在的实例对象
```

## 指针
&emsp;&emsp;`byref(x [, offset])`返回 x 的地址,x 必须为ctypes类型的一个实例.相当于c的 &x.offset 表示偏移量.例如下面的代码:
```
a = c_int(10)
ptr = byref(a)   #返回a的地址
```

&emsp;&emsp;`pointer(x)`创建并返回一个指向 x 的指针实例, x 是一个实例对象不一定必须是ctypes类型,上面已经描述

&emsp;&emsp;`POINTER(type)`返回一个类型,这个类型是指向 type 类型的指针类型.type 是 ctypes 的一个类型,相当于C中的指针定义,比如下面的代码,定义了两个指针,但是都指向a
```
>>> a = c_int(66)         # 创建一个 c_int 实例
>>> b = pointer(a)        # 创建指针
>>> c = POINTER(c_int)(a) # 创建指针,并指向a
>>> b
<__main__.LP_c_long object at 0x00E12AD0>
>>> c
<__main__.LP_c_long object at 0x00E12B20>
>>> b.contents            # 输出 a 的值,获取指针指向地址的内容
c_long(66)
>>> c.contents            # 输出 a 的值
c_long(66)
```

## 共享空间的传递
&emsp;&emsp;传递字符串时一定要将字符串转成byte,也就是需要进行str和byte类型的转换:
```
str->bytes：bytes(s, encoding='utf-8')
bytes->str：str(b, encoding='utf-8')
```
&emsp;&emsp;或者:
```
mybyte = b"test"
pcu = c_char_p(mybyte)  #字符串指针
```
&emsp;&emsp;也可以在Python中创建空间,将该空间的首地址通过指针的形式传递给C,如下面的代码:
```
myBuffer = create_string_buffer(1024) #创建1024字节的byte的空间
myBuffer.value = b"test"  #赋值
puc = POINTER(c_char)
puc = myBuffer.raw   #创建字符串指针,该指针指向字符串首地址
```

# Ipython
&emsp;&emsp;`函数名/模块名?`   显示相关的帮助信息,注意函数名在这里不能带括号`ESC`退出

# Notebook
&emsp;&emsp;`%matplotlib inline` 内嵌图表,不用调用plt.show()

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
&emsp;&emsp;可以将结果直接输出到x(x和y共享内存),如下面的代码:
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
add(x,y)        #数组加法,+运算符重载,z = x + y, z = add(x,y),可以写成add(x,y,z)
subtract(x,y)   #数组减法,-运算符重载,用法同上
multiply(x,y)   #数组乘法,*运算符重载,用法同上
divide(x,y)     #数组除法,如果x和y都是整数,那么执行整数除法,/运算符重载,用法同上
true_divide(x,y)  #数组除法,返回精确值/运算符重载,用法同上
floor_divide(x,y) #数组除法,取整//运算符重载,用法同上
negative(x)       #返回-x,负号运算符重载
power(x,y)        #返回x^y,**运算符重载
remainder(x,y)    #返回x%y,%运算符重载
equal(x,y)           #判断对应元素是否相等,返回对应的bool数组,==运算符重载
not_equal(x,y)       #判断对应元素是否不相等,返回对应的bool数组,!=运算符重载
less(x,y)            #判断对应x<y,返回对应的bool数组,<运算符重载
less_equal(x,y)      #判断对应x<=y,返回对应的bool数组,<=运算符重载
greater(x,y)         #判断对应x>y,返回对应的bool数组,>运算符重载
greater_equal(x,y)   #判断对应x>=y,返回对应的bool数组,>=运算符重载
np.logical_and       #相当于Python中的and逻辑与,没有运算符重载
np.logical_or        #相当于Python中的or逻辑或,没有运算符重载
np.logical_not       #相当于Python中的not逻辑非,没有运算符重载
np.logical_xor       #相当于Python中的xor逻辑异或,没有运算符重载
```

&emsp;&emsp;当标量于数组运算时,标量会自动扩展,不同大小的数组可以用广播的形式.

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

&emsp;&emsp;如果没有创建`Figure`图表对象,那么matplotlib将自动创建一个`Figure`图表对象,上面的`plt.figure(figsize=(8,4))`语句用于创建`Figure`图表对象,8和4分别是宽度和高度,单位是英寸(默认每英寸100像素),`plt.figure(figsize=(8,4))`就是800*400.

&emsp;&emsp;`plot`的相关参数:

* 前两个位置参数分别表示x和y轴;
* 关键字参数`label`用于设置标签,标签前后用`$`后`matplotlib`后用内嵌的`LaTex`引擎将其显示成数学公式;
* 关键字参数`color`用于指定颜色;
* 关键字参数`linewidth`用于指定线宽,单位是像素可以不是整数,`linewidth`简写成`lw`;
* 可以通过第三个位置参数,格式化字符串指定颜色和线的类型,比如上面的`plt.plot(x,z,"b--",label = "$cons(x)$")`,其中`b`表示蓝色,`--`表示虚线.IPython中输入`plt.plot?`可以查看格式化字符串的详细说明;

&emsp;&emsp;`xlabel,ylabel,title,ylim,legend`等方法是Axes(坐标轴对象)的方法,`plot`方法是在`Axes`坐标轴对象上作图,而`Axes`坐标轴对象基于`Figure`图表对象.上面的代码没有显示创建`Axes`坐标轴对象,那么`matplotlib`会自动创建充满整个`Figure`对象的`Axes`坐标轴对象.其中:

* `xlabel,ylabel`用于设置x和y轴的标题;
* `title`设置坐标轴的标题;
* `xlim,ylim`设置坐标轴的范围;
* `legend`显示图例,上图右下角的小矩形

&emsp;&emsp;`plt.save(*.jpg)`可以用于保存当前的`Figure`图表.

## 绘制子图
&emsp;&emsp;`subplot`用于在一个`Figure`中绘制多个子图,代码如下:
```
# -*- coding:utf-8 -*-
from matplotlib import pyplot as plt

plt.subplot(2,2,1)
plt.title("1")
plt.subplot(2,2,2)
plt.title("2")
plt.subplot(2,1,2)
plt.title("3")
plt.show()
```

&emsp;&emsp;图像如下:

![matplotlib_3](https://github.com/gaosiyan/PythonNotes/blob/master/Image/matplotlib_3.png?raw=true) 

&emsp;&emsp;`plt.subplot(2,2,1)`第一个参数表示划分成多少行,这里是2行,第而个参数表示划分成多少列,这里是2列.所以图像被分成2*2个子块,第三个参数表示在那个子块中画图,从左到右,从上至下由1开始编号.另外如果3个参数都小于10的话`plt.subplot(2,2,1)`可以写成`plt.subplot(221)`,`plt.subplot(2,2,2)`表示在第2个子块位置画图.`plt.subplot(2,1,2)`表示重新划分,成2行1列在第2个位置画图,效果就如上图.

## matplotlib的配置文件
&emsp;&emsp;绘制过程中用到的颜色,线形,字体等很多都直接使用`matplotlib`的默认配置,默认配置保存在一个名为`matplotlibrc`的配置文件中,通过修改配置文件,可以设置默认参数.可以有多个`matplotlibrc`配置文件,按照优先级使用,优先级如下:

* 程序当前路径下的`matplotlibrc`配置文件;
* 用户目录的`matplotlibrc`配置文件,通常位于用户目录下的`.matplotlib`目录下;
* 系统配置文件,在`matplotlib`安装目录下的`mpl-data`中.

&emsp;&emsp;可以通过下面的代码确认当前正在使用的配置文件路径:
```
import matplotlib
matplotlib.matplotlib_fname()
Out[6]: 'C:\\Anaconda3\\lib\\site-packages\\matplotlib\\mpl-data\\matplotlibrc'
```
&emsp;&emsp;`matplotlibrc`实际上是一个字典,通过`matplotlib.rc_params()`获取字典的内容.`matplotlib`被载入后会将这个文件加载到`matplotlib.rcParams`字典中,可以对该字典进行重新修改,而不影响原始`matplotlibrc`配置文件.如果修改了`matplotlib.rcParams`字典又想回到默认的`matplotlibrc`配置文件用`matplotlib.rcdefaults()`.`matplotlib`默认的字体不支持中文,要显示中文可以修改配置文件或者在程序中指定字体.通过`matplotlib.rcParams["font.family"] = "字体名称"`的方式修改字体.比如`matplotlib.rcParams["font.family"] = "simhei"`配置成黑体字体,通过下面的代码获取所有字体:
```
from matplotlib.font_manager import fontManager
fontManager.ttflist
```
&emsp;&emsp;Windows10的字体都位于`C:\Windows\Fonts`下,在程序中配置字体更加灵活,可以配置多种字体但是比较复杂,如下:
```
# -*- coding:utf-8 -*-
from matplotlib import pyplot as plt
from matplotlib.font_manager import FontProperties

font1 = FontProperties(fname=r"C:\Windows\Fonts\simhei.ttf",size = 14) # 配置字体对象和大小
plt.subplot(221)
plt.title("图1",fontproperties = font1) # 应用字体对象
plt.subplot(222)
plt.title("2")    # 默认字体
plt.subplot(212)
plt.title("3")
plt.show()
```

## 面向对象绘图
&emsp;&emsp;`matplotlib`采用了面向对象技术,前面只用了简单的pyplot模块,屏蔽了很多细节,了解面向对象过程可以进一步的控制绘图细节.

### Artist对象
&emsp;&emsp;对于绘图最基础的对象是`Artist`对象.`Artist`对象的子类有简单类型和容器类型.简单类型的`Artist`对象是标准的绘图原件,例如:`Line2D`(2维直线),`Rectangle`(矩形),`Text`(文本),`AxesImage`(坐标图像)等.容器类型`Artist`对象可以包含很多简单类型的`Artist`对象,使他们组织成一个整体,例如:`Axis`(坐标轴),`Axes`(坐标系),`Figure`(图形)等.我们画函数图像时基本的步骤如下:

1. 创建`Figure`(图形)对象;
2. 为`Figure`对象,创建一个或多个`Axes`(坐标系)对象;
3. 调用`Axes`对象的方法创建各种简单的`Artist`对象.

&emsp;&emsp;代码如下:
```
#创建Figure对象
fig = plt.figure()   

#为Figure创建坐标轴对象,这里的取值是坐标轴在figure中的边距和大小,取值范围[0,1],[左右边距,上下边距,宽,高]
ax = fig.add_axes([0.15,0.1,0.7,0.3])

# 调用Axis对象的plot方法绘制直线,并返回该直线的Line2D对象,ax.plot一次可以绘制多条曲线,所以会返回一个列表,我们只取列表第一个元素
line = ax.plot([1,2,3],[1,2,1])[0] 
```

&emsp;&emsp;`Axes`(坐标系)对象的`lines`属性(比如上面的代码用`ax.lines`)以列表形式返回当前坐标系的所有`Line2D`对象,如果想删除曲线,直接从此列表中删除即可.

&emsp;&emsp;`Axes`(坐标系)对象`ax`的其它方法:

&emsp;&emsp;`ax.set_xlabel("x轴标题")`设置X轴名称,实际上是调用`self.xaxis.set_label_text("x轴标题")`也就是修改坐标系对象的`Axis`(坐标轴)对象的相关属性.

&emsp;&emsp;`ax.xaxis` 是ax坐标系对象的X轴`Axis`坐标轴对象,`ax.xaxis.label`获取坐标轴标题对象是一个`Text`(文本)对象,通过`ax.xaxis.label.get_text()`来获取,也可以通过`Text`(文本)对象的`_text`属性获取`ax.xaxis.label._text`.

#### Artist对象属性
&emsp;&emsp;每一个绘图元件都基于`Artist`对象,而每个`Artist`对象都有很多属性来控制显示效果,比如`Figure`对象和`Axes`对象都有`patch`属性用于控制背景,它又是一个`Rectangle`(矩形)对象.所有`Artist对象`的公有(常用)属性如下:

* alpha 透明度,0到1之间,0为完全透明,1为完全不透明;
* axes 拥有当前Artist对象的坐标轴对象,比如Line2D对象的坐标轴容器,可能为None;
* figure 拥有当前Artist对象的figure对象,可能为None;
* label 文本标签;
* visible 是否可以;

&emsp;&emsp;上面的属性可以通过`对象.set_label()`或者`对象.get_label()`的方式修改或者访问.

#### Figure容器
&emsp;&emsp;要修改某个坐标轴或者曲线的属性时先要获取该对象,就是如何找到对应的`Artist`对象,前面的代码`ax = fig.add_axes([0.15,0.1,0.7,0.3])`,在Figure容器中创建坐标系并返回坐标系对象`ax`,可以用过`ax`操作坐标系.例如`ax.grid(True)`显示当前坐标系的网格线.

&emsp;&emsp;Figure常用属性:

* axes 返回当前Figure容器中的Axes对象列表;
* patch 返回当前Figure容器中的背景属性;
* lines 返回当前Figure容器中的Line2D对象列表,可以直接在Figure上面用Line2D函数创建曲线,不一定基于坐标系对象;
* texts 返回当前Figure容器中Text对象列表;

#### Axes容器
&emsp;&emsp;Axes容器是绘图最核心的容器,`plot`方法实际上是`Axes`对象的方法,它在对应的`Axes`对象上画曲线,当没有`Axes`对象时,`matplotlib`会自动创建.和`Figure`对象一样它有一个`patch`背景属性,当`Axes`是直角坐标系时,`patch`属性是一个`Rectangle`(矩形)对象,当`Axes`是极坐标系时,`patch`属性是一个`Circle`对象,下面的代码将Axes的背景设置为绿色:
```
fig = plt.figure()
ax = fig.add_subplot(111)
ax.patch.set_facecolor("green")
```
&emsp;&emsp;`Axes`对象的`plot`方法会创建一组`Line2D`对象并将其添加到`Axes.lines`属性中,plot方法的关键字参数实际上是传递给Line2D对象的.

&emsp;&emsp;Axes常用属性:

* artists artists对象列表;
* patch 背景对象;
* lines Line2D对象列表;
* texts Text对象列表;
* xaxis X轴对象;
* yaxis Y轴对象.

#### Axis容器
&emsp;&emsp;Axis是坐标轴对象,包括刻度线,刻度标签,坐标网格以及坐标文本等对象.刻度包括主刻度和副刻度.

&emsp;&emsp;`get_major_ticks()`获取主刻度

&emsp;&emsp;`get_minor_ticks()`获取副刻度

&emsp;&emsp;每一个刻度线都是一个`XTick`或`YTick`对象,包括刻度线和刻度标签,通过坐标轴对象`axis`的`get_ticklocs()`方法获取刻度位置列表,`get_ticklabels()`获取刻度文本列表.代码示例:
```
axis = get_ticklines()                # 获取刻度线对象是一个Line2D对象列表,默认是获取主刻度线
axis = get_ticklines(minor = True)    # 获取副刻度线
xaxis.set_label_text("X轴")           # 修改x轴名称同plt.xlabel("Time(s)")
```
&emsp;&emsp;修改坐标轴刻度文本和刻度线的代码:
```
for label in axis.get_ticklabels():   # 遍历所有刻度标签文本,只有主刻度有标签文本
    label.set_color("red")
    label.set_rotation(45)            # 文本逆时针旋转45度
    label.set_fontsize(16)            # 文本字体大小

for line in axis.get_ticklines():     # 遍历所有刻度线对象
    line.set_color("green")           # 刻度线为绿色
    line.set_markersize(25)           # 刻度线高度
    line.set_markeredgewidth(3)       # 刻度线宽度
```

### 面向对象的其它操作
&emsp;&emsp;`fig = plt.gcf()` 返回当前的Figure对象

&emsp;&emsp;`plt.scf(fig)` 切换当前的Figure对象

&emsp;&emsp;`plt.getp(fig)` 返回当前的Figure对象的所有属性,可以用过set_或者get_的方式访问修改

&emsp;&emsp;`line.get_linewidth()`获取Line2D对象的线宽 

&emsp;&emsp;`axes = plt.gca()` 返回当前的坐标轴对象,默认创建是可以用这个方法返回坐标系并操作它

&emsp;&emsp;`plt.sca(axes)` 默认坐标系切换,可以在多个坐标系中来回切换当前坐标系

&emsp;&emsp;判断对象是哪个类可以用`对象名称.__class__.__name__`

## 其它绘图函数
&emsp;&emsp;`plot`函数用于绘制曲线;

&emsp;&emsp;`scatter`函数用于绘制散点图,星座图;

&emsp;&emsp;`pie`函数用于饼图;

&emsp;&emsp;`bar`函数用于绘制直方图;

&emsp;&emsp;`stem`函数用于绘制火柴杆图;

&emsp;&emsp;具体示例可以参考[matplotlib官网示例](https://matplotlib.org/gallery/index.html) 

## 完整代码
```
# -*- coding:utf-8 -*-
__version__ = "0.1"

"""
周期是1秒的连续函数x(t) = 2*cos(2*pi*t)的Ts采样图
"""

import numpy as np
from matplotlib import pyplot as plt

def main():
# 用于模拟连续函数 x(t) = 2cos(2*pi*t),画0到10S的图形
    t = np.linspace(0,10,10000)     # 0~10秒取10000个点,用离散模拟连续
    xt = 2 * np.cos(2 * np.pi * t)  # x(t) = 2cos(2*pi*t) 周期是1

    # Ts = 0.1秒对 x(t) = 2cos(2*pi*t)进行采样 -> x[n] = x[n*Ts] = 2cos(2*pi*(n*Ts))采样
    Ts = 0.1                        # 0.1S采样一次
    n = np.arange(0,101,1)          # 10S有101个采样点[0,1,..100]
    xn = 2 * np.cos(2 * np.pi * np.multiply(n,Ts))  # x[n*Ts] = 2cos(2*pi*(n*Ts))

    # 序列创建完毕开始画图
    fig = plt.figure()                        # 创建Figure对象

    # 画连续函数x(t) = 2cos(2*pi*t)
    ax0 = fig.add_subplot(2,1,1)              # 创建Axis对象  
    ax0.plot(t,xt)                            # 当成连续函数
    ax0.grid(True)                            # 打开网格
    ax0.set_title("$x(t) = 2*cos(2*\pi*t)$")  # LaTex表达式
    ax0.xaxis.set_label_text("t")
    ax0.yaxis.set_label_text("$x(t)$")

    # 画离散函数x[n] = x[n*Ts] = 2cos(2*pi*(n*Ts))
    ax1 = fig.add_subplot(2,1,2)

    markerline, stemlines, baseline = ax1.stem(n,xn) # 火柴杆图    
    """
    markerline -> Line2D对象,火柴杆头部的曲线对象
    stemlines -> Line2D对象列表,每个火柴杆连线,下面的代码控制不显示火柴棒,只有火柴头
    for line in stemlines:
        line.set_visible(False)

    baseline -> x轴基线
    """
    baseline.set_visible(False)                  # 关闭X轴的基线显示
    ax1.grid(True)                               # 打开网格
    ax1.set_title("$x[n] = 2*cos(2*\pi*n*Ts)$")  # LaTex表达式
    ax1.xaxis.set_label_text("n")
    ax1.yaxis.set_label_text("$x[n]$")  

    #plt.subplots_adjus用于控制边距,有6个关键字参数,其中top,bottom,left,right整个图的上下左右边距,hspace子图间的垂直间距,wspace子图间的水平间距
    plt.subplots_adjust(hspace=0.5)
    plt.show()

if __name__ == '__main__':
    main()
```

&emsp;&emsp; 效果图如下:

![matplotlib_4](https://github.com/gaosiyan/PythonNotes/blob/master/Image/matplotlib_4.png?raw=true) 









































