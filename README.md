# Python Training

#### MRO是什么
MRO是多继承的时候，如果一个类继承两个类的时候，按照继承顺序进行同名方法的优先级排序 进行的排序方法是C3 线性化算法


#### ``__init__`` 和 ``__new__`` 有什么区别
``__init__`` 是python类中的数值的初始化，也可以在floder下创建 ``__init__.py`` 文件,这样表示当前文件夹是一个可以导入的包


#### ``__all__``和``__init__``一般怎么进行配合
``__all__``可以控制需要导出的方法类，其中``__all__==['method_name_a','method_name_b']``这样可以控制让其只输出两个方法


#### ``**kwargs``和``*args``这两个参数有什么区别
``**kwargs``可以用来接收未定义的key value键值对形式参数 例如: { name1:value1, name2:value2 }
``*args``可以用来接收未定义的元组形式参数 例如: (1,2,3)

#### 装饰器方法怎么使用，有什么作用
```
from functools import wraps

def test(func):
    @wraps(func)
    def wrapper(*args, **kwargs): #在此处可以接收所有的参数，因为有*args, **kwargs
        print("🔸 装饰器开始")     #前置方法操作
        result = func(*args, **kwargs)
        print("🔸 装饰器结束")     #后置方法操作
        return result
    return wrapper
    
@test #在此处是以上定义的test装饰器
def do_somthing(name):
    print(name)
    
do_somthing("hello")
```

#### Django中的同步和异步该怎么执行
以下是同步写法的异步方式，通过async和await配合，结果将在1秒后输出内容
```
import asyncio
async def async_hello(request):
    await asyncio.sleep(1)  # 模拟耗时任务
    return JsonResponse({'message': 'Hello from async view!'})
```
但是Django中的ORM并不会变成异步，这个过程是同步的，这里会出现报错
```
async def view(request):
    user = await User.objects.get(id=1)
```
并发执行的话需要通过``asyncio.create_task(method_name)``来创建新的线程去执行代码
```
import asyncio

async def greet():
    print("Hello")
    await asyncio.sleep(1)
    print("World")

async def main():
    task = asyncio.create_task(greet())
    await task
```
如果在生产环境想进行异步执行的话，可以使用celery
```
# tasks.py
from celery import shared_task
@shared_task
def insert_data(data):
    Record.objects.create(**data)
```

```
# views.py
def sync_view(request):
    insert_data.delay({"name": "Charlie"})  # ✅ 异步提交任务
    return JsonResponse({"msg": "后台已提交，主流程返回"})
```


#### 关于链式调用方法的简要
```
当我想创建一个链式调用的时候，将要创建的内容后面加上一个Builder，例如AccountBuilder，在方法中不断返回this
class AccountBuilder:
    def __init__(self):
        self.acc = ""

    def doSomething1(self):
        self.acc += "Step1 "
        return self  # ✅ 链式调用关键点

    def doSomething2(self):
        self.acc += "Step2 "
        return self

    def getAcc(self):
        return self.acc
```
