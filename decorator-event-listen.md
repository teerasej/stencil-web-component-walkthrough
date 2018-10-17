# @Event  และ @Listen

- เราสามารถใช้ `@Event()` กำหนด property เพื่อใช้เป็นชื่อ Event ที่ต้องการได้ 
- เราเรียก event ที่สร้างเองนี้ว่า Custom DOM Event
- การสั่ง dispatch event ทำผ่าน `.emit()` 
- แน่นอนว่าสามารถฝากข้อมูลไปกับ event object ได้ด้วยเช่นกัน `.emit(object)` 

import { Event, EventEmitter } from '@stencil/core';

...
export class TodoList {

  @Event() todoCompleted: EventEmitter;

  todoCompletedHandler(todo: Todo) {
    this.todoCompleted.emit(todo);
  }
}

## @Listen(): การดักรับ Event 

- เราสามารถใช้ `@Listen('event name')` กำหนดให้กับ method ใน Parent Component เพื่อดักรับ Event ที่ emit ออกมาจาก Child component ได้ 

import { Listen } from '@stencil/core';

...
export class TodoApp {

  @Listen('todoCompleted')
  todoCompletedHandler(event: CustomEvent) {
    console.log('Received the custom todoCompleted event: ', event.detail);
  }
}

เรายังสามารถกำหนดชื่อของ Element และ event ที่เกิดแบบเจาะจงได้ด้วย 

import { Listen } from '@stencil/core';

...
export class TodoList {

  @Listen('body:scroll')
  handleScroll(ev) {
    console.log('the body was scrolled', ev);
  }
}

และยังสามารถใช้กับ keyboard event ได้เช่นเดียวกัน 

@Listen('keydown')
handleKeyDown(ev){
  if(ev.keyCode === 40){
    console.log('down arrow pressed')
  }
}

@Listen('keydown.up')
handleUpArrow(ev){
  console.log('will fire when up arrow is pressed');
}

ค่าที่ constant ของ keydown ที่มีให้คือ 

- `.enter`
- `.escape`
- `.space`
- `.tab`
- `.left`
- `.up`
- `.right`
- `.down`

## วิธีใช้ใน JSX 

import { Event, EventEmitter } from '@stencil/core';

...
export class TodoList {

  @Event() todoCompleted: EventEmitter;

  todoCompletedHandler(todo: Todo) {
    this.todoCompleted.emit(todo);
  }
}

<todo-list onTodoCompleted={ev => this.someMethod(ev)}></todo-list>
