Необходимо реализовать дженерик `Omit` из стандартной библиотеки.

Пример

```ts
interface Todo {
  title: string
  description: string
  completed: boolean
}

type Result = MyOmit<Todo, 'description' | 'title'> // { completed: boolean }
```

Решение

```ts
type MyOmit<T extends Record<string, any>, K extends keyof T> = {
  [P in keyof T as P extends K ? never : P]: T[P]
}
```
