#### 推导式（lambda表达式）

###### 列表推导式——list

```python
[表达式 for 变量 in 列表] 
[out_exp_res for out_exp in input_list]

# 或

[表达式 for 变量 in 列表 if 条件]
[out_exp_res for out_exp in input_list if condition]

# out_exp_res：列表生成元素表达式，可以是有返回值的函数。
# for out_exp in input_list：迭代 input_list 将 out_exp 传入到 out_exp_res 表达式中。
# if condition：条件语句，可以过滤列表中不符合条件的值。
```

> 过滤掉长度小于或等于3的字符串列表，并将剩下的转换成大写字母：

```python
names = ['Bob','Tom','alice','Jerry','Wendy','Smith']
new_names = [name.upper()for name in names if len(name)>3]
```

> 计算 30 以内可以被 3 整除的整数：

```python
multiples = [i for i in range(30) if i % 3 == 0]
```

###### 字典推导式——dict

```python
{ key_expr: value_expr for value in collection }

# 或
{ key_expr: value_expr for value in collection if condition }
```

> 使用字符串及其长度创建字典：

```python
listdemo = ['Google','Runoob', 'Taobao']
# 将列表中各字符串值为键，各字符串的长度为值，组成键值对
newdict = {key:len(key) for key in listdemo}
>>>
{'Google': 6, 'Runoob': 6, 'Taobao': 6}
```

> 提供三个数字，以三个数字为键，三个数字的平方为值来创建字典：

```python
dic = {x: x**2 for x in (2, 4, 6)}

>>>
{2: 4, 4: 16, 6: 36}
```

###### 集合推导式——set

```python
{ expression for item in Sequence }
或
{ expression for item in Sequence if conditional }
```

> 计算数字 1,2,3 的平方数：

```python
setnew = {i**2 for i in (1,2,3)}
>>>
{1, 4, 9}
```

> 判断不是 abc 的字母并输出：

```python
a = {x for x in 'abracadabra' if x not in 'abc'}
>>>
{'d', 'r'}
```

###### 元组推导式——tuple（生成器表达式）

```python
(expression for item in Sequence )
或
(expression for item in Sequence if conditional )
```

元组推导式是用 **()** 圆括号将各部分括起来，而列表推导式用的是中括号 **[]**

元组推导式返回的结果是一个生成器对象

> 我们可以使用下面的代码生成一个包含数字 1~9 的元组

```python
a = (x for x in range(1,10))

# 返回的是生成器对象
>>> a
<generator object <genexpr> at 0x7faf6ee20a50>  

# 使用 tuple() 函数，可以直接将生成器对象转换成元组
>>> tuple(a)       
(1, 2, 3, 4, 5, 6, 7, 8, 9)
```

#### 迭代器与生成器

##### 迭代器

> 把一个类作为一个迭代器使用需要在类中实现两个方法` __iter__() `与 `__next__() `。
>
> Python 的构造函数为 `__init__()`, 它会在对象初始化的时候执行
>
> `__iter__`方法需要返回对象本身，即：self
>
> `__next__`方法，返回下一个数据，如果没有数据了，则需要抛出一个StopIteration的异常。

```python
# 迭代器类型

class IT(object):
    def __init__(self):
        self.counter = 0
        
    def __iter__(self):
        return self

    def __next__(self):
        self.counter += 1
        if self.counter ==3:
            raise StopIteration()
        return self.counter

# 创建一个迭代器对象
obj1 = IT()

print(next(obj1))

```

迭代器是一个可以记住遍历的位置的对象

迭代器有两个基本的方法：**iter()** 和 **next()**

```python
使用常规for语句进行遍历list=[1,2,3,4]
it = iter(list)    # 创建迭代器对象
print (next(it))   # 输出迭代器的下一个元素
>>> 
1

print (next(it))
>>> 
2

# 使用常规for语句进行遍历
for x in it:
    print (x, end=" ")
    
# 也可以使用 next() 函数
while True:
    try:
        print (next(it))
    except StopIteration:
        sys.exit()
```

