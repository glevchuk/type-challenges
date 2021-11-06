Необходимо реализовать дженерик Pick из стандартной библиотеки.

Пример

```ts
interface Todo {
  title: string
  description: string
  completed: boolean
}

type TodoPreview = MyPick<Todo, 'title' | 'completed'>

const todo: TodoPreview = {
    title: 'Clean room',
    completed: false,
}
```

Решения

1. Можно исключить ключ, если условный тип после `as` вернёт `never`.

```ts
type MyPick<T, K> = {
  [P in keyof T as P extends K ? P : never]: T[P]
}
```

2. Можно использовать пересечение типов, тогда останутся только те ключи, которые есть
и в T и в K.

```ts
type MyPick<T, K> = {
  [P in keyof T & K]: T[P]
}
```
