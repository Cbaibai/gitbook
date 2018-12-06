**函数定义**

```
#语法:
def funcName (argList):
    <statement>
```
```
def area(width, height):
    return width * height
```

**函数变量作用域**

```
a = 4 #全局变量

def print_func1():
    a = 17 #局部变量
    print('a = ', a)
def print_func2():
    print('a = ', a)
print_func1()
print_func2()
print('a = ', a)

#输出:
in print_func a =  17
in print_func a =  4
a =  4
```

**文档字符串**

<font color=#906060 size=2>
如果将一个字符串放在函数的第一行,而没有名称去引用它,python会将它存储在函数中,以便以后可以引用它,这个字符串通常叫做docstring,即documentation string,文档字符串,简单的说就是给函数一个描述说明
</font>

```
#!/usr/bin/python
def add(a,b):  
    """this a function to additon""" #文档字符串  
    sum = a+b  
    return sum

print(add.__doc__) #输出文档字符串

#输出:this a function to additon
```

**按引用传递参数**

```python
#在python中,所有函数都是按引用(指针)传递参数(与C语言中的普通值传递参数不同),在函数内部更改值后会直接影响函数外的值
#coding=utf-8
#!/usr/bin/python
 
def changeme( mylist ):
   "修改传入的列表"
   mylist.append([1,2,3,4]);
   print "函数内取值: ", mylist
   return

mylist = [10,20,30];
changeme( mylist );
print "函数外取值: ", mylist

#函数内取值:  [10, 20, 30, [1, 2, 3, 4]]
#函数外取值:  [10, 20, 30, [1, 2, 3, 4]]
```

**位置/必选参数**

```python
def minus (a, b):
    return a - b
print(minus(3, 2)) #必须按照函数参数列表中形参的位置按顺序传入实参,否则会出现错误
```

**默认值/缺省参数**

```python
def power(x = 2, n):
    if n > 0:
        return x * power(n - 1)
print(power(5))
```

**命名参数**

```
#命名参数表明形参的顺序是可以无关的
def printinfo( name, age ):
   '''打印任何传入的字符串'''
   print "Name: ", name;
   print "Age ", age;
   return;
printinfo(age = 50, name = 'mike')
```

**可变/不定长参数**

<font color=#906060 size=2>
一个最不常用的选择是可以让函数调用可变个数的参数.这些参数被包装进一个元组(查看元组和序列).在这些可变个数的参数之前,可以有零到多个普通的参数
</font>

```python
#一般参数
def calc(numbers):
    sum = 0
    for x in numbers:
        sum += n
    return sum
calc([1, 2, 3]) #list调用
calc((1, 2, 3)) #tuple调用

#可变参数
def calc(*numbers):
    sum = 0
    for n in numbers:
        sum += n
    return sum
calc(1, 2, 3) #传入的多个参数当传给numbers时会被转换为一个tuple,所以可变参数函数体内实际代码和一般参数函数的代码一样
#如果要将list或tuple作为可变参数传给函数,就不能再用calc([1, 2, 3]),要在list或tuple前加上*,即calc(*[1, 2, 3]),表示将序列中的每一个值都做为参数传递给函数,表示num = [1, 2, 3],calc(num[0], calc[1], calc[2])
```

**关键字参数**

<font color=#906060 size=2>
可变参数允许你传入0个或任意个参数,这些可变参数在函数调用时自动组装为一个tuple,而关键字参数允许你传入0个或任意个含参数名的参数,这些关键字参数在函数内部自动组装为一个dict
</font>

```
#关键字参数前可以有多个必选参数
def person(name, age, **kw):
    print('name:', name, 'age:', age, 'other:', kw)

one = person('Michael', 30)
two = person('Bob', 35, city='Beijing')
three = person('Adam', 45, gender='M', job='Engineer')
print(one)
print(two)
print(three)

#输出:
name: Michael age: 30 other: {}
name: Bob age: 35 other: {'city': 'Beijing'}
name: Adam age: 45 other: {'gender': 'M', 'job': 'Engineer'}

#而如果要将一个dict作为关键字参数传入时:
extra = {'city': 'Beijing', 'job': 'Engineer'}
person('Jack', 24, city=extra['city'], job=extra['job'])

#当然了,同将tuple传入可变参数函数中一样,上述写法也可简化为:
person('Jack', 24, **extra)
#将extra中的每一个键值对作为参数传递给函数
```

