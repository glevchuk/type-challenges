Необходимо реализовать дженерик `ReturnType` из стандартной библиотеки.

Пример

```ts
type Result = MyReturnType<() => 123> // 123
```

```ts
type MyReturnType<T extends (...args: any[]) => any> =
  T extends (...args : any[]) => infer U
    ? U
    : never;
```
