[toc]

# <font color=#904060 size=3>OS</font>

```
#os模块提供了不少与操作系统相关联的函数
>>> import os
>>> os.getcwd()#返回当前的工作目录
'C:\\Python34'
>>> os.chdir('/server/accesslogs')   # 修改当前的工作目录
>>> os.system('mkdir today')   # 执行系统命令 mkdir 
0
--------------------------
>>> import os
>>> dir(os)
<returns a list of all module functions>
>>> help(os)
<returns an extensive manual page created from the module's docstrings>

#在使用os这样的大型模块时内置的dir()和help()函数非常有用
```

# <font color=#904060 size=3>glob</font>

```
#文件通配符
#glob模块提供了一个函数用于从目录通配符搜索中生成文件列表
>>> import glob
>>> glob.glob('*.py')
['primes.py', 'random.py', 'quote.py']
```

# <font color=#904060 size=3>sys</font>

```
#命令行参数
#通用工具脚本经常调用命令行参数,这些命令行参数以链表形式存储于sys模块的argv变量
>>> import sys
>>> print(sys.argv)
['demo.py', 'one', 'two', 'three']
```
```
#错误输出重定向和程序终止
>>> sys.stderr.write('Warning, log file not found starting a new one\n')
Warning, log file not found starting a new one
#即使在stdout被重定向时,stderr也可以用于显示警告和错误信息
```

# <font color=#904060 size=3>re</font>

```
#re模块为高级字符串处理提供了正则表达式工具
>>> import re
>>> re.findall(r'\bf[a-z]*', 'which foot or hand fell fastest')
['foot', 'fell', 'fastest']
>>> re.sub(r'(\b[a-z]+) \1', r'\1', 'cat in the the hat')
'cat in the hat'

#如果只需要简单的功能,应该首先考虑字符串方法,因为它们非常简单
>>> 'tea for too'.replace('too', 'two')
'tea for two'
```

# <font color=#904060 size=3>math</font>

```python
#math模块为浮点运算提供了对底层C函数库的访问
>>> import math
>>> math.cos(math.pi / 4)
0.70710678118654757
>>> math.log(1024, 2)
10.0

#random提供了生成随机数的工具
>>> import random
>>> random.choice(['apple', 'pear', 'banana'])
'apple'
>>> random.sample(range(100), 10)   # sampling without replacement
[30, 83, 16, 4, 8, 81, 41, 50, 18, 33]
>>> random.random()    # random float
0.17970987693706186
>>> random.randrange(6)    # random integer chosen from range(6)
4
```

# <font color=#904060 size=3>zlib</font>

```
>>> import zlib
>>> s = b'witch which has which witches wrist watch'
>>> len(s)
41
>>> t = zlib.compress(s)
>>> len(t)
37
>>> zlib.decompress(t)
b'witch which has which witches wrist watch'
>>> zlib.crc32(s)
226805979
```

# <font color=#904060 size=3>smtplib</font>

```
#用于发送电子邮件的smtplib
>>> from urllib.request import urlopen
>>> for line in urlopen('http://tycho.usno.navy.mil/cgi-bin/timer.pl'):
...     line = line.decode('utf-8')  # Decoding the binary data to text.
...     if 'EST' in line or 'EDT' in line:  # look for Eastern Time
...         print(line)

<BR>Nov. 25, 09:43:32 PM EST

>>> import smtplib
>>> server = smtplib.SMTP('localhost')
>>> server.sendmail('soothsayer@example.org', 'jcaesar@example.org',
... """To: jcaesar@example.org
... From: soothsayer@example.org
...
... Beware the Ides of March.
... """)
>>> server.quit()
```

# <font color=#904060 size=3>datetime</font>

```python
#datetime模块为日期和时间处理同时提供了简单和复杂的方法
#支持日期和时间算法的同时,实现的重点放在更有效的处理和格式化输出
>>> # dates are easily constructed and formatted
>>> from datetime import date
>>> now = date.today()
>>> now
datetime.date(2003, 12, 2)
>>> now.strftime("%m-%d-%y. %d %b %Y is a %A on the %d day of %B.")
'12-02-03. 02 Dec 2003 is a Tuesday on the 02 day of December.'

>>> # dates support calendar arithmetic
>>> birthday = date(1964, 7, 31)
>>> age = now - birthday
>>> age.days
14368
```