<font color=#906060 size=2>
&emsp;&emsp;即便Python程序的语法是正确的,在运行它的时候,也有可能发生错误,运行期检测到的错误被称为异常.<br/>
&emsp;&emsp;大多数的异常都不会被程序处理,都以错误信息的形式展现出来
</font>

```
 except (RuntimeError, TypeError, NameError):
 #一个except同时处理多个异常
        pass
#多个异常可以放在一个元组里
```

```
import sys

try:
#一个try可以对应多个except子句
    f = open('myfile.txt')
    s = f.readline()
    i = int(s.strip())
except OSError as err:
    print("OS error: {0}".format(err))
except ValueError:
    print("Could not convert data to an integer.")
except:
#未被上述捕获的异常都会在这里被处理,即默认通用的异常处理方式
    print("Unexpected error:", sys.exc_info()[0])
    raise
```

**异常else子句**

```python
import sys

for arg in sys.argv[1:]:
    try:
        f = open(arg, 'r')
    except IOError:
#捕获异常并处理
        print('cannot open', arg)
    else:
#当上述except所述所有异常都未发生时,执行该else语句
        print(arg, 'has', len(f.readlines()), 'lines')
        f.close()
```

**抛出异常**

```python
>>> try:
        raise NameError('HiThere')
#raise(不是throw)唯一的一个参数指定了要被抛出的异常,它必须是一个异常类的实例或直接是异常类(也就是 Exception的子类)
    except NameError:
        print('An exception flew by!')
        raise
#再次抛出异常
   
An exception flew by!
Traceback (most recent call last):
  File "<stdin>", line 2, in ?
NameError: HiThere
```

**自定义异常**

```
>>> class MyError(Exception):
        def __init__(self, value):
            self.value = value
        def __str__(self):
            return repr(self.value)
   
>>> try:
        raise MyError(2*2)
    except MyError as e:
        print('My exception occurred, value:', e.value)
   
My exception occurred, value: 4
>>> raise MyError('oops!')
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
__main__.MyError: 'oops!'
#在这个例子中,类Exception默认的 __init__()被覆盖
```
```
#当创建一个模块有可能抛出多种不同的异常时,一种通常的做法是为这个包建立一个基础异常类,然后基于这个基础类为不同的错误情况创建不同的子类
class Error(Exception):
    """Base class for exceptions in this module."""
    pass

class InputError(Error):
    """Exception raised for errors in the input.

    Attributes:
        expression -- input expression in which the error occurred
        message -- explanation of the error
    """

    def __init__(self, expression, message):
        self.expression = expression
        self.message = message

class TransitionError(Error):
    """Raised when an operation attempts a state transition that's not
    allowed.

    Attributes:
        previous -- state at beginning of transition
        next -- attempted new state
        message -- explanation of why the specific transition is not allowed
    """

    def __init__(self, previous, next, message):
        self.previous = previous
        self.next = next
        self.message = message
#大多数的异常的名字都以"Error"结尾,就跟标准的异常命名一样
```

**定义清理行为**

```
>>> try:
        raise KeyboardInterrupt
    finally:
#无论在任何情况下都会执行finally所指的清理行为(不管try子句里面有没有发生异常,finally子句都会执行)
        print('Goodbye, world!')
   
Goodbye, world!
KeyboardInterrupt
```
```
>>> def divide(x, y):
        try:
            result = x / y
        except ZeroDivisionError:
            print("division by zero!")
        else:
            print("result is", result)
        finally:
            print("executing finally clause")
   
>>> divide(2, 1)
result is 2.0
executing finally clause
>>> divide(2, 0)
division by zero!
executing finally clause
>>> divide("2", "1")
executing finally clause
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
  File "<stdin>", line 3, in divide
TypeError: unsupported operand type(s) for /: 'str' and 'str'
```

**预定义的清理行为**

<font color=#409090 size=2>
一些对象定义了标准的清理行为,无论系统是否成功的使用了它,一旦不需要它了,那么这个标准的清理行为就会执行
</font>

```python
#打开一个文件,然后把内容打印到屏幕上
for line in open("myfile.txt"):
    print(line, end="")
```
```
#就算处理过程中出问题了,文件流f也会正常关闭
with open("myfile.txt") as f:
    for line in f:
        print(line, end="")
```