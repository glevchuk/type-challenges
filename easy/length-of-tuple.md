Реализовать дженерик, который будет возврашать длину переданного кортежа.

Пример

```ts
type tesla = ['tesla', 'model 3', 'model X', 'model Y']
type spaceX = ['FALCON 9', 'FALCON HEAVY', 'DRAGON', 'STARSHIP', 'HUMAN SPACEFLIGHT']

type teslaLength = Length<tesla>  // expected 4
type spaceXLength = Length<spaceX> // expected 5
```

Решения

```ts
type Length<T extends { length: number }> = T['length'];
```

```ts
type Length<T extends any> = T extends { length: infer L } ? L : never;
```
