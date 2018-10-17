# @State

- กำหนดให้ property 
- ถ้ามีการเปลี่ยนแปลงค่าของ Property จะทำให้เกิดการ `render()`
- ไม่สามารถเปลี่ยนแปลงค่านี้ได้จากภายนอก Component 

```js
export class TodoList {
  @State() completedTodos: Todo[];

  completeTodo(todo: Todo) {
    // This will cause our render function to be called again
    this.completedTodos = [...this.completedTodos, todo];
  }
```
