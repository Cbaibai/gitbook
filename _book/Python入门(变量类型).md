**变量赋值**

<font color=#906040 size=2>
python中的变量不需要声明,变量的赋值即是变量声明和定义的过程
</font>

```python
#-*- coding:UTF-8 -*-
#规定编码为utf-8编码,以显示中文
a = b = c = 1;
#fgg
"""
#三引号用于多行注释
js中也可以这样多变量赋值var a,b,c=1,
或var a=b=c=1,都是可以的,
但不能var a,b,c=1,2,3
"""
a, b, c =1, 2.7, 'john';
#这与matlab中的[y1,y2,...] = deal(x1,x2,...)语句类似
#在python中,'',""都可用于表示字符串
```

**python数据类型**

<font size=2>
虽然python是一门弱类型语言,在赋值定义时变量是不考虑类型的,但同js等其它弱类型语言一样,它的数据在内存中存储也是有数据类型的区别的<br/>
</font>

<font color=#906040 size=2>
<b>python3中共有六个标准的数据类型:</b>
<ul><li>
Number 数值</li><li>
String 字符串</li><li>
List 列表</li><li>
Tuple 元组</li><li>
Sets 集合</li><li>
Dictionary 字典
</li></ul>
</font>

+ 数值 Number

<font color=#909040 size=2>
<i>python支持四种不同的数值类型:</i>

<ul><li>
int 有符号整型</li><li>
float 浮动型</li><li>
bool 布尔型</li><li>
complex 复数
</li></ul>
</font>

```python
a, b, c, d = 10, 5.5, True, 4+3i
print(type(a), type(b), type(c), type(d))
#与python2.x不同,python3.x中的print的参数需要加上括号
#注意:bool值是True和False

#输出:
#<class 'int'> <class 'float'> <class 'bool'> <class 'complex'>
```
```python
#数值运算
5 + 4 #加法,9
4.3 - 2 #减法,2.3
3 * 7 #乘法,21
2 / 4 #除法得浮点数,0.5
2 // 4 #除法得整数,0
17 % 3 #取余,2
2 ** 5 #乘方(2^5),32
7.0 / 2 #不同类型的数混合运算时,会自动将整数转换为浮点数
-------------------
#命令行交互模式下,最后一次运算结果会被保存在内置变量 _ 中
>>>price = 100.50
>>>sum = price ** 2
10100.25
>>>10899.75 + _
11000
```

+ 字符串 String

<font color=#409090 size=2><i>
字符串是由数字,字母和下划线组成的一串字符.<br/>
*注:没有单独的字符类型,长度为1的字符串即为一个字符
</i></font>

<font color=#906090 size=2>
python的字符串数组有两者取值顺序:
<ul><li>
从左往右索引默认从0(第一个字符)开始,最大长度是字符串长度len少1</li><li>
从右往左索引默认从-1(最后一个字符)开始,最大长度为字符串长度</li></ul>
</font>

```python
#####转义字符\#####
str = 'Yes, he doesn\'t'
print(str,type(str),len(s)) #输出:Yes, he doesn't 14
print('C:Users\name')
#输出:C:\Users
#ame
print(r'C:\Users\name') #输出:C:\Users\name
#在字符串前加上r表示输出原始字串,不进行转义
```
```python
#####字符串输出#####
str = 'hello world!'
print(str) #输出完整字符串,等价于print(str[:])或print(str[:i]+str[i:])
print(str[0]) #输出第一个字符
print(str[2:5]) #输出第三个到第五个之间的字符(不包括2,包括3,5)
#冒号(切片)运算符:,'abcd'中的'cd'可表示为[1|...],用切片表示为[1:]
print(str[2:]) #输出第二个字符以后字符子串(不包括2)
print(str[-10:-6])
print(str * 2) #输出字符串两次
print(str + "TEST") #这里的+可以理解为js中的字符连接号+
print(str[2:100]) #返回2以后的子串
print(str[2:1]) #返回一个空字符串''
print(str[-100:]) #返回整个字符串
str = 'abc''123'
#两个紧邻的字面字符串会被自动串联成一个字符串
print(str)


#输出:
 Hello World!
 H
 llo
 llo World!
 love
 Hello World!Hello World!
 Hello World!TEST
 abc123
```
```python
#####定义一个跨越多行的字符串#####
str1 = 'I am \na boy'  #在字符串中嵌套'\n'
str2 = '''I am
a boy'''   #用三引号的断行垂直连接作用
str3 = 'I am \  #用'\'的断行水平拼接作用
a boy'
print(str1)
print(str2)
print(str3)

#输出:
I am
a boy
I am
a boy
I am a boy
```
<font color=#aaa size=1><i>
与C等其他语言不同,python中的字符串是常量,即不可更改,str[0]='f'是错误的(同
C++中的string类型一样,是全局内存区的常量)
</i></font>

+ 列表List

<font color=#409090 size=2>
python中的列表数据类型可以看做是matlab中的元胞数组(里面可以存储不同类型的值),只不过增加了许多新的特性
</font>

