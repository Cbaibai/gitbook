**条件控制**

```python
age = int(input("Age of the dog: "))
print()
#if和elif的冒号:后接的是条件满足时应执行的代码块(代码块不用大括号{}表示,而是以缩进表示,每个代码块前的缩进量应是一样的)
#python中没有switch语句
if age < 0:
  print("This can hardly be true!")
elif age == 1:
  print("about 14 human years")
elif age == 2:
  print("about 22 human years")
elif age > 2:
  human = 22 + (age -2)*5

print("Human years: ", human)

input('press Return>')
```

**循环**
+ while循环
```
#语法:
while condition:
    <statements>
```
```
n = 100
sum = 0
counter = 1
while counter <= n:
     sum = sum + counter
     counter += 1

#代码块与非代码块之间最好保持一个空行的间距
print("Sum of 1 until %d: %d" % (n,sum)) 
```

+ for循环

```
for <variable> in <sequence>:
  <statements>
else:
  <statements>
```
```python
lang = ['C', 'C++', 'Perl', 'Python'] 
for x in lang:
    if x == 'Python':
        print('I am learning python')
    print(x)
else:
    print("Finally")
#当循环正常终止(不是break)时,会执行循环后附带的else语句
```
```python
for i in range(5):
    print(i)
#range(n)或range(m,n),range(m,n,step)产生一个等差数组序列

a = ['Mary', 'had', 'little', 'lamb']
for i in range(len(a)):
    print(i,a[i])
#用len()遍历一个序列的索引
```

+ pass

```python
while Ture:
    pass
#pass相当于system('pause'),不进行任何操作
```