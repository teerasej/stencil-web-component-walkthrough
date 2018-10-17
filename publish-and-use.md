# Publish Web Component 

1. ตั้งค่า `stencil.config.js`

```js
export const config: Config = {
  namespace: 'myname',
  outputTargets: [
    {
      type: 'dist'
    },
    {
      type: 'www'
    }
  ]
  ...
};
```

เพิ่มค่าที่สอดคล้องกันในไฟล์​ `package.json`

- ในค่า **main** ให้เปลี่ยนเป็นชื่อไฟล์ js ที่ตรงกับที่เรา config ไว้ใน namespace ของไฟล์ `stencil.config.js`

```js
{
  "main": "dist/myname.js",
  "types": "dist/types/index.d.ts",
  "collection": "dist/collection/collection-manifest.json",
  "files": [
    "dist/"
  ]
  ...
}
```

3. รันคำสั่ง `npm run build`

## การนำมาใช้ 

### ใช้แบบ Local

1. Copy โฟลเดอร์ `dist` จากโปรเจค web component ไปใส่ในโปรเจคที่ต้องการใช้งาน
2. ใส่ script tag เรียกใช้ไฟล์ JS ของ Web Component

```html
<script src="dist/nextflow-timer.js"></script>
```


### ใช้จาก NPM.js

ใส่ tag script คล้ายๆ กับด้านล่างในไฟล์ `index.html` ที่ได้จาก npm ด้านล่าง

```html
<script src='https://unpkg.com/nextflow-timer@0.0.1/dist/nextflow-timer.js'></script>
```

## ใช้จาก Node Modules

1. รันคำสั่งติดตั้ง package ของเรา `npm install my-name --save`
2. วาง tag ประมาณนี้ในไฟล์ `index.html` 

```html
<script src='node_modules/nextflow-timer/dist/nextflow-timer.js'></script>
```

