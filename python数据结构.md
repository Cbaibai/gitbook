<center><b><font size=5>目 &emsp;录</font></center></b>
<center><table><tr><td width=300px>

[toc]
</td></tr></table></center>
# <font color=#906060 size=3>列表相关函数</font>

<font size=2>
  <table> 
    <tr> 
     <th width=120px align=center>方法</th> 
     <th>描述</th> 
    </tr> 
    <tr> 
     <td align=center>list.append(x)</td> 
     <td>把一个元素添加到列表的结尾,相当于 a[len(a):] = [x]</td> 
    </tr> 
    <tr> 
     <td align=center>list.extend(L)</td> 
     <td>通过添加指定列表的所有元素来扩充列表,相当于 a[len(a):] = L</td> 
    </tr> 
    <tr> 
     <td align=center>list.insert(i, x)</td> 
     <td>在指定位置插入一个元素.第一个参数是准备插入到其前面的那个元素的索引,如a.insert(0, x)会插入到整个列表之前,而a.insert(len(a), x)相当于a.append(x) </td> 
    </tr> 
    <tr> 
     <td align=center>list.remove(x)</td> 
     <td>删除列表中值为x的第一个元素,如果没有这样的元素,则会返回一个错误</td> 
    </tr> 
    <tr> 
     <td align=center>list.pop([i])</td> 
     <td>从列表的指定位置删除元素,并将其返回.如
     果没有指定索引,a.pop()返回最后一个元素.元
     素随即从列表中被删除.(方法中i两边的方括号
     表示这个参数是可选的,而不是要求你输入一对
     方括号,你会经常在Python库参考手册中遇到这样的标记)</td> 
    </tr> 
    <tr> 
     <td align=center>list.clear()</td> 
     <td>移除列表中的所有项,等于del a[:]</td> 
    </tr> 
    <tr> 
     <td align=center>list.index(x)</td> 
     <td>返回列表中第一个值为x的元素的索引,如果没有匹配的元素就会返回一个错误</td> 
    </tr> 
    <tr> 
     <td>list.count(x)</td> 
     <td>返回 x 在列表中出现的次数</td> 
    </tr> 
    <tr> 
     <td align=center>list.sort()</td> 
     <td>对列表中的元素进行排序</td> 
    </tr> 
    <tr> 
     <td align=center>list.reverse()</td> 
     <td>倒排列表中的元素</td> 
    </tr> 
    <tr> 
     <td align=center>list.copy()</td> 
     <td>返回列表的浅复制,等于a[:]</td> 
    </tr> 
  </table>
  </font>

```python
>>> List = [66.25, 333, 333, 1, 1234.5]
>>> print(List.count(333), List.count(66.25), List.count('x'))
2 1 0
>>> List.insert(2, -1)
>>> List.Listppend(333)
>>> List
[66.25, 333, -1, 333, 1, 1234.5, 333]
>>> List.index(333)
1
>>> List.remove(333)
>>> List
[66.25, -1, 333, 1, 1234.5, 333]
>>> List.reverse()
>>> List
[333, 1234.5, 1, 333, -1, 66.25]
>>> List.sort()
>>> List
[-1, 1, 66.25, 333, 333, 1234.5]
```

# <font color=#906060 size=3>把列表当做堆栈使用</font>


```python
>>> stack = [3, 4, 5]
>>> stack.append(6)
>>> stack.append(7)
>>> stack
[3, 4, 5, 6, 7]
>>> stack.pop()
7
>>> stack
[3, 4, 5, 6]
>>> stack.pop()
6
>>> stack.pop()
5
>>> stack
[3, 4]
```


# <font color=#906060 size=3>把列表当做队列使用</font>

```python
>>> from collections import deque
>>> queue = deque(["Eric", "John", "Michael"])
>>> queue.append("Terry")           # Terry arrives
>>> queue.append("Graham")          # Graham arrives
>>> queue.popleft()                 # The first to arrive now leaves
'Eric'
>>> queue.popleft()                 # The second to arrive now leaves
'John'
>>> queue                           # Remaining queue in order of arrival
deque(['Michael', 'Terry', 'Graham'])
```
# <font color=#906060 size=3>把列表当做队列使用</font>

