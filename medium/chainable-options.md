Необходимо реализовать дженерик `ChainableOptions`.

Пример

```ts
declare const config: Chainable

const result = config
  .option('foo', 123)
  .option('name', 'type-challenges')
  .option('bar', { value: 'Hello World' })
  .get()

// expect the type of result to be:
interface Result {
  foo: number
  name: string
  bar: {
    value: string
  }
}
```

Решение

```ts
// Пока не могу придумать, как решить, думаю пойти в эту сторону, но это не точно:
type Chainable<K, V, R> = {
  option(key: K, value: V): Chainable<>
  get(): R
}
```
