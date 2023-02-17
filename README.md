# python-study-notes
# **第一章 Python入门**

## 00 程序基本格式

1. **缩进**
    每一行的行首是有意义的，不能随意打空格，一般4个空格为一个逻辑分割。

2. **区分大小写**
    在为变量起名字的时候，注意区分大小写，'Aa' 和 'aa' 不是一个东西。

3. **标点符号拥有其含义**

4. **注释**
    有两种形式

    1.  单行注释：\#
    2.  多行注释：\''' 注释内容'''

5. **换行**

    一行写不下可以换行：\

    ```python
    a = [1, 2, 3, 4, 5,\
        6, 7, 8, 9, 10]
    ```

6. **约定俗成的命名规范（选学）**

## 01 栈-堆关系（选学）



## 02 基本用法

### 1. 变量的赋值及删除

```python
# 单一赋值
a = 2022
# 链式赋值
a = b = 1997
# 系列解包赋值
a, b = 2000, 2001
# 复合型赋值
x = [a, b] = [1, 2]
```

```python
# 变量的删除
del a
```

### 2. 常量

Python不支持常量，用命名规范来区分，既取的变量名全为大写或 _ 。

```python
MAX_SPEED = 100
```

### 3. 打印变量的value

```python
print(a)
print(a, b) # 同时一行打印两个值
# 不换行打印,end的defult是'\n'
print(a, end='')
```

### 4. 导入模块

```python
# 直接导入所有
import math
# 导入且改名字
import numpy as np
# 导入母模块中部分的函数
from math import sqrt
from math import * # 也是导入所有函数，但是将来用的时候不用带母模块名称==> sqrt(100) 而不是math.sqrt(100),因为可能会发生名称，尽量不要这么用
```



## 03 数值运算

### 1. 数据类型

1. 整数

    例：1990, 2000, -10

2. 浮点数

    例：3.14, 314e-2

3. 布尔值

    例：False, True（本质上是0, 1）

4. 字符串

    由字符组成："abc", 'hello', "1990"

```python
# 字符串的赋值方式
a = "abc"
b = 'cba'
c = "1990" # 注意这个也是字符串，因为用引号进行赋值了
```

### 2. 数据类型的相互转换

```python
# 变为整数
int(3.14)
int("3")
# 变为浮点数
float(3)
float("3.14")
# 变为字符串
str(3.14)
str(3)
```



### 3. 基本运算符


```python
divmod(13, 3) # 同时得到商和余数
```


### 4. 自运算（增强型赋值）


⚠️运算符中间不能有空格

### 5. 比较运算符





⚠️比较的结果为**真**返回值=True（1），为**假**返回值=False（0）

### 6. 逻辑运算符


### 7. 同一运算符


⚠️ 同一运算符的判断根据为对象地址，效率更高

⚠️ ==判断根据对象值，默认调用对象的\__eq__()

### 8. 时间的表示

时间是从 ***1970年1月1日 00:00:00*** 开始以***毫秒***（1/1000秒）进行计算的。此时间以前为负数。

```python
import time
print(time.time()) #当前时间
```

### 9. 二进制，八进制，十六进制（选学）

***

# **第二章 字符串**

字符串的本质是**字符序列**；

对已有字符串**无法直接进行修改**，只能在内存里创建新的字符串，看似是修改过。

默认为**16位的Unicode编码**

```python
# 字符==>Unicode码
ord('A')
# Unicode码==>字符
chr(66)
```

## 01 字符串的基本

### 1. 创建字符串

```python
# 单行
a = 'hello'
b = 'hello "world"'
c = ''

# 多行
d = '''hello
	world
	love
	you
''' # 双引号同理

# 包含关系
e = 'hello "world"' # hello "world"
```

### 2. 字符串长度

```python
len("nihao") # 5

a = 'love'
len(a) # 4
```

### 3. 字符串的加/拼接与乘

```python
# 加法
a = 'hello '
b = 'world'
a + b # hello world

# 拼接
a = 'abc''def' # abcdef

# 乘法
a = 'love'*3 # lovelovelove
```

⚠️ 加法运算时，两边都必须为字符串，否则抛异常

### 4. 转义字符

用 **\\+特殊字符** 实现一些特别功能


## 02 字符串的切片检索与变更



### 1. 切片

####  1.1 提取单个字符

```python
# 例子
a = 'abcdefghijklmnopqrstuvwxyz'
```

正向搜索：0 ~ len()-1

