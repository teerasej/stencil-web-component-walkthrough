## @Method

- กำหนดเพื่อทำให้ Method สามารถเรียกใช้จากนอก Component ได้

import { Method } from '@stencil/core';

...
export class TodoList {

  @Method()
  showPrompt() {
    // show a prompt
  }
}

วิธีการเรียกใช้ด้วย JavaScript

const todoListElement = document.querySelector('todo-list');
todoListElement.showPrompt();
