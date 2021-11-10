Необходимо реализовать дженерик `TupleToUnion`, который принимает кортеж и возвращает объединение из его значений.

Пример

```ts
type Result = TupleToUnion<[123, '456', true]> // 123 | '456' | true>
```

Решение

```ts
type TupleToUnion<T extends unknown[]> = T[number];
```
