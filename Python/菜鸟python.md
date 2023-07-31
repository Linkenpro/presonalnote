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