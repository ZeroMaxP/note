## 构造

```python
>>>classmate=['Tony','Jack','Merry'];
classmate[0]==classmate[-n]; #n为list的len
```



### len()可以获取list的长度

```python
>>>len(classmate);
```



### append(childnode)  //在list中追加元素到末尾

```python
>>>classmate.append(childnode);
```



### insert(index,childnode)  //在index位置添加元素

```Python
>>>classmate.insert(index,childnode);
```



### pop(index)  //删除(index)的元素

```python
>>>classmate.pop(); #默认是list的末尾
>>>classmate.pop(index); #删除index
```



### sort()

```python
>>> a = ['c', 'b', 'a']
>>> a.sort()
>>> a
['a', 'b', 'c']
```



### replace(‘old’,‘new’)

```python
>>> a = 'abc'
>>> b = a.replace('a', 'A')  #不改变b本身,只是以返回值形式
>>> b
'Abc'
>>> a
'abc'
```



## tuple

```python
>>> classmates = ('Michael', 'Bob', 'Tracy')
```

现在，classmates这个tuple不能变了，它也没有append()，insert()这样的方法。其他获取元素的方法和list是一样的，你可以正常地使用`classmates[0]`，`classmates[-1]`，但不能赋值成另外的元素。

tuple的陷阱：当你定义一个tuple时，在定义的时候，tuple的元素就必须被确定下来，比如：

```python
>>> t = (1, 2)
>>> t
(1, 2)
```

如果要定义一个空的tuple，可以写成`()`：

```python
>>> t = ()
>>> t
()
```

但是，要定义一个只有1个元素的tuple，如果你这么定义：

```python
>>> t = (1)
>>> t
1
```

定义的不是tuple，是`1`这个数！这是因为括号`()`既可以表示tuple，又可以表示数学公式中的小括号，这就产生了歧义，因此，Python规定，这种情况下，按小括号进行计算，计算结果自然是`1`。

所以，只有1个元素的tuple定义时必须加一个逗号`,`，来消除歧义：

```python
>>> t = (1,)
>>> t
(1,)
```

Python在显示只有1个元素的tuple时，也会加一个逗号`,`，以免你误解成数学计算意义上的括号。

最后来看一个“可变的”tuple：

```python
>>> t = ('a', 'b', ['A', 'B'])
>>> t[2][0] = 'X'
>>> t[2][1] = 'Y'
>>> t
('a', 'b', ['X', 'Y'])
```

