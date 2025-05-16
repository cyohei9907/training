TS

## Partial<T> 是什么？
Partial<T> 是 TypeScript 内建的 工具类型（Utility Type） 之一。
它会把泛型参数 T 中 所有属性变成可选 (?)，并保持其余类型信息不变。

## 超好用的值合并写法
```
      const payload = {
        ...(props.record ?? {}), 
        ...form 
      } as Schema.Record.AnalyticTemplate
```
