# @Props 

- กำหนดค่าที่สามารถเรียกใช้ได้ในรูปแบบของ Attribute นอก component
- เก็บ data type ได้หลายประเภท เช่น `number`, `string`, `boolean`, `Array`, `object`
- `render()` จะถูกเรียกใช้งาน ถ้าค่าของ `@Props` มีการเปลี่ยนแปลง
- **เมื่อค่า `@Prop` ถูกกำหนดแล้ว จะเปลี่ยนแปลงไม่ได้** (ไม่ว่าจะเป็นจากการกำหนดผ่าน attribute หรือการกำหนดจากใน component)

```ts
import { Prop } from '@stencil/core';

...
export class TodoList {
  @Prop() color: string;
  @Prop() favoriteNumber: number;
  @Prop() isSelected: boolean;
  @Prop() myHttpService: MyHttpService;
}
```

### การกำหนดค่า `@Props` ผ่าน HTML และ JSX

ให้สังเกตว่า ถึงแม้ค่า property ที่กำหนด @Props จะเป็นแบบ camel case **แต่ตอนเรียกใช้ใน HTML tag จะเป็นแบบ inline dash**

```html
<todo-list color="blue" favorite-number="24" is-selected="true"><
```

แต่ถ้าเรียกใช้ใน JSX ก็เขียนแบบ camel case ได้นะ ตรงนี้ต้องดูให้ดี 

```html
<todo-list color="blue" favoriteNumber="24" isSelected="true"></todo-list>
```

### การเข้าถึงค่า `@Props` ผ่าน JavaScript  

เราสามารถใช้ JavaScript ทั่วไปในการเข้าถึงค่าต่างๆ ได้

```js
const todoListElement = document.querySelector('todo-list');
console.log(todoListElement.myHttpService); // MyHttpService
console.log(todoListElement.color); // blu
```

### หากต้องการจะกำหนดค่าใหม่ให้ `@Props`

```js
 @Prop({ mutable: true }) name: string = 'Stencil';
```
