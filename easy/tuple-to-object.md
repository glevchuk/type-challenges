Пример

```ts
const tuple = ['tesla', 'model 3', 'model X', 'model Y'] as const

const result: TupleToObject<typeof tuple> // expected { tesla: 'tesla', 'model 3': 'model 3', 'model X': 'model X', 'model Y': 'model Y'}
```

Решение

```ts
type TupleToObject<T extends readonly any[]> = {
  [P in T[number]]: P
}
```

С помощью `T[number]` мы получаем доступ к каждому литеральному типу в кортеже.
Именно к литеральному, потому что ранее к массиву было применено const assertions.
