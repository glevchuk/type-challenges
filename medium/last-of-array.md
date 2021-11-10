Необходимо реализовать дженерик `Last` который из кортежа `T` достаёт последний элемент.

Пример

```ts
type arr1 = ['a', 'b', 'c']
type arr2 = [3, 2, 1]

type tail1 = Last<arr1> // 'c'
type tail2 = Last<arr2> // 1
```

Решение

```ts
type Last<T extends any[]> = T extends [...any, infer U] ? U : never;
```