```python
a[0] # a
a[2] # c
a[len(a)-1] # z 
```

反向搜索：-1 ~ -len()

```python
a[-1] # z
a[-5] # v
a[-len(a)] # a
```

#### 1.2 切片slice操作

格式为：**[起始start:终止end:步长step]**

正向操作：


反向操作：


⚠️ 偏移量不在范围内则会报错

### 2. split() 拆分与join()合并

split() 拆分：基于指定**分隔符**和**拆分数量**拆分字符串，返回字典

```python
a = "one two three four five six"
a.split() # ['one', 'two', 'three', 'four', 'five', 'six']

b = "one+two+three+four+five+six"
b.split("+") # ['one', 'two', 'three', 'four', 'five', 'six']
b.split("+", 2) # ['one', 'two', 'three+four+five+six']

c = 'one\ntwo\nthree' 
c.split("\n") # ['one', 'two', 'three']
```

join() 合并：基于**分隔符**做合并

```python
a = ["apple", "banana", "orange"]
strs = '*'.join(a)
print(strs) # apple*banana*orange
```

⚠️ **join() 与 + 做对比**

使用字符串拼接符+，会生成新的字符串对象，因此**不推荐使用+**来拼接字符串。

推荐使用join 函数，因为join 函数在拼接字符串之前会计算所有字符串的长度，然后逐一拷贝， 仅新建一次对象。

### 3. replace() 替换

```python
a = 'abcccccdef'
a = a.replace('c', '*')
print(a) # ab*****def
```

## 03 format创建字符串

拥有三种格式化字符串创建形式

- "%d" % ()
- str.format()
- f"{}"

### 1. 占位符 %

```python
x1 = 18
print('My age: %d' % (x1)) # My age: 18
```

⚠️ %d 是可以替换的，拥有其含义


### 2. format()

```python
num1 = 20
num2 = 30
print('num1={}, num2={}'.format(num1, num2)) # num1=20, num=30

num1 = 20
num2 = 30
print('num1={0}, num2={1}, num3={1}, num4={0}'.format(num1, num2)) # num1=20, num2=30, num3=30, num4=20

print('{num1} {num2}'.format(num2='world', num1='hello ')) # hello world
```

### 3. f"{}"

```python
name = "小明"
age = 24
print(f'我叫{name}，今年{age}岁了。') # 我叫小明，今年24岁了。

num = 3.141526
print(f'保留两位小数：{num:.2f}') # 保留两位小数：3.14
```

⚠️ 还有很多格式化方案，比如4.6f等等，详情请见官方文档

官网文档：https://docs.python.org/zh-cn/3/library/string.html#format-string-syntax

## 04 字符串进阶(选学)

### 1.  从控制台读取字符串（交互式）

```python
>>> Myname = input("请输入名字：")
请输入名字：Saitama University
>>> Myname
'Saitama University'
```

### 2. 字符串的驻留机制和比较

**字符串驻留**：仅保存一份相同且不可变字符串的方法，不同的值被存放在字符串驻留池中。 Python 支持字符串驻留机制，对于符合标识符规则的字符串（仅包含下划线（_）、字母 和数字）会启用字符串驻留机制驻留机制。

```python
>>> a = "abd_33"
>>> b = "abd_33"
>>> a is b
True

>>> c = "dd#"
>>> d = "dd#"
>>> c is d
False

>>> str1 = "aa"
>>> str2 = "bb"
>>> str1+str2 is "aabb"
False
>>> str1+str2 == "aabb"
True
```

⚠️ ==,!=对字符串进行比较，是否含有相同的字符。

is / not is，比较的是对象的地址，即id(obj1)是 否和id(obj2)相等。

### 3. 其他常用方法

官方文档：https://docs.python.org/zh-cn/3/library/string.html#

------

# **第三章 序列**

**序列**：用于存储一系列数据。

**序列的种类**：

 	1. 列表  [ ]         || 可变   ,   有序
 	2. 元组  ( )         || 不可变  ，  有序
 	3. 字典  { : }       || 可变    ，  无序 （键值对，对应关系）
 	4. 集合  { }         || 可变    ，  无序 （字典的特殊形式，只有键）
 	5. 字符串  ' '      || 整体是一个对象

## 01 列表

列表：可变序列，元素可为不同类型。

```python
a = [10, 20, 'abc', True]
```

### 1. 创建列表

#### 1.1 两种经典的创建方式

```python
# 基本语法[]创建
a = [10, 20, 30, 40]
b = [] # 空的列表

# list()创建
c = list(range(10, 50, 10))
d = list()
e = list("Saitama university")
```

