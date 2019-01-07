# 基础-Numpy

[TOC]



### 1.概念

Python开源的数值计算扩展



##### 优点

1. 强大的N维数组对象Array
2. 成熟的函数库
3. 用于整合C/C++和Fortran代码的工具包
4. 实用的线性代数、傅里叶变换和随机数生成函数
5. numpy和稀疏矩阵运算包scipy配合使用更加强大



##### 参数介绍

```
ndim：维度
shape：形状（各维度的长度）
size：总长度
dtype：元素类型

loc:锚点
scale:波动范围
axi=1 :行
axi=0 :列
```



### 2.tdarray&ndarray

##### 介绍

numpy数组类型

tdarray:一维数组

ndarray:多维数组(矩阵)



所有的赋值操作都不会创建副本,内存共享,如果需要创建副本,则需要copy()操作复制一个

##### 引入

```python
import numpy as np
```



##### 通用方法列表

```python
num=np.array([1,2,3,4,5]) #创建数组
num.reshape((行数,-1)) #更改数组为指定行数,-1是占位符
num.reshape((-1)) #更改数组为一行

#查看
type(num) #类型 numpy.tdarray
num.shape #查看数组各维度大小的元组

#索引
num[行切片][列切片] #查看指定范围行列的数据,两个切片查询,数组维度不变
num[行][列] #查看指定行列的数据,只有有一个是整数索引,维度就会减一
result_index=num>2 #以bool数组的形式查看元素中大于2的数组
num[result_index] #查看大于2的元素生成的新数组


#遍历
nditer(矩阵) #遍历矩阵

#修改
num[行切片][列切片]=指定值 #修改指定值
num[[行数组][列数组]]+=指定值 #修改指定范围的行列的值增加指定值

#复制
copy(数组) #复制一个副本
```



##### Routines方法列表

```python

juzhen=np.zeros(shape, dtype=float, order='C') #创建初始值为0的矩阵,形状shape
juzhen=np.ones(shape, dtype=None, order='C') #创建初始值为1的矩阵
juzhen=np.eye(N, M=None, k=0, dtype=float) #创建满秩矩阵,左上角到右下角连线为1,其余为0

#np.full(shape=(100,250,3),fill_value=125,order='C')
juzhen=np.full(shape, fill_value, dtype=None, order='C') #创建初始值为fill_value的矩阵 

juzhen=np.linspace(start, stop, num=50, endpoint=True, retstep=False, dtype=None) #创建一个[start,stop]之间平均分隔num此的矩阵 
juzhen=np.arange(start,stop,step) #按照step步幅(默认1),创建一个[start,stop)的连续数组

juzhen=np.random.randn(d0, d1, ..., dn) #创建标准正太分布矩阵
juzhen=np.random.normal(loc=0.0, scale=1.0, size=None) #创建正太分布矩阵 loc为锚点,scale为波动范围,size为矩阵内元素数量
juzhen = np.random.random(size = (200,600,3)) #创建随机三维数组,200为高度,600为宽度
```



### 3.Numpy数据类型

##### 类型类型

```python
名称	描述
bool_	#布尔型数据类型（True 或者 False）
int_	#默认的整数类型（类似于 C 语言中的 long，int32 或 int64）
intc	#与 C 的 int 类型一样，一般是 int32 或 int 64
intp	#用于索引的整数类型（类似于 C 的 ssize_t，一般情况下仍然是 int32 或 int64）
int8	#字节（-128 to 127）
int16	#整数（-32768 to 32767）
int32	#整数（-2147483648 to 2147483647）
int64	#整数（-9223372036854775808 to 9223372036854775807）
uint8	#无符号整数（0 to 255）
uint16	#无符号整数（0 to 65535）
uint32	#无符号整数（0 to 4294967295）
uint64	#无符号整数（0 to 18446744073709551615）
float_	#float64 类型的简写
float16	#半精度浮点数，包括：1 个符号位，5 个指数位，10 个尾数位
float32	#单精度浮点数，包括：1 个符号位，8 个指数位，23 个尾数位
float64	#双精度浮点数，包括：1 个符号位，11 个指数位，52 个尾数位
complex_	#complex128 类型的简写，即 128 位复数
complex64	#复数，表示双 32 位浮点数（实数部分和虚数部分）
complex128	#复数，表示双 64 位浮点数（实数部分和虚数部分）
```

numpy 的数值类型实际上是 dtype 对象的实例，并对应唯一的字符，包括 np.bool_，np.int32，np.float32，等等。



##### 类型优先级

str>float>int



##### 数据类型方法列表

```python
num.dtype() #查看数组中元素的类型,按照类型最大范围兼容原则
np.array([1.2,2.55,3],dtype(np.int64)) #修改数组元素为指定数据类型,小数部分被省略
```



### 4.Numpy数学运算与常用函数

```python
num1=np.array([[1,2],[5,6]])
num2=np.array([[5,3],[6,8]])

num3=np.array([[1,2],[5,6]])
num4=np.array([[5,3,3],[6,8,6]])
```



##### 数学运算列表

```python
#加减乘除

num1+num2 #矩阵对应元素相加
np.add(num1,num2) #矩阵对应元素相加

num1-num2 #矩阵对应元素相减
np.subtract #矩阵对应元素相减

num1*num2 #矩阵对应元素相乘
np.multiply #矩阵对应元素相乘

num1/num2 #矩阵对应元素相除
np.divide(num1,num2) #矩阵对应元素相除

#开放根
np.sqrt(num1) #开方根

#矩阵算法
num3.dot(num4) #矩阵相乘算法,注意,反过来是无法进行矩阵乘法的
np.dot(num3,num4) #矩阵相乘算法
'''
array([[17, 19, 15],
       [61, 63, 51]])
'''

```



##### 常用函数列表

```python
np.sum(num1,axis=1) #矩阵行相加
np.sum(num1,axis=0) #矩阵列相加
np.mean(num1) #矩阵所有数据的平均值
np.mean(num1,axis=1) #矩阵所有行的平均值
np.mean(num1,axis=0) #矩阵所有列的平均值
np.random.uniform(1,100) #生成1-100之间的随机值
np.random.randint(low, high=None, size=None, dtype='l') #创建[low-hight]之间随机,尺寸为size的矩阵
np.random.random((行,列,size=数量)) #创建指定行列矩阵的(0~1)的随机数,共生成size个
np.tile(num1,(1,2)) #重复矩阵,一行两列
'''
array([[3, 4, 3, 4],
       [5, 5, 5, 5]])
'''

num1.argsort() #排序,返回一个下标矩阵
num1.argsort(axis=0) #列排序,每一列从小到大
num.T #矩形转置(行转列)
num.transpose(a) #矩形转置(行转列)
np.vstack(num) #垂直旋转
np.hstack(num) #水平旋转
np.concatenate((num1,num2),axis=1) #级联,横向级联

np.split(arr,(index1,index2,..)) #按照指定下标分隔数组
np.vsplit(arr,(index1,index2,..)) #垂直方向分割数组
np.hplit(arr,(index1,index2,..)) #水平方向分割数组
```



### 5.广播

numpy矩阵中,列相同,行不同时,numpy运算可以自动补全维度