**#关键字参数的(键)限定(命名关键字参数)**
```python
#对于一般的关键字参数函数,调用者可以传入不受限制的关键字参数,但如果只想要函数接受拥有特定键的键值对作为关键字参数
#只接受键为city,job的键值对
def person(name, age, *, city, job):
    print(name, age, city, job)

print(person('Jack', 24, city='Beijing', job='Engineer'))
#输出:Jack 24 Beijing Engineer
person('Jack', 24, city='Beijing', job) #命名关键字必须传入相应的参数名(就算没有值),否则会报错
#如果函数关键字参数列表中有默认值参数,即person(name, age, *, city = "Beijing", job),可以不传入city
person('Jack', 24, job='Engineer')

person('Jack', 24, 'Beijing', 'Engineer') #会抛出错误
```

**混合参数**

<font color=#906060 size=2>
在Python中的函数,可以用必选参数,默认参数,可变参数,关键字参数和命名关键字参数,这5种参数都可以组合使用(除可变参数无法和命名关键字参数混合外).但要注意的是,参数列表中参数的顺序必须是:必选参数&rarr;默认参数&rarr;可变参数/命名关键字参数&rarr;关键字参数
</font>

```
def f1(a, b, c=0, *args, **kw):
    print('a =', a, 'b =', b, 'c =', c, 'args =', args, 'kw =', kw)

def f2(a, b, c=0, *, d, **kw):
    print('a =', a, 'b =', b, 'c =', c, 'd =', d, 'kw =', kw)

#交互式:
>>> f1(1, 2)
a = 1 b = 2 c = 0 args = () kw = {}
>>> f1(1, 2, c=3)
a = 1 b = 2 c = 3 args = () kw = {}
>>> f1(1, 2, 3, 'a', 'b')
a = 1 b = 2 c = 3 args = ('a', 'b') kw = {}
>>> f1(1, 2, 3, 'a', 'b', x=99)
a = 1 b = 2 c = 3 args = ('a', 'b') kw = {'x': 99}
>>> f2(1, 2, d=99, ext=None)
a = 1 b = 2 c = 0 d = 99 kw = {'ext': None}

#通过tuple或dict,也可以调用上述函数
>>> args = (1, 2, 3, 4)
>>> kw = {'d': 99, 'x': '#'}
>>> f1(*args, **kw)
a = 1 b = 2 c = 3 args = () kw = {'d': 99, 'x': '#'}
>>> args = (1, 2, 3)
>>> kw = {'d': 88, 'x': '#'}
>>> f2(*args, **kw)
a = 1 b = 2 c = 3 d = 88 kw = {'x': '#'}
```

**匿名函数**

<font color=#304899 size=2><i>
python使用lambda来创建匿名函数
</i></font>

<font color=#409090 size=2>
<ul>
<li>lambda只是一个表达式，函数体比def简单很多</li>
<li>lambda的主体是一个表达式,而不是一个代码块,仅仅能在lambda表达式中封装有限的逻辑进去</li>
<li>lambda函数拥有自己的命名空间,且不能访问自有参数列表之外或全局命名空间里的参数</li>
<li>虽然lambda函数看起来只能写一行,却不等同于C或C++的内联函数,后者的目的是调用小函数时不占用栈内存从而增加运行效率</li>
</ul>
</font>

```
语法:
lambda [arg1 [,arg2,.....argn]]:expression
```

```python
#coding=utf-8
#!/usr/bin/python
 
#可写函数说明
sum = lambda arg1, arg2: arg1 + arg2;
 
#调用sum函数
print "Value of total : ", sum( 10, 20 )
print "Value of total : ", sum( 20, 20 )

#输出:
Value of total :  30
Value of total :  40
```