#### 1.2 range() 语句与推导式创建

**range() 语句**可以方便的创建数值序列（range对象），并能够通过list() 语句将其转换为列表。

​									range([start,] end [,step])

start 参数：可选，起始数字，默认为0

end 参数：必选，结尾数字

step 参数：可选，步长，默认为1

```python
# range()创建
list(range(10)) # [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
list(range(10, 50, 10)) # [10, 20, 30, 40]
list(range(3, -10, -1)) # [3, 2, 1, 0, -1, -2, -3, -4, -5, -6, -7, -8, -9]

# 推导式生成列表（for和if循环）
f = [2*x for x in range(5)] # [0, 2, 4, 6, 8]
g = [x*2 for x in range(100) if x%9 == 0] # [0, 18, 36, 54, 72, 90, 108, 126, 144, 162, 180, 198]
```

### 2.  列表元素的追加

**共5种方法**：append() ， +运算符，extend()，insert()，乘法扩展

⚠️ 向中间添加元素效率低，一般在末尾添加元素。

#### 2.1 append() 方法

原地修改列表对象，是真正的列表尾部添加新的元素，**速度最快，推荐使用**。

```python
a = [20, 40]
a.append(80)
print(a) # [20, 40, 80]
```

#### 2.2 +运算符

不是真正的尾部添加元素，而是**创建新的列表对象**；

将原列表的元素和新列表的元素依次复制到新的列表对象中。**涉及大量的复制操作，不建议使用**。

```python
a = [20, 40]
a = a + [50]
print(a) # [20, 40, 50]
```

#### 2.3 insert() 方法

insert()方法可以将指定的元素插入到列表对象的任意制定位置。

使插入位置后面的元素进行移动，**会影响处理速度。涉及大量元素时，尽量避免使用**。

类似发生这种移动的函数还有：remove()、pop()、del()，它们在删除非尾部元素时也会发生操作位置后面元素的移动。

```python
a = [10, 20, 30]
a.insert(2, 100)
print(a) # [10, 20, 100, 30]
```

#### 2.4 乘法扩展

使用乘法扩展列表，**生成一个新列表**，新列表元素时原列表元素的多次重复。

```python
a = ['SU', 100]
b = a*3

print(a) # ['SU', 100]
print(b) # ['SU', 100, 'SU', 100, 'SU', 100]
```

### 3. 列表元素的删除

**共3种方法**：del删除，pop()，remove()

#### 3.1 del 删除

删除列表指定位置元素。

```python
a = [100, 200, 888, 300, 400]
del a[2]
print(a) # [100, 200, 300, 400]
```

#### 3.2 pop() 方法

删除并返回指定位置元素，如果未指定位置则默认操作列表最后一个元素。

```python
>>> a = [10, 20, 88, 30, 40]
>>> a.pop(2)
88
>>> print(a) # [10, 20, 30, 40]
```

#### 3.3 remove() 方法

删除**首次出现**的指定元素，若不存在该元素抛出异常。

```python
a = [1,200,3,4,5,200,3,200,3]
a.remove(200) 
print(a) # [1, 3, 4, 5, 200, 3, 200, 3]
```

### 4. 列表的访问与计数

#### 4.1 直接访问寻找元素

**索引**的区间在 [0, 列表长度-1] 这个范围。超过这个范围则会抛出异常。

```python
>>> a = [10, 20, 30, 40, 50, 20, 30, 20, 30]
>>> a[2]
30
```

#### 4.2 index() 获得索引位置

index()可以获取指定元素首次出现的索引位置。

语法是：index(value,[start,[end]])。其中， start 和end 指定了搜索的范围。

```python
>>> a = [10, 20, 30, 40, 50, 20, 30, 20, 30]
>>> a.index(20)
1
>>> a.index(20, 3) # 从索引位置3 开始往后搜索的第一个20
5
>>> a.index(30, 5, 7) # 从索引位置5 到7 这个区间，第一次出现30 元素的位置
6
```

#### 4.3 count() 获得出现的次数

count() 可以返回指定元素在列表中出现的次数。

```python
>>> a = [10, 20, 30, 40, 50, 20, 30, 20, 30]
>>> a.count(20)
3
```

#### 4.4 len() 返回列表长度

len()返回列表长度，即列表中包含元素的个数。

```python
>>> a = [10, 20, 30]
>>> len(a)
3
```

#### 4.5 成员资格判断

