# ติดตั้ง Stencil

- ติดตั้ง node.js เวอร์ชั่น 6.0 ขึ้นไป **แบบ LTS**

# สร้างโปรเจค Stencil ใหม่

1. รันคำสั่ง

```bash
npm init stencil
```

2. เลือก `component`

# Component Anatomy 

## Decorator 

```ts
@Component({
  tag: 'my-first-component',
  styleUrl: 'my-first-component.css'
})
```

## Class 

```ts
export class MyComponent {

  // Indicate that name should be a public property on the component
  @Prop() name: string;

  render() {
    return (
      <p>
        My name is {this.name}
      </p>
    );
  }
}
```

## @Prop()

เป็น decorator ที่กำหนดให้กับ property ใน class ได้ 

- ทำให้สามารถกำหนดค่าเป็น attribute ของ component ได้
- การเปลี่ยนแปลงค่า property ของ `@Prop` จะทำให้เกิดการ render ใหม่เสมอ
