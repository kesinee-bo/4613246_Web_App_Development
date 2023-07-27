## Vue Intro Project

ข้อมูลสินค้า
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


style
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