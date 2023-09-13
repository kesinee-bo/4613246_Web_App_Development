# **การสร้าง Book Shop API (NodeJs)**

## การติดตั้งโปรแกรมที่จำเป็น

- [MySQL Community](https://dev.mysql.com/downloads/installer/)

- [MySQL Workbench](https://dev.mysql.com/downloads/workbench/)

## การติดตั้ง VsCode Extension

- REST Client
- Thunder Client

## ดาวน์โหลดไฟล์สำหรับโปรเจ็คเริ่มต้น

ทำการดาวน์โหลดไฟล์จากลิงค์ด้านล่างนี้

[Book Shop API (Start files)](https://drive.google.com/file/d/11AnFxvLy0AplIwYMnsUT-I7B6YV4C56u/view?usp=sharing)

หลังจากนั้นทำการ unzip ไฟล์เตรียมไว้ในโฟลเดอร์ที่ต้องการ

## สร้าง Database และ Table สำหรับโปรเจ็ค (BookShopDB)

โดยนำไฟล์ material/bookshoopdbV5.sql ไป Import ใน MySQL Workbench จะทำให้ได้ฐานข้อมูลชื่อว่า BookShopDB พร้อม Table ที่ต้องใช้ในโปรเจ็ค

## สร้างโปรเจ็คใน Vs Code

สร้าง Folder สำหรับโปรนี้ และทำการเปิดโปรเจ็คนี้ใน VsCode หลังจากนั้นจึงรันคำสั่งต่อไปนี้ เพื่อสร้างไฟล์เริ่มต้นของโปรเจ็ค

```
npm init
```

ติดตั้ง pakage ที่ต้องใช้งานทั้งหมด

```
npm install express --save
```

```
npm install express-fileupload --save
```

```
npm install bcryptjs --save
```

```
npm install jsonwebtoken --save
```

```
npm install cors --save
```

```
npm install mysql --save
```

```
npm install dotenv --save
```

```
npm install nodemon --save
```

แก้ไขไฟล์ package.json ในส่วนดังต่อไปนี้ (เพิ่มเติมในการรัน test ด้วย)

```
"scripts": {
    "start": "node index.js",
    "dev": "nodemon index.js",
    "test": "nodemon test.js"
 },
```

และนำไฟล์ที่ upzip ไว้ย้ายมาไว้ในกล่องโปรเจ็ค

กำหนดค่าต่างๆ ในไฟล์ .env ดังนี้ (กำหนด user และ password ของ MySQL ให้ตรงกับที่ใช้งานจริง) ในตัวอย่างนี้ได้ใช้งาน JWT ในการยืนยันตัวตน โดยจะกำหนดค่า secret สำหรับใช้ในการสร้าง token (SECRET="vrcs")

```
SECRET="vrcs"
API_VERSION="/api/v2"
BOOKSHOP_PICTURE_PATH="./book_images/"
MYSQL_USER="root"
MYSQL_PASSWORD="password"
MYSQL_DATABASE="bookshopdb"
MYSQL_HOST="localhost"
```

## สร้างและทดสอบ API (แบบง่าย) ด้วย REST Client และ Thunder Client

โดยในไฟล์ test.js ให้เติมโค้ดในส่วนที่ comment ไว้และทำการทดสอบผ่าน rest client จากไฟล์ test.http

ในการรัน test ให้ใช้คำสั่งดังนี้

```
npm run test
```

### เรียกดูข้อมูลหนังสือทั้งหมด

```
// -------- Get all books
app.get( '/books',  function (req, res)  {

    try
    {

        res.setHeader('Content-Type', 'application/json');
        res.header("Access-Control-Allow-Origin", "*");
        res.header("Access-Control-Allow-Headers", "Origin, X-Requested-With, Content-Type, Accept");


        db.query(
          `
        SELECT
          bookid,title,isbn,pageCount,
          publishedDate,thumbnailUrl,
          shortDescription,authors.name as 'author',
          category,price
        FROM books,authors
        WHERE books.author=authors.authorid`,
          function (error, results, fields) {
            if (error) throw error;
            return res
              .status(200)
              .send({ error: false, message: "books list", data: results });
          }
        );

		} catch {

      return res.status(401).send()

    }



});
```

ทดลองเรียกใช้ API เพื่่อดูข้อมูลหนังสือทั้งหมดได้ผ่านทาง REST Client โดยเพิ่มคำสั่งดังนี้ในไฟล์ test.http

```
### -------- Get All Books
GET http://localhost:3000/books HTTP/1.1
content-type: application/json
```

### เพิ่มข้อมูลหนังสือ

```
// -------- Add new book
app.post( '/books',  function (req, res)  {

  try
  {

    var title = req.body.title;
    var price=req.body.price;
    var isbn = req.body.isbn;
    var pageCount = req.body.pageCount;
    var publishedDate=req.body.publishedDate;
    var thumbnailUrl=req.body.thumbnailUrl;
    var shortDescription=req.body.shortDescription;
    var author=req.body.author;
    var category=req.body.category;


    res.setHeader('Content-Type', 'application/json');
    res.header("Access-Control-Allow-Origin", "*");
    res.header("Access-Control-Allow-Headers", "Origin, X-Requested-With, Content-Type, Accept");

    db.query(`INSERT INTO books
      (title,price, isbn, pageCount, publishedDate, thumbnailUrl,
      shortDescription, author, category)
      VALUES ( '${title}',${price}, '${isbn}', ${pageCount}, '${publishedDate}', '${thumbnailUrl}',
      '${shortDescription}', '${author}', '${category}');`,function (error, results, fields) {
        if (error) throw error;
        return res.send({ error: false, message: 'Insert new book' });
    });


  } catch {

    return res.status(401).send()

  }

});
```

ทดลองเรียกใช้ API เพื่อเพิ่มข้อมูลหนังสือได้ผ่านทาง REST Client โดยเพิ่มคำสั่งดังนี้ในไฟล์ test.http

```
### -------- Create Book
POST http://localhost:3000/books HTTP/1.1
content-type: application/json

{
    "title": "Data Mining",
    "isbn": "1234567890",
    "pageCount": 304,
    "publishedDate": "2023-09-14T00:00:00.000-0700",
    "thumbnailUrl": "https://raw.githubusercontent.com/kesinee-bo/sp01/master/Books/unavailable.jpg",
    "shortDescription": "Greate Book...Highly recommended. -- Choice Magazine",
    "author": "64",
    "category": "Machine Learning",
    "price": 100
}
```

### เรียกดูข้อมูลหนังสือตาม id

```
// -------- Get book by id
app.get('/book/:bookid',  function (req, res)  {

  try
  {


      res.setHeader('Content-Type', 'application/json');
      res.header("Access-Control-Allow-Origin", "*");
      res.header("Access-Control-Allow-Headers", "Origin, X-Requested-With, Content-Type, Accept");

      var bookid = Number(req.params.bookid);

      db.query('SELECT * FROM books where bookid=?', bookid.toString(),function (error, results, fields) {
          if (error) throw error;
          return res.send({ error: false, message: 'book id =' + bookid.toString(), data: results });
      });

    } catch {

      return res.status(401).send()

    }

});

```

ทดลองเรียกใช้ API เพื่อดูข้อมูลหนังสือตาม id ได้ผ่านทาง REST Client โดยเพิ่มคำสั่งดังนี้ในไฟล์ test.http

```
### -------- Get Book by Book Id
GET http://localhost:3000/book/63 HTTP/1.1
content-type: application/application/json
```

### แก้ไขข้อมูลหนังสือตาม id

```

// -------- Edit book by id
app.put( '/books/:bookid',  function (req, res)  {

  try
  {

    var title = req.body.title;
    var price=req.body.price;
    var isbn = req.body.isbn;
    var pageCount = req.body.pageCount;
    var publishedDate=req.body.publishedDate;
    var thumbnailUrl=req.body.thumbnailUrl;
    var shortDescription=req.body.shortDescription;
    var author=req.body.author;
    var category=req.body.category;

    res.setHeader('Content-Type', 'application/json');
    res.header("Access-Control-Allow-Origin", "*");
    res.header("Access-Control-Allow-Headers", "Origin, X-Requested-With, Content-Type, Accept");

    var bookid = Number(req.params.bookid);

    db.query(`UPDATE books
              SET
                    title='${title}',
                    price=${price},
                    isbn= '${isbn}',
                    pageCount=${pageCount},
                    publishedDate='${publishedDate}',
                    thumbnailUrl='${thumbnailUrl}',
                    shortDescription='${shortDescription}',
                    author='${author}',
                    category= '${category}'
              WHERE bookid=?`, bookid,function (error, results, fields) {
        if (error) throw error;
        return res.send({ error: false, message: 'Edit book id =' + bookid.toString(), data: results });
    });


  } catch {

    return res.status(401).send()

  }


});
```

ทดลองเรียกใช้ API เพื่อแก้ไขข้อมูลหนังสือตาม id ได้ผ่านทาง REST Client โดยเพิ่มคำสั่งดังนี้ในไฟล์ test.http

```
### -------- Edit Book
PUT http://localhost:3000/books/63 HTTP/1.1
content-type: application/json

{
    "title": "Data Mining xxxx",
    "isbn": "1234567890",
    "pageCount": 304,
    "publishedDate": "2023-09-14T00:00:00.000-0700",
    "thumbnailUrl": "https://raw.githubusercontent.com/kesinee-bo/sp01/master/Books/unavailable.jpg",
    "shortDescription": "Greate Book...Highly recommended. -- Choice Magazine",
    "author": "64",
    "category": "Machine Learning",
    "price": 100
}
```

### ลบข้อมูลหนังสือตาม id

```
// -------- Delete book by id
app.delete( '/books/:bookid',  function (req, res)  {

  try
  {

    res.setHeader('Content-Type', 'application/json');
    res.header("Access-Control-Allow-Origin", "*");
    res.header("Access-Control-Allow-Headers", "Origin, X-Requested-With, Content-Type, Accept");

    var bookid = Number(req.params.bookid);

    db.query('DELETE FROM books where bookid=?', bookid,function (error, results, fields) {
        if (error) throw error;
        return res.send({ error: false, message: 'Delete book id =' + bookid.toString(), data: results });
    });


  } catch {

    return res.status(401).send()

  }


});
```

ทดลองเรียกใช้ API เพื่อลบข้อมูลหนังสือตาม id ได้ผ่านทาง REST Client โดยเพิ่มคำสั่งดังนี้ในไฟล์ test.http

```
### -------- Delete Book by Book Id
DELETE http://localhost:3000/books/64 HTTP/1
content-type: application/json
```

## สร้าง API โดยมีการกำหนด Route และเรียกใช้ Controller ไฟล์

### การใช้งาน Json Web Token (JWT) 

ในตัวอย่างนี้ได้ใช้งาน JWT ในการยืนยันตัวตน โดยมีการเขียนฟังก์ชันสำหรับลงทะเบียนและการเข้าสู่ระบบ โดยเรียกใช้ผ่าน API (Rest Client ไฟล์ testing/users.http) ดังนี้ 


ลงทะเบียนผู้ใช้งาน

```
### ---- Register ----
POST http://localhost:3000/api/v2/users/auth/register HTTP/1.1
content-type: application/json

{
      "username": "admin1",
      "role": "admin",
      "password": "password"
}
```

เมื่อลงทะเบียนแล้ว จะได้รหัสผู้ใช้งานใหม่ ให้ทดลอง Login ดังนี้
```
### ---- Sign In ----

POST http://localhost:3000/api/v2/users/auth/signin HTTP/1.1
content-type: application/json

{
      "username": "admin1",
      "role": "admin",
      "password": "password"
}
```


ผลลัพธ์ที่ได้จะเป็น Token สำหรับเข้าระบบ ตัวอย่าง Token เช่น
```
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6Im5vbzQiLCJwYXNzd29yZCI6IiQyYSQxMCQuSlk3YlZNbGZrcFhkN21DL0VlQk0uRVdYMXFqZjJoTy5LdE9qaFkvUndSTmUyZE94TWxMYSIsImlhdCI6MTY2NTYzNzE5NX0.0HImJfXnfBeYfIJiojx-OJoTpUBDWaWGdGZ70d9S5sg
```


โดยการเรียก API หลังจาก login จะต้องส่ง Token ไปด้วยเสมอ เช่น
    
```
### -------- Get All Books
GET http://localhost:3000/api/v2/books HTTP/1.1
content-type: application/json
Authorization: bearer yJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6Im5vbzQiLCJwYXNzd29yZCI6IiQyYSQxMCQuSlk3YlZNbGZrcFhkN21DL0VlQk0uRVdYMXFqZjJoTy5LdE9qaFkvUndSTmUyZE94TWxMYSIsImlhdCI6MTY2NTYzNzE5NX0.0HImJfXnfBeYfIJiojx-OJoTpUBDWaWGdGZ70d9S5sg
```

ในบรรทัดสุดท้าย Authorization หลังคำว่า bearer คือ Token ที่ได้จากการ login 


### controllers/booksController.js

นำฟังก์ชันจาก test.js มาเขียนใหม่ในรูปแบบของการประกาศฟังก์ชันแบบ async มาใช้งาน โดยเก็บในตัวแปร และทำการ export ออกไปใช้งาน ดังต่อไปนี้

เรียกดูข้อมูลหนังสือทั้งหมด

```
//-------- Get All Books
const getBooks = async ......
```

เพิ่มข้อมูลหนังสือ

```
//--------  Add new Book
const addBook = async ....
```

เรียกดูข้อมูลหนังสือตาม id

```
//-------- Get Book by Id
const getBookById = async .....
```

แก้ไขข้อมูลหนังสือ

```
//-------- Update Book by Id
const updateBookById = async ....
```

ลบข้อมูลหนังสือ

```
//-------- Delete Book by Id
const deleteBookById = async .....
```

ทำการ export ออกไปใช้งาน เช่น

```
module.exports = {

 //Export function getBooks
 getBooks,

 uploadBookCover,
};
```

### routes/index.js

สร้างเส้นทางในการเรียก API ไปยังส่วนของ books โดยเพิ่มคำสั่งดังนี้

```
app.use(api_version +'/books', require('./books'));
```

### routes/books.js
สร้างเส้นทางในการเรียก API โดยใช้ Express Router โดยเรียกใช้งานฟังก์ชันจาก booksController

เริ่มต้นจากการประกาศเพื่อเรียกใช้ ฟังค์ชันใน booksController ดังต่อไปนี้

```
const booksController = require('../controllers/booksController');

```

กำหนดเส้นทางในการเรียกใช้งานฟังก์ชันใน booksController กับ http method ต่างๆ เช่นการเรียกไปยังฟังก์ชัน getBooks ด้วย http method get จะเป็นดังนี้

```
// -------- Route for Get all books
router.route('/')
   .get(verify,booksController.getBooks)
   //--- Add new book
```

โดยทดสอบการทำงานผ่านทาง REST Client ดังนี้

```
### -------- Get All Books
GET http://localhost:3000/api/v2/books HTTP/1.1
content-type: application/json
Authorization: bearer <<token>>
```

<ins>โจทย์</ins> ให้นักศึกษาทำการเพิ่มการเรียกใช้งานฟังก์ชันสำหรับเพิ่มหนังสือ แก้ไขหนังสือ และลบหนังสือ

สำหรับเส้นทางที่ต้องส่ง parameter เพื่อเรียกใช้ เช่น การเรียกดูข้อมูลหนังสือตาม id จะมีการรับ parameter ชื่อ bookid ดังนี้

```
// -------- Route for Get book by id, Delete book by id and Edit book by id
router.route('/:bookid/')
    .get(verify,booksController.getBookById)
```

โดยทดสอบการทำงานผ่านทาง REST Client ดังนี้ (เรียกดูข้อมูลหนังสือตาม id 12)

```
### -------- Get All Books
GET http://localhost:3000/api/v2/books/12 HTTP/1.1
content-type: application/json
Authorization: bearer <<token>>
```

<ins>โจทย์</ins> ให้นักศึกษาทำการเพิ่มการเรียกใช้งานฟังก์ชันสำหรับแก้ไขหนังสือและลบหนังสือ


## <ins>การบ้าน</ins> สร้าง API สำหรับการเพิ่ม ลบ และแก้ไข ข้อมูลผู้แต่งหนังสือ (Author)


