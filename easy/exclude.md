Реализовать дженерик Exclude из стандартной библиотеки

Пример

```ts
interface Todo {
  title: string
  description: string
  completed: boolean
}

type TodoPreview = MyExclude<Todo, 'title'>

const todo: TodoPreview = {
  description: 'Close the door'
  completed: false,
}
```

Решение

```ts
type MyExclude<T, U> = T extends U ? never : T;
```
