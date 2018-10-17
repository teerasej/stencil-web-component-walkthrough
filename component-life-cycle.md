# Component Lifecycle Methods

- แนะนำให้ trigger `render()` ใน method `componenntWillLoad()` หรือ `componentWillUpdate()` เพราะ 2 method นี้ จะทำงานก่อน `render()` เสมอ
- การทำให้เกิด trigger `render()` ใน `componentDidLoad()` หรือ `componentDidUpdate()` จะทำให้เกิดการ re-render ที่ไม่จำเป็น มีผลต่อประสิทธิภาพโดยรวม
- การอัพเดต state ใน `componentDidUpdate()` สามารถนำไปสู่การติดลูป render ได้ ควรหลีกเลี่ยง 

# ลำดับการ render ของ Parent และ Child component 

จะเริ่ม render จาก parent ไปยัง child และการ render จากเสร็จจาก child ก่อน

<cmp-a>
    <cmp-b>
      <cmp-c></cmp-c>
    </cmp-b>
  </cmp-a>

1. cmp-a - componentWillLoad()
2. cmp-b - componentWillLoad()
3. cmp-c - componentWillLoad()
4. cmp-c - componentDidLoad()
5. cmp-b - componentDidLoad()
6. cmp-a - componentDidLoad()

# Async Lifecycle Methods

- ใน `componentWillLoad()` สามารถสั่ง return promise เพื่อเป็นกลไกที่ทำให้ parent component ไม่เข้าสู่สถานะ **loaded** (นั่นคือยังไม่ render)
- วิธีนี้จะทำให้แน่ใจได้ว่าตัว component ได้ข้อมูลมา render ก่อนที่จะเข้าสู่ `render()`

## ตัวอย่าง

`fetch()` จะคืนค่า promise ทำให้แน่ใจได้ว่ากลไก async จะได้ข้อมูลมาเพื่อใช้ในการ render 

componentWillLoad() {
  return fetch('/some-data.json')
    .then(response => response.json())
    .then(data => {
      this.content = data;
    });
}
