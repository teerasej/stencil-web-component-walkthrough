# Decorator 

## @Component

- ตัวกำหนดคุณสมบัติของ Component เช่น ชื่อ tag, ไฟล์ css ที่นำมาใช้

```ts
import { Component } from '@stencil/core';

@Component({
  tag: 'todo-list',
  styleUrl: 'todo-list.css'
})
export class TodoList {
  ...
}
```