判断列表中是否存在指定的元素，我们可以使用count()方法，返回0 则表示不存在，返回 大于0 则表示存在。

一般我们会使用更加简洁的in 关键字来判断，直接返回True 或False。

```python
>>> a = [10,20,30,40,50,20,30,20,30]
>>> 20 in a
True
>>> 100 not in a
True
>>> 30 not in a
False
```

#### 4.6 极值与和

```python
a = [3, 10, 20, 15, 9]

# 检索最大值
print(max(a)) # 20

# 检索最小值
print(min(a)) # 3

# 求和
print(sum(a)) # 57
```

### 5. 列表的切片

[起始偏移量start:终止偏移量end[:步长step]]

正向操作：


反向操作：


⚠️ 起始偏移量小于0 则会当做0，终止偏移量大于“长度-1”会被当成”长度-1”，不会报错

```api
>>> [10,20,30,40][1:30]
[20, 30, 40]
```

### 6. 列表的遍历

```python
for obj in ListObj:
  print(obj)
```

### 7. 列表的排序

分为**对原列表进行修改**及**创建新列表**两种。

#### 7.1 对原列表进行修改

```python
# 升序
a = [20, 10, 30, 40]
a.sort()
print(a) # [10, 20, 30, 40]

# 降序
b = [20, 10, 30, 40]
b.sort(reverse=True)
print(b) # [40, 30, 20, 10]

# 打乱顺序
c = [10, 20, 30, 40]
import random # 引入random库辅助实现
random.shuffle(c)
print(c) # [10, 30, 20, 40]
```

#### 7.1 创建新列表

```python
#升序
a = [20, 10 ,30, 40]
a = sorted(a)
print(a) # [10, 20, 30, 40]

# 降序
b = [20, 10, 30, 40]
b = sorted(b, reverse=True)
print(b) # [40, 30, 20, 10]

# reversed()返回迭代器
c = [20, 10 ,30, 40]
d = reversed(c)
print(d) # <list_reverseiterator object at 0x7fa10028c340>
print(list(d)) # [40, 30, 10, 20]
print(list(d)) # []

# !!迭代器只能迭代一次，比如打印两次第一次有数值，第二次为空
```

### 8. 多维列表

科学计算一般用numpy array来做，但可以学习一下，其实差不太多。

```python
a = [
  [1, 2, 3, 4, 5],
  [6, 7, 8, 9, 10],
  [11, 12, 13, 14, 15]
]

print(a[2][3]) # 14
```

### 9. 列表的拷贝（选学）

浅拷贝与深拷贝，之后会深讲，

**列表的浅拷贝**只拷贝内存地址，新旧列表的变更为连锁反应。

**列表的深拷贝**则拷贝整个列表对象，新旧列表的变更会分开。

```python
# 浅拷贝
list1 = [30, 40, 50]
list2 = list1

# 深拷贝
list1 = [30, 40, 50]
list2 = [] + list1s
```

## 02 元组

1. **元组为不可变序列**。不能增加，修改，删除元素的相关方法。

2. 访问速度快。

3. 与整数和字符串一样，元组可以作为字典的键，列表则永远不能作为字典的键使用。

### 1. 元组的创建

```python
# 一般创建
a = (10, 20, 30)
b = 10, 20, 30

# 函数创建
c = tuple()
c = tuple(10, 20, 30)
c = tuple('abc') # ('a', 'b', 'c')
c = tuple(range(3))
c = tuple([0, 1, 2])
```

⚠️ 如果创建只有一个元素的元组时，后面一定要带逗号，否则创建的是数字。函数创建则没有这个问题。

```python
a = (10)
print(type(a)) # <class 'int'>

b = (10,)
print(type(b)) # <class 'tuple'>
```

### 2. 元组的访问及计数

```python
# 访问
a = (20, 10, 30, 9, 8)
print(a[0]) # 20
print(a[3]) # 9
print(a[0:2]) # (20, 10)
```

### 3. zip 合并

zip(列表1，列表2，...)将多个列表对应位置的元素组合成为元组，并返回这个zip 对象。在for loop 常用。

```python
a = [10, 20, 30]
b = [40, 50, 60]
c = [70, 80, 90]
d = zip(a, b, c)

print(d) # <zip object at 0x7fc72833b680>
print(list(d)) # [(10, 40, 70), (20, 50, 80), (30, 60, 90)]
print(list(d)) # []
```

⚠️ zip对象为迭代对象，打印第二次为空。

### 4. 生成器推导式创建元组（选学）