```
 #_*_ coding:UTF-8 _*_
 #!/usr/bin/python
 
 list = [ 'abcd', 786 , 2.23, 'john']
 series = list + [True, 'steve'] #列表串联,+为列表连接运算符
 
 print(list) # 输出完整列表
 print(list[0]) # 输出列表的第一个元素,列表索引
 print(list[1:3]) # 输出第二个至第三个的元素,列表切片
 print(list[2:]) # 输出从第三个开始至列表末尾的所有元素
 print(list) * 2 # *指重复操作
 print(series)
 series[0] = 'abc' #更改列表中的元素
 print(series)
 series.append('123') #用列表对象的append方法向列表末尾添加新项
 newList = [series, ['abc', 123]] #嵌套列表
 series[:] = [] #清除列表
 
 #输出:
['abcd', 786, 2.23, 'john']
abcd
[786, 2.23]
[2.23, 'john']
['abcd', 786, 2.23, 'john', 'abcd', 786, 2.23, 'john']
['abcd', 786, 2.23, 'john', True, 'steve']
['abc', 786, 2.23, 'john', True, 'steve']
```
<font color=#aaa size=1><i>
与python字符串不同的是,列表中的元素是可以改变的
</i></font>

+ 元组 Tuple

<font color=#409090 size=2>
Tuple和列表List基本等同,但它不能二次赋值,即它相当于只读的列表List
</font>

```python
#coding:UTF-8
#!/usr/bin/python
 
tuple = ( 'abcd', 786 , 2.23, 'john', 70.2 )
tuple[0] = 'abc' #修改元组元素的操作是非法的

print(tuple[0], tuple[2:5], type(tuple), len(tuple))
tuple = () #空元祖,删除元组

tup1 = (20, ) #只有一个元素的元组需要在后面加上一个逗号
tup2, tup3 = (1, 2, 3),(4, 5, 6)
print(tup1, tup2 + tup3) #元组也支持用+连接,即元组串接
#print(str1, str2, ...)会输出'str1str2...',即print的多个参数间可以自动连接成一个字符串
del tup1 #删除元组(值赋为空只能算是清空变量,只有用del才能从符号表中删除这个变量,使之重新变成未定义)
#可变元组(元组项中包含列表的元组)
itup = ('a', 'b', ['X', 'Y'])
L = itup[2]
L[0] = 'A'
```
<font color=#aaa size=1><i>
string,list和tuple都属于序列(sequence)
</i></font>

+ 集合 Sets

<font color=#409090 size=2>
集合是一个无序不重复元素的集
</font>

```python
Student = {'Tom', 'Jim', 'Mary', 'Tom', 'Rose'}
print(Student) #在集合中重复的元素会被自动滤掉
#输出:{'Jim', 'Jack', 'Mary', 'Rose'}

print('Rose' in Student) #membership testing成员测试
#输出:True

blank = set() 
#set()函数用于创建集合,它会自动滤掉重复值
#创建空集合不能用blank = {},只能用set()

#python集合可以进行数学上的集合运算
a = set('abracadabra')
b = set('alacazam')
print(a)
print(b)
print(a-b) #a,b的差集
print(a | b) #a,b的并集
print(a & b) #a,b的交集
print(a ^ b) #a,b的并集与a,b的交集的差集,即a,b中不同时存在的元素

#输出:
{'r', 'a', 'c', 'd', 'b'}
{'m', 'a', 'z', 'c', 'l'}
{'r', 'd', 'b'}
{'r', 'z', 'a', 'm', 'd', 'b', 'c', 'l'}
{'a', 'c'}
{'r', 'z', 'm', 'd', 'b', 'l'}
```

+ 字典 Dictionaries

<font color=#409090 size=2>
字典是一种映射类型(mapping type),它是一组无序的键值对集(有点类似json)
</font>

```python
dic = {} #创建空字典
tel = {'Jack':1557, 'Tom':1320, 'Rose':1886}

tel['Jack'] #通过key查询
del tel['Rose'] #删除一个键值对
tel['Mary'] = 4127 #添加一个键值对
list(tel.keys()) #keys()为字典对象的内置函数,返回所有由tel中的key组成的list
sorted(tel.keys()) #将字典del按key排序
'Tom' in tel #成员测试

#用dict()从序列(String,List,Tuple)创建字典
dict([('sape', 4139), ('guido', 4127), ('jack', 4098)])
#输出{'jack': 4098, 'sape': 4139, 'guido': 4127}

通过列表推导式来构建字典
{x: x*2 for x in (2,4,6)}
#in()运算符与sql中的in类似,表示一个可选值的集合
#输出:{2: 4, 4: 16, 6: 36}

dict(sape=4139, guido=4127, jack=4098)
#输出:{'jack': 4098, 'sape': 4139, 'guido': 4127}

tel.clear()
del tel
#都可用于删除字典
```

<font color=#aaa size=1><i>
字典的关键字key必须为不可变类型(即不能是list类型和包含可变类型的tuple),且不能重复,{'abc':123,}, {123:456}, {('hbmy'):789}都是可行的,但{['name']:123}就不行
</i></font>
