 {% include "./Python入门(变量类型).md" %}

# <font size=3>迭代器</font>

<font color=#904060 size=2>
迭代器是一个可以记住遍历的位置的对象.迭代则可以作为访问集合元素的一些方式
</font>

```
list = [1, 2, 3, 4]
it = iter(list) #创建迭代器对象
print(next(it)) #next(iterobj)用于输出迭代器的下一个元素

#使用常规的for遍历迭代器对象
for x in it:
    print(x, end='')
#输出:1 2 3 4
#print()打印的是一行值,末尾会自动增加'\n',使用end=''表示不在末尾加'\n',即表示该行未结束

#使用next()遍历
import sys
while True:
    try:
        print(next(it))
    except StopIteration:
#next(iterobj)一直迭代取出迭代器里的下一个元素,当取到最后一个值之后再打算取值(此时已无值可取)时,会抛出一个StopIteration异常,可使用类似函数定义的方法设置异常发生时的处理方式
        sys.exit()
#输出:
1
2
3
4
```
![](https://note.youdao.com/yws/public/resource/2a8f9c410b7a7248f3d159ff794790f0/xmlnote/a9d0be7d644a1276ac28bfac16cb9041/10160 "")
```
#!/usr/bin/python
#自定义迭代器(斐波那契数列)
#迭代器:任何实现了__iter__和__next__()方法的对象都是迭代器,__iter__返回迭代器自身,而__next__返回迭代器中的下一个值
from itertools import islice
class Fib:
    def __init__(self):
        self.prev = 0
        self.curr = 1
 
    def __iter__(self):
        return self
 
    def __next__(self):
        value = self.curr
        self.curr += self.prev
        self.prev = value
        return value

f = Fib()
print(list(islice(f, 0, 10)))

#输出:[1, 1, 2, 3, 5, 8, 13, 21, 34, 55]
```

# <font size=3>生成器</font>

<font color=#904060 size=2>
生成器是一个返回迭代器的函数,只能用于迭代操作,更简单点理解生成器就是一个迭代器
</font>

```
import sys
from itemtools import islice
def fibonacci(n):
    curr, prev, counter = 0, 1, 0
    while True:
        if (counter > n): 
            return
        yield curr
        prev, curr = curr, curr + prev
#与一般函数不同,生成器函数返回返回值用的是yield而不是return
#在调用生成器运行的过程中,每次遇到yield时函数会暂停并保存当前所有的运行信息,返回yield的值,并在下一次执行next()方法时从当前位置继续运行
        counter++
f = fibonacci(10) # f 是一个迭代器,由生成器函数fibonacci返回yield生成
#f=fiboncci()返回的是一个生成器对象,此时函数体中的代码并不会执行,只有显示或隐示地调用next的时候才会真正执行里面的代码
while True:
    try:
        print (next(f), end=" ")
    except StopIteration:
        sys.exit()
        
#输出:0 1 1 2 3 5 8 13 21 34 55
```
<font color=#606090 size=2>
<ul<li>
容器是一系列元素的集合,str,list,set,dict file,sockets对象都可以看作是容器,容器都可以被迭代(用在for,while等语句中),因此他们也
被称为可迭代对象</li><li>
可迭代对象实现了__iter__方法，该方法可返回一个迭代器对象.</li><li>
迭代器持有一个内部状态的字段，用于记录下次迭代返回值，它实现了__next__和__iter__方法,迭代器不会一次性把所有元素加载到内存,而是需要的时候才生成返回结果</li><li>
生成器是一种特殊的迭代器,它的返回值不是通过return而是用yield,</li></ul>
</font>