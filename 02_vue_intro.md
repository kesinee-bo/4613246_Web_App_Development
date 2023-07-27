## **Vue Intro Project**

**1) สร้างโปรเจ็คใหม่โดยใช้คำสั่ง**
```
npm create vite@latest
```
&nbsp;&nbsp;&nbsp;&nbsp; เลือกโปรเจ็ค vue โดยใช้ JavaScript

**2) สร้าง folder ชื่อว่า images ในกล่อง Public**

**3) โหลดไฟล์ major4.webp และ major4.jpg จาก repository นี้ในกล่อง images ไปไว้ยังกล่อง Public/images ที่สร้างไว้ในข้อ 2**


**4) ใช้ข้อมูลสินค้าตามที่ให้มาดังนี้ ( กำหนดในส่งของ data() )**
```
{
    product: 'หูฟังไร้สาย Marshall Major IV',
    brand: 'Marshall',
    image: './images/major4.webp',
    description: 'หูฟังจาก Marshall ในรุ่น Major IV เป็นหูฟังไร้สายชนิด on ear รุ่นที่ 4 แล้วครับ โดยในรุ่นนี้จะออกแบบให้สวมใส่สบายมากขึ้น พร้อมแบตเตอรี่ที่สามารถใช้งานได้นานสูงสุดถึง 80 ชั่วโมงเลยทีเดียว',
    url: 'https://www.marshallheadphones.com',
    inStock: true,
    inventory: 20,
    details: ['Wired', 'Wireless'],
    variants: [
        {id: 239, color: 'Black', image: './images/major4.webp'},
        {id: 240, color: 'Brown', image: './images/major4.jpg'},
    ],
    cart: 0
}
```

**5) กำหนดส่วน style ดังต่อไปนี้**
```
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
```