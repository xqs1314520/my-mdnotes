# numpy

## numpy数组
```python
import numpy as np
b=np.array([4,'5',4])  #numpy数组只要数组出现非整形，就将其进行转换。也就是说数组只能存储同种数据
>>>['4' '5' '4']

#创建方式：
#利用列表生成
np.array[]
#arange函数
np.arange(x:y:z) #开始结束步长
# random函数生成随机数的数组，可以是N行N列，且每个元素都是0~1的随机数。
np.random.random((n,n))
#倘若我们要整型随机数，且约定范围，可以使用randint
e=np.random.randint(0,10,size=(3,4))

#使用函数生成特殊数组
a1=np.zeros((2,2)) #生成一个所有元素都是0的2行2列数组
a2=np.ones((2,2)) #生成一个所有元素都是1的2行2列数组
a3=np.full((2,2),7) #full 意思是全都是，生成一个2行2列全是7的数组
a4=np.eye(3)  #生成一个在对角线为1，其他元素均为0

```
数组创建历程参考文档
https://numpy.org/doc/stable/reference/routines.array-creation.html  


numpy数组的数据类型，整型就有int8 int16 int32 在处理不同类型的，不同范围的数值时，就可以采取不同的数据类型，提高了效率，节省了内存空间。
### 维度尺寸形状
```python
#ndim 获取数组维度
a1=np.array([1,2,3])
print(a1.ndim)
a2=np.array([[1,2,3],[4,5,6]])
print(a2.ndim)
a=np.array([
    [
        [1,2,3],
        [4,5,6]
    ],
    [
        [7,8,9],
        [10,11,12]
    ]
])
print(a.ndim)
print(a1.shape)
print(a2.shape)
print(a.shape)

#reshape 变形，参数自己设置，但是要满足元素总的个数不发生改变。
a4=a.reshape((4,3))

#一维数组只能是列数，行数为1
a5=a.reshape((12,))
print(a5)

#扁平化操作。返回一个一维数组
a6=a.flatten()
print(a6)


#ndarray.siza  获取数组中总的元素个数，
#count=a.size() 加了()会报错：TypeError: 'int' object is not callable。其实这是一个错误的语法。size后不需要加
count=a.size
print(count)


# itemsize返回数组中每个元素占的大小 单位是字节

itemsiza=a.itemsize
print(itemsiza)  #输出为4，表明4字节，
print(a.dtype)   #输出为int32


#size 配合itemsize 就可以获得整个数组的大小
total=itemsiza*count
print(total)

'''
数组一般达到三维就对其进行转换成二维
通过ndarray.ndim 可以获得数组的维数
ndarray.shape获得数组的形状（几行几列） shape返回的是一个元组，几个元素代表几维数组
ndarray.reshape 不会修改原来的数组，只会返回新的数组
ndarray.size 
ndarray.itemsize

'''
```

### 索引和切片

```python
#索引&切片
#对应一维数组而言，和列表完全相同
a1=np.arange(1,29)
print(a1[4])
#切片
print(a1[4:6])
# 使用步长
print(a1[::2])
# 使用负数
print(a1[-1])
#对于多维数组而言，以二维数组为例
#索引
a2=np.random.randint(0,10,size=(4,6))
print(a2)
#获取连续的某几行的数据 可以采用切片的方式
print(a2[0:2])
#获取指定几行的数据
print(a2[[0,2,3]])
#获取某行某列的数据,用逗号隔开，前面是行后面是列。
print(a2[1,2])
#按行列获取多个不连续元素，类似于坐标获取
print(a2[[1,2],[3,4]])
#要获取连续的行列元素，比如这里获得第一、二行，第二三列的数
print(a2[1:3,2:4])
#获取某列的数据,注意上下两句的区别，下面返回的是数组第一行的元素，相当于做了一个切片操作，加个逗号就相当于
print(a2[:,1])
print(a2[:1])
#同样的可以对列的数进行设计，可以某几列连续或不连续的进行输出
print(a2[:,[1,3]])


```