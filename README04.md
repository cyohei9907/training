斐波那契数列练习
```
[0,1]
[0,1,1]
[0,1,1,2]
[0,1,1,2,3]
.....

def fib_iter(n:str)->list[int]:
  if n <= 0:
    return []
  fib = [0,1]
  while len(fib) < n:
    fib.append(fib[-1]+fib[-2])
  return fib[:n]
```
yield是什么意思
```
def method:
  yield 'hello'
r=method()
next(r)
yield是指将当前的值传递给外部,
在某个方法里的话代表着将当前方法解释为生成器函数，在调用之后并不会立即执行
而是通过next(r)来进行调用
```
