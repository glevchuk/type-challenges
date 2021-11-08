Реализовать дженерик `Unshift`, который в начало массива `T` вставляет `U`.

Пример

```ts
type Result = Unshift<[2, 3], 1> // [1, 2, 3]
```

Решение

```ts
type Unshift<T extends any[], U> = [U, ...T];
```
