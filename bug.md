#   面向对象面向过程
## bug
![](2021-10-22-20-32-52.png)
```python
print(10/0)


#索引从0开始
lst=[1,2,3,4]
print(lst[4])
```
## 类与对象

类是多个类似事物组成的群体统称。
数据类型


```python
class Student:
    native_place='吉林'   #直接写在类的变量，我们称为类属性
    #初始化方法
    def __init__(self,name,age):
        self.name=name   #self.name 为实体属性，进行了一个赋值操作，将局部变量的name值赋给实体属性。
        self.age=age        #比如调用方法的时候可以进行传参。name和age 可以在调用的时候传进来，然后self.name 就接收，然后作为类的局部变量。
    #在创建实例的时候就要对类进行传参，传送的参数要与一开始绑定的相同
    Stu=Student('hallo',20)  #分别对应了初始化方法的name，age。

    #实例方法
    def eat(self):
        print('hallo')    #在类之内定义的函数称为方法，之外叫函数

    #静态方法
    @staticmethod
    def method():  #静态方法没有self
        print('静态方法')
    #类方法
    @classmethod
    def cm(cls):
        print('我是类方法')

print(id(Student))
print(type(Student))
print(Student)


#类方法的第一个参数一定是self，并且类里面方法的互相调用要使用self.

    def add(self):
        print('hh')

    def ss(self):
        self.add()
```

在python里，要想使instance.method()这个格式可以正常工作，在class里面编写method的时候，就必须把变量的第一个位子留出来，用来指代未来call这个method的instance


