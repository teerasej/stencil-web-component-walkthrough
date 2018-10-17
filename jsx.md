# JSX 

- JSX สามารถนำมาใช้ได้ใน Stencil

```ts
class MyComponent {
  render() {
    return (
      <div>
        <h1>Hello World</h1>
        <p>This is JSX!</p>
      </div>
    );
  }
}

```

## การ bind ข้อมูลใน JSX

```ts
render() {
  return (
    <div>Hello {this.name}</div>
  )
}
```

## ระบบ Slot

เราสามารถใช้ Tag `<slot/>` เพื่อกำหนดจุดที่ต้องการ render child component ในจุดที่ต้องการได้ 

```ts
render() {
  return (
    <div>
      <h2>A Component</h2>
      <div><slot /></div>
    </div>
  );
}
```

ดังนั้น `<p>Child Element</p>` จะถูกแทนที่ลงไปใน `<slot/>` ของ `<my-component>`

```ts
render(){
  return(
    <my-component>
      <p>Child Element</p>
    </my-component>
  )
}
```

### การตั้งชื่อ Slot 

เราสามารถกำหนด attribute `name` ให้กับ tag `<slot/>` ได้

```ts
// my-component.tsx

render(){
  return [
    <slot name="item-start" />,
    <h1>Here is my main content</h1>,
    <slot name="item-end" />
  ]
}
```

เวลาใช้ ก็สามารถกำหนดชื่อ slot ให้ tag HTML เช่นเดียวกัน

```ts
render(){
  return(
    <my-component>
      <p slot="item-start">I'll be placed before the h1</p>
      <p slot="item-end">I'll be placed after the h1</p>
    </my-component>
  )
}
```

## Loop 

เราสามารถใช้ loop ของ JSX ในการวนลูปแสดง JSX ที่ต้องการ รวมถึงการใช้ Data Bindinng ได้

```ts
render() {
  return (
    <div>
      {this.todos.map((todo) =>
        <div>
          <div>{todo.taskName}</div>
          <div>{todo.isCompleted}</div>
        </div>
      )}
    </div>
  )
}
```
