# Introduction
* iterable
* iterator
* iteration

## 1. Iterable
an iterable is any object in python which has an `__iter__` (python 3+) or a  `__getitem__` (python2.7 still work in python 3+ ) method defined which returns an iterator or can take indexex. In short an `iterable` is any obejct which can provide us with an iterator.
code example:
```
>>> class A:
...         def __getitem__(self, index):
...             if index >= 10:
...                 raise IndexError
...             return index * 111
... 
>>> list(A())
[0, 111, 222, 333, 444, 555, 666, 777, 888, 999]
```

## 2. Iterator 

An iterator is any object in Python which has a `next` (Python2) or `__next__`method defined. That’s it. That’s an iterator. Now let’s understand iteration.

```
class MyNumbers:
  def __iter__(self):
    self.a = 1
    return self

  def __next__(self):
    x = self.a
    if x > 10:
    	raise IndexError
    self.a += 1
    print(x)
    return x

myclass = MyNumbers()
print(list(myclass))
# 1, 2, 3, 4, 5, 6, 7, .. , 10

class MyNumbers:
  def __iter__(self):
    self.a = 1
    return self

  def __next__(self):
    x = self.a
    if x > 10:
    	raise IndexError
    self.a += 1
    #print(self.a)
    return x

myclass = MyNumbers()
myiter = iter(myclass)
print(next(myiter)) # 1
print(next(myiter)) # 2
```

## 3. iteration
In simple words it is the process of taking an item from something e.g a list. When we use a loop to loop over something it is called iteration. It is the name given to the process itself. Now as we have a basic understanding of these terms let’s understand generators.


## 4. generators

Generators are iterators, but you can only iterate over them once. It’s because they do not store all the values in memory, they generate the values on the fly. You use them by iterating over them, either with a ‘for’ loop or by passing them to any function or construct that iterates. Most of the time `generators` are implemented as functions. However, they do not `return` a value, they `yield` it. Here is a simple example of a `generator` function:
```
>>> def generator_func():
...     for i in range(10):
...             yield i
... 
>>> for it in generator_func():
...     print(it)
... 
0
1
2
3
4
5
6
7
8
9
```

reference:
https://book.pythontips.com/en/latest/generators.html
