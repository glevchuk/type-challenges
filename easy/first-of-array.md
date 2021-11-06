Необходимо реализовать дженерик, который достаёт тип первого элемента в массиве.

Пример

```ts
type arr1 = ['a', 'b', 'c']
type arr2 = [3, 2, 1]

type head1 = First<arr1> // expected to be 'a'
type head2 = First<arr2> // expected to be 3
```

Решения

```ts
type First<T extends any[]> = T extends [infer F, ...any] ? F : never;
```

Нравится больше всего, потому что я только недавно понял смысл `infer` и хочется вставлять его везде.

```ts
type First<T extends any[]> = T['length'] extends 0 ? never : T[0];
```

Нравится меньше, потому что я только недавно понял смысл `infer`.

```ts
type First<T extends any[]> = {
  [P in keyof T as P extends '0' ? P : never]: T[P];
} extends { 0: infer A } ? A : never;
```

Это решение шуточное и я просто пытался написать дикий оверхед, автор не несёт за собой никакой отвественности.
