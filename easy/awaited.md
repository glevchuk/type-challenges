Реализовать дженерик, который достаёт содержимое дженерика Promise.

Пример

```ts
type PromisedString = Promise<string>

type Unpacked = Awaited<Promise<string>> // string
```

Решение

```ts
type Awaited<T> = T extends Promise<infer U> ? U : never;
```
