### Python Training Day 2


``super(``)有什么作用
``super()`` 是python内部重要的内置方法函数，用来调用父类的方法
例如：
```
class Animals:
  def speak():
    print("hello I'm dog")

class Dog:
  def doSomthing():
    super().speak()
```

如果现在是一个python类，但是我想让他像方法一样调用该怎么做，那就使用 ``__call__``方法来调用吧
```
class File:
  def __call__(**kwargs, *args):
    print f"hello ${args}"
file = File()
file("Alice")
```

关于``__exit__``和``__enter__``的具体用法是在with的时候进行使用的，常用于资源进程开始，资源释放

思考:这里和前面装饰器都能够进行函数包裹操作

```
class MyContext:
  def __enter__(**kwargs, *args):
    print f"hello ${args}，the proccess is started"
  def __exit__(**kwargs, *args):
    print "it's over"

with MyContext() as progress:
  print "in progress"
  
```

关于鸭子类型，众所周知，python可以以func为参数进行调用，那么参数也可以是一个class
这个class中如果有某个实现方法的话，在调用的func中可以直接进行class的方法调用，正常来说必须定义当前class的类型
```
class Person:
  def yelling(self):
    print("human yelling")
class Animals:
  def yelling(self):
    print("Animals yelling")
def doSomthing(things):
  things.yelling()

doSomthing(Person())
doSomthing(Animals())
```

什么是tuple、list、dict、set
```
tuple是不可变序列，用于只读的list
list是可变序列，里面的内容可以被修改
dict是字典，kw形式的结果，感觉内容有点像泛型的Object，或者json
set是无序不重复序列，专门用来去重
```











