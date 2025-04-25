进行类型判断的时候使用isinstance比较好，比如是继承自某个类型的子类的话也可以进行判断

```
字符串	isinstance(x, str)
整数	isinstance(x, int)
浮点数	isinstance(x, float)
布尔	isinstance(x, bool)
列表	isinstance(x, list)
字典	isinstance(x, dict)
元组	isinstance(x, tuple)
集合	isinstance(x, set)
None	x is None
UUID	isinstance(x, uuid.UUID)
```
进行if判断，这里可以判断内容是否为空，一般可以用not来判断是否为空，但`{}` 的时候需要用==才能判断字典为空
```
name = ""
if not name:

data = []
if not data:

info = {}
if info == {}:
```
这里`&&`判断用`and`，`||`判断用`or`
```
if a > 0 and b < 10:
    print("a 正确并且 b 正确")

if x == 1 or y == 2:
    print("有一个成立就行")
```
三目运算
```
result = "success" if is_success else "failed"
```
判断是否是`None`
```
判断结果是否为None     if result is None:
判断结果是否不为None   if result is not None:
```
判断是否在某个集合中
```
if 'name' in ['name','tel','address']:
if 'name' not in ['name', 'tel', 'address']:
```
`match`操作 如果都不匹配的结果是 `_`
```
match status:
    case 200:
        print("成功")
    case 404:
        print("未找到")
    case _:
        print("其他错误")
```
遍历操作使用for in即可进入迭代循环，在不知道对象原始是否支持迭代的时候
只要先用for item in items进行简单操作后即可知道是否能迭代
后面的或者更适合的方式就和文档相关了
```
遍历字典
    for key,value in users_dict.items()
        print(f'{key}:{value})
遍历列表
    for item in args:
        print(item)
遍历元组
    for item in args:
        print(item)
遍历集合
    for item in item_set:
        print(item)
带index遍历
    for index, fruit in enumerate(fruits):
        print(index, fruit)
固定次数遍历
    for i in rang(5)
        print(i)
```

enumerate是什么
```
enumerate返回一个enum对象，实际上是index 加上 value
for index ,value in enumrate(items):
    print(f'{index}:value')
```