###### 创建一个迭代器

把一个类作为一个迭代器使用需要在类中实现两个方法 __iter__() 与 __next__() 。

__iter__() 方法返回一个特殊的迭代器对象， 这个迭代器对象实现了 __next__() 方法并通过 StopIteration 异常标识迭代的完成。

__next__() 方法（Python 2 里是 next()）会返回下一个迭代器对象。

> 创建一个返回数字的迭代器，初始值为 1，逐步递增 1：

```python
class MyNumbers:
  def __iter__(self):
    self.a = 1
    return self
 
  def __next__(self):
    x = self.a
    self.a += 1
    return x
 
myclass = MyNumbers()
myiter = iter(myclass)
 
print(next(myiter))
print(next(myiter))
print(next(myiter))
print(next(myiter))
print(next(myiter))
```

###### StopIteration异常用于标识迭代的完成

> 在 20 次迭代后停止执行

```python
class MyNumbers:
  def __iter__(self):
    self.a = 1
    return self
 
  def __next__(self):
    if self.a <= 20:
      x = self.a
      self.a += 1
      return x
    else:
      raise StopIteration
 
myclass = MyNumbers()
myiter = iter(myclass)
 
for x in myiter:
  print(x)
```

##### 生成器

使用了 **yield** 的函数被称为生成器（generator），**yield** 是一个关键字，用于定义生成器函数

生成器函数是一种特殊的函数，可以在迭代过程中逐步产生值，而不是一次性返回所有结果。

生成器是一个返回迭代器的函数，只能用于迭代操作，更简单点理解生成器就是一个**特殊的迭代器**

> 当生成器函数中使用 **yield** 语句时，函数的执行将会暂停，并将 **yield** 后面的表达式作为当前迭代的值返回。
>
> 然后每次调用生成器的 **next()** 方法或使用 **for** 循环进行迭代时，函数会从上次暂停的地方继续执行，直到再次遇到 **yield** 语句。
>
> 生成器函数可以逐步产生值，而不需要一次性计算并返回所有结果。
>
> 调用一个生成器函数，返回的是一个迭代器对象。

```python
def countdown(n):
    while n > 0:
        yield n
        n -= 1
 
# 创建生成器对象
generator = countdown(5)
 
# 通过迭代生成器获取值
print(next(generator))  # 输出: 5
print(next(generator))  # 输出: 4
print(next(generator))  # 输出: 3
 
# 使用 for 循环迭代生成器，输出剩下的获取剩下的两个倒数值
for value in generator:
    print(value)  # 输出: 2 1
```

生成器函数的优势是它们可以按需生成值，避免一次性生成大量数据并占用大量内存

> 使用 yield 实现斐波那契数列

```python
#!/usr/bin/python3
 
import sys
 
def fibonacci(n): # 生成器函数 - 斐波那契
    a, b, counter = 0, 1, 0
    while True:
        if (counter > n): 
            return
        yield a
        a, b = b, a + b
        counter += 1
f = fibonacci(10) # f 是一个迭代器，由生成器返回生成
 
while True:
    try:
        print (next(f), end=" ")
    except StopIteration:
        sys.exit()
```

#### 函数

函数是组织好的，可重复使用的，用来实现单一，或相关联功能的代码段。

- 函数代码块以 **def** 关键词开头，后接函数标识符名称和圆括号 **()**
- 任何传入参数和自变量必须放在圆括号中间，圆括号之间可以用于定义参数
- 函数的第一行语句可以选择性地使用文档字符串—用于存放函数说明。
- 函数内容以冒号 **:** 起始，并且缩进。
- **return [表达式]** 结束函数，选择性地返回一个值给调用方，不带表达式的 return 相当于返回 None。

![py-tup-10-26-1](F:\GIt\presonalnote\Python\py-tup-10-26-1.png)

###### 语法

```python
def 函数名（参数列表）:
    函数体
```

