Реализовать дженерик MyReadonly2, который принимает два аргумента `T` и `K`.

`K` является списком ключей `T`, которые должны стать `readonly`. Когда `K` не передан, то поведение должно быть как у `Readonly` из стандартной библиотеки.

Пример

```ts
interface Todo {
  title: string
  description: string
  completed: boolean
}

const todo: MyReadonly2<Todo, 'title' | 'description'> = {
  title: "Hey",
  description: "foobar",
  completed: false,
}

todo.title = "Hello" // Error: cannot reassign a readonly property
todo.description = "barFoo" // Error: cannot reassign a readonly property
todo.completed = true // OK
```

Решение

```ts
type MyReadonly2<T extends Record<string, any>, K extends keyof T = ""> = {
  readonly [P in keyof T as K extends keyof T
    ? P extends K
      ? P
      : never
    : P]: T[P];
} & {
  [P in keyof T as K extends keyof T
    ? P extends K
      ? never
      : P
    : P extends K
    ? P
    : P]: T[P];
};
```

Первый челлендж, который занял у меня времени больше, чем час и всё это время я думал не в ту сторону.
Проверял всё, кроме способа изложенным [здесь](https://github.com/ghaiklor/type-challenges-solutions/blob/main/ru/medium-readonly-2.md),
хотя он был в моей голове. Но ведь просто проверить как сработает объединение с модификаторами сложнее, чем сидеть несколько часов над задачей, правда?

В общем вроде и решил задачу, но ощущение победы было до тех пор, пока не посмотрел на другие решения.
