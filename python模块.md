```
#fibo.py
#fibo模块(自定义模块)
# Fibonacci numbers module

def fib(n):
# write Fibonacci series up to n
    a, b = 0, 1
    while b < n:
        print(b, end=' ')
        a, b = b, a+b
        print()
def fib2(n):
# return Fibonacci series up to n     
    result = []
    a, b = 0, 1
    while b < n:
        result.append(b
        a, b = b, a+b
        return result 
```
```python
>>> import fibo
#导入整个模块,通过moduleName.moduleContent访问模块内的函数和变量
>>> fibo.fib(1000)
1 1 2 3 5 8 13 21 34 55 89 144 233 377 610 987
>>> fibo.fib2(100)
[1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89]
>>> fibo.__name__
'fibo'

#将函数句柄引用给一般变量
>>> fib = fibo.fib
>>> fib(500)
1 1 2 3 5 8 13 21 34 55 89 144 233 377
```
```
#从模块内导入特定的函数/变量
#只能使用特定的函数/变量
>>> from fibo import fib, fib2
>>> fib(500)
#直接使用模块内函数,不需要用moduleName.moduleContent
1 1 2 3 5 8 13 21 34 55 89 144 233 377

#导入全部内容
>>> from fibo import *
>>> fib(500)
1 1 2 3 5 8 13 21 34 55 89 144 233 377
```

**\__name__**

<font color=#609090 size=2>
一个模块被另一个程序第一次引入时,其主程序将运行,如果我们想在模块被引入时,模块中的某一程序块不执行,我们可以用__name__属性来使该程序块仅在该模块自身运行时执行(模块自身作为主程序执行和模块被引用到另一个程序中被执行)
</font>

```
#!/usr/bin/python3
# Filename: using_name.py

if __name__ == '__main__':
 print('程序自身在运行')
else:
 print('我来自另一模块')
```

**dir()函数**

<font color=#609090 size=2>
内置的函数dir()可以找到模块内定义的所有名称,以一个字符串列表的形式返回
</font>

```
>>> a = [1, 2, 3, 4, 5]
>>> import fibo
>>> fib = fibo.fib
>>>dir(fibo) ##得到一个当前模块fibo中定义的属性列表
#['__name__', 'fib', 'fib2']
>>> dir()
#如果没有给定参数,那么dir() 函数会罗列出当前主程序中所定义的所有名称
['__builtins__', '__name__', 'a', 'fib', 'fibo', 'sys']
>>> a = 5 # 建立一个新的变量 'a'
>>> dir()
['__builtins__', '__doc__', '__name__', 'a', 'sys']
>>>
>>> del a # 删除变量名a
>>>
>>> dir()
['__builtins__', '__doc__', '__name__', 'sys']
>>>
```
