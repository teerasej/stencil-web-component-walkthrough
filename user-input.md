# User Input

- Stencil ใช้ [DOM Event แบบ native ทั้งหมด](https://developer.mozilla.org/en-US/docs/Web/Events) 
- สังเกตว่าเราใช้ Arrow function กับ Event 

```ts
export class MyComponent {
  handleClick(event: UIEvent) {
    alert('Received the button click!');
  }

  render() {
    return (
      <button onClick={ (event: UIEvent) => this.handleClick(event)}>Click Me!</button>
    );
  }
}
```

ตัวอย่างการใช้กับ event ชื่อ `onChange`

```ts
export class MyComponent {
  inputChanged(event) {
    console.log('input changed: ', event.target.value);
  }

  render() {
    return (
      <input onChange={(event: UIEvent) => this.inputChanged(event)}>
    );
  }
}
```

