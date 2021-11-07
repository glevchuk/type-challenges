Реализовать дженерик `If`, который принимает условие `C`, возвращет истинный `T` или ложный `F` в зависимости от `true`/`false` в `C`.

Пример

```ts
type Result = If<true, 'yeah', 'oh no'> // 'yeah'
```

Решение

```ts
type If<C, T, F> = C extends true ? T : F;
```