```python
>>> vec = [2, 4, 6]
>>> [3*x for x in vec]
[6, 12, 18]
-----------------------------------------
>>> freshfruit = ['  banana', '  loganberry ', 'passion fruit  ']
>>> [weapon.strip() for weapon in freshfruit]
['banana', 'loganberry', 'passion fruit']
-----------------------------------------
>>> [[x, x**2] for x in vec]
[[2, 4], [4, 16], [6, 36]]
-----------------------------------------
>>> [3*x for x in vec if x > 3]
[12, 18]
>>> [3*x for x in vec if x < 2] [] 
-----------------------------------------
>>> [vec1[i]*vec2[i] for i in range(len(vec1))]
[8, 12, -54]
```

# <font color=#906060 size=3>嵌套列表</font>

```
>>> [[row[i] for row in matrix] for i in range(4)]
[[1, 5, 9], [2, 6, 10], [3, 7, 11], [4, 8, 12]]
```
```
>>> transposed = []
>>> for i in range(4):
...     transposed.append([row[i] for row in matrix])
...
>>> transposed
[[1, 5, 9], [2, 6, 10], [3, 7, 11], [4, 8, 12]]
------------------------------------------
>>> transposed = []
>>> for i in range(4):
...     # the following 3 lines implement the nested listcomp
...     transposed_row = []
...     for row in matrix:
...         transposed_row.append(row[i])
...     transposed.append(transposed_row)
...
>>> transposed
[[1, 5, 9], [2, 6, 10], [3, 7, 11], [4, 8, 12]]
```

# <font color=#906060 size=3>del语句</font>


<font color=#409090 size=2><i>
使用 del 语句可以从一个列表中依索引而不是值来删除一个元素.这与使用pop()返回一个值不同。可以用 del 语句从列表中删除一个切割,或清空整个列表(我们以前介绍的方法是给该切割赋一个空列表)
</i></font>

```
>>> a = [-1, 1, 66.25, 333, 333, 1234.5]
>>> del a[0]
>>> a
[1, 66.25, 333, 333, 1234.5]
>>> del a[2:4]
>>> a
[1, 66.25, 1234.5]
>>> del a[:]
>>> a
[]
```
```
del a
#也可以用 del 直接删除实体变量
```

# <font color=#906060 size=3>元组和序列</font>

```
>>> t = 12345, 54321, 'hello!'
>>> t[0]
12345
>>> t
(12345, 54321, 'hello!')
>>> # Tuples may be nested:
... u = t, (1, 2, 3, 4, 5)
>>> u
((12345, 54321, 'hello!'), (1, 2, 3, 4, 5))
```

# <font color=#906060 size=3>集合</font>

<font color=#409090 size=2><i>
集合是一个无序不重复元素的集,主要功能是关系测试和消除重复元素
</i></font>

