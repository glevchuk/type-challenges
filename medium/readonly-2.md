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
// in progress
```
