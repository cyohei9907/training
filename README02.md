### Python Training Day 2


super()有什么作用
super() 是python内部重要的内置方法函数，用来调用父类的方法
例如：
```
class Animals:
  def speak():
    print("hello I'm dog")

class Dog:
  def doSomthing():
    super().speak()
```

