# **การติดตั้งโปรแกรมและเครื่องมือต่าง ๆ**
## 1) ติดตั้ง Node.js

https://nodejs.org/en/download/

วิธีการตรวจสอบเวอร์ชันผ่าน command  

```
npm -v
```
หากต้องการใช้ yarn
```
npm install --global yarn
```
วิธีการตรวจสอบเวอร์ชันผ่าน command  
```
yarn --version
```
หากต้องการใช้ yarn

## 2) ติดตั้ง git + สมัคร github

https://git-scm.com/downloads

https://www.github.com

วิธีการตรวจสอบเวอร์ชันผ่าน command  

```
git -v
```

## 3) ติดตั้ง Visual Studio Code

https://code.visualstudio.com/download

การเปิด Visual Studio ใน Directory ปัจจุบัน

```
code .
```

การเปิด Visual Studio ใน Directory ปัจจุบัน และทับโปรเจ็คที่เปิดอยู่

```
code . -r
```

### Extension แนะนำทั่วไป

```
Color Picker by anseki
Color Highlight by sergii n
AutoFileName by jerryHong
Path Intellisense by christian kohler
Rainbow Bracket by 2gua
Path Intellisense by Christian Kohler
Auto Close Tag by Jun Han
Auto Rename Tag by Jun Han
```
### Extension ในการจัดเอกสาร HTML JavaScript CSS
```
Prettier - Code formatter by Prettiter
```
### Extension จำลอง Web Server
```
Live Server by Ritwick Dey
```
### Extension ในการทดสอบ Web API (ลักษณะเดียวกับโปรแกรม Postman)
```
Thunder Client by Ranga Vadhineni
REST Client by Huachao Mao
```
### Extension ช่วยในการบันทึกภาพ Code
```
CodeSnap by adpyke
Polacode by P & P
```
### Extension สำหรับ JavaScript
```
JavaScript (ES6) code snippets by charalampos karypidiss
```
### Extension สำหรับ Vue.js
```
Vue Language Features (Volar) by vue
Vue 3 snippets by hollowtree
Vue VSCode Snippets by arah.drasner
```


## 4) ติดตั้ง MySQL


### MySQL + Workbench


https://dev.mysql.com/downloads/installer/

หรือ

### XAMPP


https://www.apachefriends.org/download.html

## 5) การเก็บงานในรายวิชา
### สร้าง Directory ใน drive D: หากไม่มีสร้างใน C: ได้
```
d:
```
### สร้าง Directory รายวิชา
```
mkdir 4613246_Web_App_Development
```
### ไปยัง Directory เก็บโปรเจ็ครายวิชา
```
cd 4613246_Web_App_Development
```

## 6) การสร้างโปรเจ็กต์ใหม่ Vite + Vue


### **Step 1**: Install Vite in Global

```
npm install -g vite
```

### **Step 2**: Create new Vite Project with Vue

```
npm create vite@latest
```

or

```
yarn create vite
```

### **Step 3**: Install node module in Vite Project

```
npm install
```

or

```
yarn install
```

### **Step 4**: Run Project Vite with Vue

```
npm run dev
```

or

```
yarn dev
```

snippet สำหรับสร้าง component vue ใหม่
```
vbase-3-setup
```

# **Command Lines เบื้องต้น**
### การเปลี่ยน Drive จาก c เป็น d
```
d:
```
ผลที่ได้
```
C:\Users\User>d:
D:\>
```

### การเปลี่ยน Directory
cd ตามด้วย Path จะเปลี่ยน Directory ปัจจุบันไปยัง Path นั้น
```
cd Downloads
```
ผลที่ได้
```
C:\Users\User>cd Downloads
C:\Users\User\Downloads>
```

### **จะย้อน Directory กลับขึ้นไปหนึ่งขั้น**
พิมพ์คำสั่ง cd .. จะย้อน Directory กลับขึ้นไปหนึ่งขั้น
```
cd ..
```
ผลที่ได้
```
C:\Users\User\Downloads>cd ..
C:\Users\User>
```

### **ไปยัง Root Directory**
พิมพ์คำสั่ง cd \ จะไปยัง Root Directory
```
cd \
```
ผลที่ได้
```
C:\Users\User>cd \
C:\>
```

### **สร้าง Directory**
พิมพ์คำสั่ง mkdir myFolder เพื่อสร้าง Directory
```
mkdir myFolder
```
ผลที่ได้ ตรวจสอบโดยใช้คำสั่ง dir จะปรากฎ Directory ที่สร้าง
```
dir
```
อ้างอิง https://medium.com/arcadia-software-development/คำสั่ง-command-line-พื้นฐาน-และตัวอย่างการใช้คำสั่งต่างๆ-871f18f90c82
