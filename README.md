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

