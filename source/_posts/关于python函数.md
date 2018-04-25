---
title: 关于python函数
date: 2017-01-08 11:13:37
tags:
- python
categories:
- python
---
看python时遇见一个函数,是这样的:
```bash
def add(L=[]):  
    L.append('x')  
    return L
add()
add()
add()
```

我发现结果是:['x'], ['x','x'], ['x','x','x']
似乎带有记忆功能.
因为写前端是javascript函数,如果是执行3次同一个函数时,结果应该是一样的,重新了解了一下基础,发现是默认参数的问题,参数从[],变成了[‘x’],因此默认参数必须指向不变对象.
对于这个问题我们可以用None来实现
```bash
def add(L=None):  
    if L is None:    
        L = []  
        L.append('x')  
    return L
```
这样参数指向[],即使多次用add()调用,结果还是['x']
