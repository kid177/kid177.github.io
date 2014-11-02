---
title: "*args和**kwargs"
layout: post
categories: [python, stackoverflow]
tags: [tips,翻译]
published: no
---

StackOverFlow
=============

**地址**:[*args and **kwargs?[duplicate]](http://stackoverflow.com/questions/3394835/args-and-kwargs/3394898#3394898)

----------

其实这只是个语法`*`和`**`,`*args`和`**kwargs`只是一个命名习惯不是要强制使用这两个名字

当你不知道有多少个参数需要传到你的函数中时你可以使用`*args`,也就是说他允许你传递任意个参数.比如:

{%highlight python%}
>>> def print_everything(*args):
        for count, thing in enumerate(args):
...         print '{0}. {1}'.format(count, thing)
...
>>> print_everything('apple', 'banana', 'cabbage')
0. apple
1. banana
2. cabbage
{%endhighlight%}

类似的`**kwargs`允许你去处理之前没有定义过的具名参数:
{%highlight python%}
>>> def table_things(**kwargs):
...     for name, value in kwargs.items():
...         print '{0} = {1}'.format(name, value)
...
>>> table_things(apple = 'fruit', cabbage = 'vegetable')
cabbage = vegetable
apple = fruit
{%endhighlight%}

你也可以和命名参数一起使用.明确的参数会先得到值然后其他值会传递到`*args`和`**kwargs`.命名参数必须放在列表的第一位,例如:
{%highlight python%}
def table_things(titlestring, **kwargs)
{%endhighlight%}

你也可以把两个不定参数放在同一个函数中但是`*args`必须放在`**kwargs`之前

调用函数的时候你也可以使用`*`和`**`语法.例如:
{%highlight python%}
>>> def print_three_things(a, b, c):
...     print 'a = {0}, b = {1}, c = {2}'.format(a,b,c)
...
>>> mylist = ['aardvark', 'baboon', 'cat']
>>> print_three_things(*mylist)
a = aardvark, b = baboon, c = cat
{%endhighlight%}

它取到了列表(元组)中的元素然后和函数中的参数进行匹配.当然,你也可以在函数定义和函数调用时都使用`*`语法.

