**类定义**

```
#!/usr/bin/python3

#类定义
class people:
    #定义基本属性
    name = ''
    age = 0
    #定义私有属性(有下划线__),私有属性在类外部无法直接进行访问
    __weight = 0
    #定义构造方法(__init__())
    def __init__(self,n,a,w):
#与一般函数定义不同,类方法必须包含参数self,且为第一个参数
        self.name = n
        self.age = a
        self.__weight = w
    def speak(self):
        print("%s 说: 我 %d 岁。" %(self.name,self.age))

# 实例化类var = className()
p = people('W3Cschool',10,30)
p.speak()
#输出:W3Cschool 说: 我 10 岁。
```

**继承**

```
#单继承示例
#DerivedClassName(BaseClassNameList)
class student(people):
    grade = ''
    def __init__(self,n,a,w,g):
        #调用父类的构函
        people.__init__(self,n,a,w)
        self.grade = g
    #覆写父类的方法
    def speak(self):
        print("%s 说: 我 %d 岁了，我在读 %d 年级"%(self.name,self.age,self.grade))



s = student('ken',10,60,3)
s.speak()
#输出:ken 说:我10岁了,我在读 3 年级
```
```
#另一个类，多重继承之前的准备
class speaker():
    topic = ''
    name = ''
    def __init__(self,n,t):
        self.name = n
        self.topic = t
    def speak(self):
        print("我叫 %s，我是一个演说家，我演讲的主题是 %s"%(self.name,self.topic))

#多继承
class sample(speaker,student):
    a =''
    def __init__(self,n,a,w,g,t):
        student.__init__(self,n,a,w,g)
        speaker.__init__(self,n,t)

test = sample("Tim",25,80,4,"Python")
test.speak()   #方法名同，默认调用的是在括号中排前地父类的方法
#输出:我叫Tim,我是一个演说家,我演讲的主题是 Python
```

**方法重写**

```
#!/usr/bin/python3

class Parent:        # 定义父类
   def myMethod(self):
      print ('调用父类方法')

class Child(Parent): #定义子类
   def myMethod(self):
 #在子类中重写从父类中继承的方法
      print ('调用子类方法')

c = Child() # 子类实例
c.myMethod() #子类调用重写方法
```

**类的属性与方法**

<b>类的私有属性</b><br/>
<font color=#609090 size=1>
__private_attrs：两个下划线开头，声明该属性为私有，不能在类地外部被使用或直接访问。在类内部的方法中使用时self.__private_attrs
</font>

<b>类的方法</b><br/>
<font color=#609090 size=1>
在类地内部,使用def关键字可以为类定义一个方法,与一般函数定义不同,类方法必须包含参数self,且为第一个参数
</font>

<b>类的私有方法</b><br/>
<font color=#609090 size=1>
__private_method：两个下划线开头，声明该方法为私有方法，不能在类地外部调用。在类的内部调用 slef.__private_methods
</font>

```
#!/usr/bin/python3

class JustCounter:
    __secretCount = 0  # 私有变量
    publicCount = 0    # 公开变量

    def count(self):
        self.__secretCount += 1
        self.publicCount += 1
        print (self.__secretCount)

counter = JustCounter()
counter.count()
counter.count()
print (counter.publicCount)
print (counter.__secretCount)  # 报错，实例不能访问私有变量

#输出:
1
2
2
Traceback (most recent call last):
  File "test.py", line 16, in <module>
    print (counter.__secretCount)  #这里会报错,实例不能访问私有变量
AttributeError: 'JustCounter' object has no attribute '__secretCount'
```

类的专有方法:<br/>

> + __init__:构造函数,在生成对象时调用
> + __del__:析构函数,释放对象时使用
> + __repr__ :打印,转换
> + __setitem__:按照索引赋值
> + __getitem__:按照索引获取值
> + __cmp__:比较运算
> + __call__:函数调用
> + __add__: 加运算
> + __sub__: 减运算
> + __mul__: 乘运算
> + __div__: 除运算
> + __mod__: 求余运算
> + __pow__: 乘方

**运算符重载**

```
#!/usr/bin/python3

class Vector:
   def __init__(self, a, b):
      self.a = a
      self.b = b

   def __str__(self):
      return 'Vector (%d, %d)' % (self.a, self.b)
   
   def __add__(self,other):
      return Vector(self.a + other.a, self.b + other.b)

v1 = Vector(2,10)
v2 = Vector(5,-2)
print (v1 + v2)

#输出:Vector(7,8)
```