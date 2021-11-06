Реализовать дженерик ReadOnly из стандартной библиотеки.

Пример

```ts
interface Todo {
  title: string
  description: string
}

const todo: MyReadonly<Todo> = {
  title: "Hey",
  description: "foobar"
}

todo.title = "Hello" // Error: cannot reassign a readonly property
todo.description = "barFoo" // Error: cannot reassign a readonly property
```

Решения

```ts
type MyReadonly<T> = {
  readonly [P in keyof T]: T[P]
}
```

`+` необязательно указывать, так как если префикс не добавлен, то считается что это `+`.