```
>>> s = (x*2 for x in range(5))
>>> s
<generator object <genexpr> at 0x0000000002BDEB48>
>>> tuple(s)
(0, 2, 4, 6, 8)
>>> list(s) #只能访问一次元素。第二次就为空了。需要再生成一次
[]
>>> s
<generator object <genexpr> at 0x0000000002BDEB48>
>>> tuple(s)
()
>>> s = (x*2 for x in range(5))
>>> s.__next__()
0
>>> s.__next__()
2
>>> s.__next__()
4
```

## 03 字典

1. 字典是**无序可变序列**，使用键与值来代表对应关系。其中每个元素都是一个“键值对”，包含：“键对象”和“值对象”。

2. 可以通过“键对象”实现快速获取、删除、更新对应的“值对象”。而列表中我们通过“下标数字”找到对应的对象。

​	----**“键”**是任意的不可变数据，比如：整数、浮点数、字符串、元组。｜但是：列表、字典、集合这些可变对象，不能作为“键”。并且“键”不可重复。

​	----**“值”**可以是任意的数据，并且可重复。

### 1. 字典的创建

三种创建方式

```python
# 1. 通过{}、dict()来创建字典对象
a = {'name':'SU', 'age':20, 'job':'student'}
b = dict('name':'SU', 'age':20, 'job':'student')
c = dict([('name', 'age', 'job'), ('SU', 20, 'student')]) # 键和值分开写

# 空字典
d = {}
e = dict()
```

```python
# 2. 通过zip()创建字典对象
keys = ['name', 'age', 'job']
values = ['SU', 20, 'student']
a = dict(zip(keys, values))
print(a) # {'name': 'SU', 'age': 20, 'job': 'student'}
```

```python
# 3. 通过fromkeys 创建值为空的字典
keys = ['name', 'age', 'job']
a = dict.fromkeys(keys)
print(a) # {'name': None, 'age': None, 'job': None}
```

### 2. 字典元素的访问

```python
# 例子
a = {'name':'SU', 'age':20, 'job':'student'}
```

#### 2.1 通过[键] 获得“值”

若键存在返回值。若键不存在，则抛出异常。

```python
a['name'] # 'SU'
a['age'] # 20
a['sex'] # KeyError: 'sex'
```

#### 2.2 通过get()方法获得“值”

推荐使用

优点是：指定键不存在，返回None；也可以设定指定键不存在时默认返回的对象。

```python
a.get('name') # 'SU'

b = a.get('age')
print(b) # 20
```

#### 2.3 列出所有的键值对

```python
a.items() # dict_items([('name', 'SU'), ('age', 20), ('job', 'student')])
```

#### 2.4 分别列出键或者值

```python
a.keys() # dict_keys(['name', 'age', 'job'])
a.values() # dict_values(['SU', 20, 'student'])
```

#### 2.5 len() 获得键值对个数

```python
len(a) # 3
```

#### 2.6 检测一个“键”是否在字典中

```python
'name' in a # True
```



### 3. 字典元素的添加，修改，删除

#### 3.1 新增“键值对”

如果“键”不存在，则新增“键值对”；如果“键”已经存在，则覆盖旧的键值对。

```python
a = {'name':'SU', 'age':20, 'job':'student'}
a['sex'] = 'male'
print(a) # {'name': 'SU', 'age': 20, 'job': 'student', 'sex': 'male'}

b['age'] = 18
print(a) # {'name': 'SU', 'age': 18, 'job': 'student', 'sex': 'male'}
```

#### 3.2 update() 更新字典

使用update()将新字典中所有键值对全部添加到旧字典对象上。如果key 有重复，则直接覆盖。

```python
a = {'name':'SU', 'age':20, 'job':'student'}
b = {'name':'su', 'age':18, 'job':'student', 'sex':'male'}
a.update(b)
print(a) # {'name': 'su', 'age': 18, 'job': 'student', 'sex': 'male'}
```

#### 3.3 字典中元素的删除

​	**del()**方法删除指定键值对；

​	**clear()**删除所有键值对；

​	**pop()**删除指定键值对，并返回对应的“值对象”；

```python
# del()
a = {'name':'SU', 'age':20, 'job':'student'}
del(a['name'])
print(a) # {'age': 20, 'job': 'student'}
```

```python
# clear()
a = {'name':'SU', 'age':20, 'job':'student'}
a.clear()
print(a) # {}
```