```
>>> basket = {'apple', 'orange', 'apple', 'pear', 'orange', 'banana'}
>>> print(basket)                      # show that duplicates have been removed
{'orange', 'banana', 'pear', 'apple'}
>>> 'orange' in basket                 # fast membership testing
True
>>> 'crabgrass' in basket
False

>>> # Demonstrate set operations on unique letters from two words
...
>>> a = set('abracadabra')
>>> b = set('alacazam')
>>> a                                  # unique letters in a
{'a', 'r', 'b', 'c', 'd'}
>>> a - b                              # letters in a but not in b
{'r', 'd', 'b'}
>>> a | b                              # letters in either a or b
{'a', 'c', 'r', 'd', 'b', 'm', 'z', 'l'}
>>> a & b                              # letters in both a and b
{'a', 'c'}
>>> a ^ b                              # letters in a or b but not both
{'r', 'd', 'b', 'm', 'z', 'l'}>>> basket = {'apple', 'orange', 'apple', 'pear', 'orange', 'banana'}
>>> print(basket)                      # show that duplicates have been removed
{'orange', 'banana', 'pear', 'apple'}
>>> 'orange' in basket                 # fast membership testing
True
>>> 'crabgrass' in basket
False

>>> # Demonstrate set operations on unique letters from two words
...
>>> a = set('abracadabra')
>>> b = set('alacazam')
>>> a                                  # unique letters in a
{'a', 'r', 'b', 'c', 'd'}
>>> a - b                              # letters in a but not in b
{'r', 'd', 'b'}
>>> a | b                              # letters in either a or b
{'a', 'c', 'r', 'd', 'b', 'm', 'z', 'l'}
>>> a & b                              # letters in both a and b
{'a', 'c'}
>>> a ^ b                              # letters in a or b but not both
{'r', 'd', 'b', 'm', 'z', 'l'}
```
```
#集合也支持推导式:
>>> a = {x for x in 'abracadabra' if x not in 'abc'}
>>> a
{'r', 'd'}
```

# <font color=#906060 size=3>字典</font>

<font color=#409090 size=2><i>
序列是以连续的整数为索引,与此不同的是,字典以关键字为索引,关键字可以是任意不可变类型,通常是字符串或数值
</i></font>

```
# 直接从键值对元组列表中构建字典
>>> dict([('sape', 4139), ('guido', 4127), ('jack', 4098)])
{'sape': 4139, 'jack': 4098, 'guido': 4127}

#从列表推倒式构建字典
>>> {x: x**2 for x in (2, 4, 6)}
{2: 4, 4: 16, 6: 36}

#使用关键字参数指定键值对
>>> dict(sape=4139, guido=4127, jack=4098)
{'sape': 4139, 'jack': 4098, 'guido': 4127}
```
```
>>> tel = {'jack': 4098, 'sape': 4139}
>>> tel['guido'] = 4127
>>> tel
{'sape': 4139, 'guido': 4127, 'jack': 4098}
>>> tel['jack']
4098
>>> del tel['sape']
>>> tel['irv'] = 4127
>>> tel
{'guido': 4127, 'irv': 4127, 'jack': 4098}
>>> list(tel.keys())
['irv', 'guido', 'jack']
>>> sorted(tel.keys())
['guido', 'irv', 'jack']
>>> 'guido' in tel
True
>>> 'jack' not in tel
False
```

# <font color=#906060 size=3>序列和字典的遍历</font>

```
#在字典中遍历时,关键字和对应的值可以使用items() 方法同时解读出来
>>> knights = {'gallahad': 'the pure', 'robin': 'the brave'}
>>> for k, v in knights.items():
...     print(k, v)
...
gallahad the pure
robin the brave
```
```
#在序列中遍历时,索引位置和对应值可以使用enumerate() 函数同时得到
>>> for i, v in enumerate(['tic', 'tac', 'toe']):
...     print(i, v)
...
0 tic
1 tac
2 toe
```
```
#同时遍历两个或更多的序列,可以使用 zip() 组合
>>> questions = ['name', 'quest', 'favorite color']
>>> answers = ['lancelot', 'the holy grail', 'blue']
>>> for q, a in zip(questions, answers):
...     print('What is your {0}?  It is {1}.'.format(q, a))
...
What is your name?  It is lancelot.
What is your quest?  It is the holy grail.
What is your favorite color?  It is blue.
```
```
#要按顺序遍历一个序列,使用sorted()函数返回一个已排序的序列,并不修改原值
>>> basket = ['apple', 'orange', 'apple', 'pear', 'orange', 'banana']
>>> for f in sorted(set(basket)):
...     print(f)
...
apple
banana
orange
pear
```
```
#要反向遍历一个序列,可以先指定这个序列,然后调用 reversesd() 函数
>>> for i in reversed(range(1, 10, 2)):
...     print(i)
...
9
7
5
3
1
```





