Необходимо реализовать дженерик `Parameters` из стандартной библиотеки.

Пример

```ts
const foo = (arg1: string, arg2: number): void => {}

type Result = MyParameters<typeof foo> // [string, number]
```

Решение

```ts
type MyParameters<T extends (...args: any[]) => any> =
  T extends (...args: infer U) => any
    ? U
    : never;
```