```python
# pop()
a = {'name':'SU', 'age':20, 'job':'student'}
b = a.pop('name')
print(a) # {'age': 20, 'job': 'student'}
print(b) # 'SU'
```

#### 3.4 popitem() 随机删除和返回键值对

popitem() 随机弹出项，因为字典是“无序可变序列”，没有第一个元素、最后一个元素的概念。

当想一个接一个地移除并处理项时，这个方法就非常有效（因为不用首先获取键的列表）。

```python
a = {'name':'SU', 'age':20, 'job':'student'}
b = a.popitem()

print(a) # {'name': 'SU', 'age': 20}
print(b) # ('job', 'student')
```

## 04 集合

集合是无序可变，元素不能重复。

实际上，集合底层是字典实现，集合的所有元素都是字典中的“键对象”，因此是不能重复的且唯一的。

### 1. 集合的创建与删除

1. 使用{}创建集合对象，并使用add()方法添加元素

```python
a = {3, 4, 5}
print(type(a)) # <class 'set'>
a.add(6)
print(a) # {3, 4, 5, 6}
```

2. 使用set()，将列表、元组等可迭代对象转成集合。如果原来数据存在重复项，则只保留一个。（创建的一种）

```python
a = ['a', 'b', 'b', 'c']
b = set(a)
print(b) # {'a', 'b', 'c'}
```

3. remove()删除指定元素；clear()清空整个集合

```python
# remove()
a = {10, 20, 30, 40, 50}
a.remove(20)
print(a) # {40, 10, 50, 30}
```

```python
# clear()
a = {10, 20, 30, 40, 50}
a.clear()
print(a) # set()
```

⚠️ {} 默认代表空字典，set() 代表空集合。

### 2. 集合相关操作

和数学中的概念一样，Python 对集合也提供了并集、交集、差集等运算。

```python
a = {10, 20, 'hello', 9.8}
b = {10, 9.8, 'world', 'hello'}

# 交集
c = a&b
print(d) # {9.8, 10, 'hello'}
d = a.intersection(b)
print(d) # {9.8, 10, 'hello'}

# 并集
c = a|b
print(c) # {'world', 'hello', 9.8, 10, 20}
d = a.union(b)
print(d) # {'world', 'hello', 9.8, 10, 20}

# 差集
c = a-b
print(c) # {20}
d = a.difference(b)
print(c) # {20}
```

## 04 序列的进阶（选学）

### 1. 序列的底层逻辑

<img src="/Users/karax/Library/Application Support/typora-user-images/截屏2022-08-24 13.51.55.png" alt="截屏2022-08-24 13.51.55" style="zoom:50%;" />

### 2. 序列解包

序列解包可以用于元组、列表、字典。序列解包可以让我们方便的对多个变量赋值。

```python
# 列表
a, b, c = [10, 20, 30]
print(a) # 10

[a, b, c] = [10, 20, 30]
print(a) # 10
```

```python
# 元组
x, y, z = (20, 30, 40)
print(x) # 20

(a, b, c) = (20, 30, 40)
print(a) # 20
```

```python
# 字典
'''默认对“键”进行操作，也可用keys()；
		对“键值对”操作，则需要使用items()；
		对“值”进行操作，则需要使用values()；
'''

a = {'name':'SU', 'age':20, 'job':'student'}

# 对键
x, y, z = a
print(x, y, z) # name age job
x, y, z = a.keys()
print(x, y, z) # name age job

# 对键值对
x, y, z = a.items()
print(x, y, z) # ('name', 'SU') ('age', 20) ('job', 'student')

# 对值
x, y, z = a.values()
print(x, y, z) # SU 20 student
```

### 3. 字典核心底层原理


#### 3.1 将一个键值对放进字典的底层过程



**扩容：**

python 会根据散列表的拥挤程度扩容。“扩容”指的是:创造更大的数组，将原有内容拷贝到新数组中。

接近2/3 时，数组就会扩容。

#### 3.2 根据键查找“键值对”的底层过程



#### 3.3 字典的底层逻辑总结

1. 键必须可散列

    1. 数字、字符串、元组，都是可散列的

    2. 自定义对象需要支持下面三点：

        ①支持hash()函数

        ②支持通过\__eq__()方法检测相等性

        ③若a==b 为真，则hash(a)==hash(b)也为真

2. 字典在内存中开销巨大，典型的空间换时间

3. 键查询速度很快

4. 往字典里面添加新建可能导致扩容，导致散列表中键的次序变化。因此，不要在遍历字典的同时进行字典的修改
