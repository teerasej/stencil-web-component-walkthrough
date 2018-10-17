# การอัพเดต Immuable data

Immutable data มักจะเกิดจากการกำหนด decorator ดังต่อไปนี้ให้ property:
1. `@Props` (ยกเว้นกำหนด `@Props( mutable: true)`
2. `@State`

จะมีผลทำให้เราไม่สามารถเปลี่ยนแปลงค่าเดิมได้ นอกจากกำหนดค่าใหม่ลงไป

## การอัพเดต Array

- แทนที่จะใช้ `push()` หรือ `unshift()` เพื่อเปลี่ยนแปลงข้อมูลโดยตรง เราใช้ syntax `...` ในการดึงข้อมูลเดิมมาสร้างเป็น array ใหม่

```ts
// our original array
this.items = ['ionic', 'stencil', 'webcomponents'];

// update the array
this.items = [
  ...this.items,
  'awesomeness'
]
```

## การอัพเดต Object

- เราใช้ expand `...` แบบเดียวกกันในการสร้าง object ขึ้นใหม่จาก object ตัวเก่า

```ts
// our original object
let myCoolObject = {first: '1', second: '2'}

// update our object
myCoolObject = { ...myCoolObject, third: '3' }
```
