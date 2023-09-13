# **Props and Emit**

### **สร้างโปรเจ็คใหม่**

สร้างโปรเจ็คใหม่โดยใช้คำสั่งดังนี้
```
npm create vite@latest
```

หรือ

```
yarn create vite
```

### สร้างตัวแปร books สำหรับเก็บข้อมูลหนังสือ

[ข้อมูลหนังสือ](03_02_book_data.md)

### สร้างไฟล์ Books.vue ในกล่อง Components

### หน้า App.vue เพิ่ม import book 
```
import Books from './components/Books.vue';
```

เพิ่มให้แสดง Books ใน template
```
<Books/>
```

