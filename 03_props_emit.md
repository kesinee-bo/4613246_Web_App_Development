# **Props and Emit**

## **สร้างโปรเจ็คใหม่**
สร้างโปรเจ็คใหม่โดยใช้คำสั่งดังนี้
```
npm create vite@latest
```

หรือ

```
yarn create vite
```

ข้อมูลหนังสือ
```
{
    "bookid": 0,
    "title": "Zend Framework in Action",
    "price": 100,
    "isbn": "1933988320",
    "pageCount": 432,
    "publishedDate": "2008-12-01T00:00:00.000-0800",
    "thumbnailUrl": "https://s3.amazonaws.com/AKIAJC5RLADLUMVRPFDQ.book-thumb-images/allen.jpg",
    "shortDescription": "Zend Framework in Action is a comprehensive tutorial that shows how to use the Zend Framework to create web-based applications and web services. This book takes you on an over-the-shoulder tour of the components of the Zend Framework as you build a high quality, real-world web application.",
    "author": "Rob Allen",
    "category": "Web Development"
},
{
    "bookid": 1,
    "title": "Flex on Java",
    "price": 111,
    "isbn": "1933988797",
    "pageCount": 265,
    "publishedDate": "2010-10-15T00:00:00.000-0700",
    "thumbnailUrl": "https://s3.amazonaws.com/AKIAJC5RLADLUMVRPFDQ.book-thumb-images/allmon.jpg",
    "shortDescription": "   A beautifully written book that is a must have for every Java Developer.       Ashish Kulkarni, Technical Director, E-Business Software Solutions Ltd.",
    "author": "Bernerd Allmon",
    "category": "Internet"
},
{
    "bookid": 2,
    "title": "Explorer's Guide to the Semantic Web",
    "price": 222,
    "isbn": "1932394206",
    "pageCount": 304,
    "publishedDate": "2004-06-01T00:00:00.000-0700",
    "thumbnailUrl": "https://s3.amazonaws.com/AKIAJC5RLADLUMVRPFDQ.book-thumb-images/passin.jpg",
    "shortDescription": "\"A thorough look at one vision of the Web's future ...particularly well written...Highly recommended.\" -- Choice Magazine",
    "author": "Thomas B. Passin",
    "category": "Internet"
},
{
    "bookid": 3,
    "title": "Magical A-Life Avatars",
    "price": 333,
    "isbn": "1884777589",
    "pageCount": 450,
    "publishedDate": "2000-12-01T00:00:00.000-0800",
    "thumbnailUrl": "https://s3.amazonaws.com/AKIAJC5RLADLUMVRPFDQ.book-thumb-images/small.jpg",
    "shortDescription": "\"Distinctive book explaining how to get intelligent software agents to work.\" --Clipcode.com",
    "author": "Peter Small",
    "category": "Internet"
},
{
    "bookid": 4,
    "title": "Hello! Flex 4",
    "price": 444,
    "isbn": "1933988762",
    "pageCount": 258,
    "publishedDate": "2009-11-01T00:00:00.000-0700",
    "thumbnailUrl": "https://s3.amazonaws.com/AKIAJC5RLADLUMVRPFDQ.book-thumb-images/armstrong3.jpg",
    "shortDescription": "Hello! Flex 4 progresses through 26 self-contained examples selected so you can progressively master Flex. They vary from small one-page apps, to a 3D rotating haiku, to a Connect Four-like game. And in the last chapter you'll learn to build a full Flex application called SocialStalkr   a mashup that lets you follow your friends by showing their tweets on a Yahoo map.",
    "author": "Peter Armstrong",
    "category": "Internet"
},
{
    "bookid": 5,
    "title": "Internet BBSs",
    "price": 555,
    "isbn": "132869985",
    "pageCount": 400,
    "publishedDate": "1996-10-01T00:00:00.000-0700",
    "thumbnailUrl": "https://s3.amazonaws.com/AKIAJC5RLADLUMVRPFDQ.book-thumb-images/mark.jpg",
    "shortDescription": "Internet BBSs: A Guided Tour provides in-depth coverage of the new world of true BBSs now available world-wide. It is a valuable resource for anyone currently using the Internet.",
    "author": "Richard Scott Mark",
    "category": "Internet"
},
{
    "bookid": 6,
    "title": "Mobile Agents",
    "price": 666,
    "isbn": "1884777368",
    "pageCount": 320,
    "publishedDate": "1997-03-01T00:00:00.000-0800",
    "thumbnailUrl": "https://s3.amazonaws.com/AKIAJC5RLADLUMVRPFDQ.book-thumb-images/cockayne.jpg",
    "shortDescription": "Mobile Agents is the first book to give the reader the ability to create and use powerful mobile agents on the Internet.",
    "author": "William R. Cockayne and Michael Zyda",
    "category": "Internet"
},
{
    "bookid": 7,
    "title": "OSGi in Action",
    "price": 777,
    "isbn": "1933988916",
    "pageCount": 576,
    "publishedDate": "2011-04-06T00:00:00.000-0700",
    "thumbnailUrl": "https://s3.amazonaws.com/AKIAJC5RLADLUMVRPFDQ.book-thumb-images/hall.jpg",
    "shortDescription": "OSGi in Action is a comprehensive guide to OSGi with two primary goals. First, it provides a clear introduction to OSGi concepts with examples that are relevant both for architects and developers. The central idea of OSGi is modularity, so you start by learning about OSGi bundles. You'll then see how OSGi handles module lifecycles and follow up with how it promotes service-oriented interaction among application components.",
    "author": "Richard S. Hall",
    "category": "Internet"
},
{
    "bookid": 8,
    "title": "PostGIS in Action",
    "price": 888,
    "isbn": "1935182269",
    "pageCount": 325,
    "publishedDate": "2011-04-11T00:00:00.000-0700",
    "thumbnailUrl": "https://s3.amazonaws.com/AKIAJC5RLADLUMVRPFDQ.book-thumb-images/obe.jpg",
    "shortDescription": "PostGIS in Action is the first book devoted entirely to PostGIS. It will help both new and experienced users write spatial queries to solve real-world problems. For those with experience in more traditional relational databases, this book provides a background in vector-based GIS so you can quickly move to analyzing, viewing, and mapping data.",
    "author": "Regina O. Obe",
    "category": "Internet"
},
{
    "bookid": 9,
    "title": "Hello! HTML5 & CSS3",
    "price": 999,
    "isbn": "1935182897",
    "pageCount": 325,
    "publishedDate": "2012-10-17T00:00:00.000-0700",
    "thumbnailUrl": "https://s3.amazonaws.com/AKIAJC5RLADLUMVRPFDQ.book-thumb-images/crowther.jpg",
    "shortDescription": "Quick and Easy HTML5 and CSS3 is written for the web designer or developer who wants a fast, example-oriented introduction to the new HTML and CSS features. After a quick review of the basics, you'll turn to what's new. Start by learning to apply important new elements and attributes by building your first real HTML5 pages. You'll then take a quick tour through the new APIs: Form Validation, Canvas, Drag & Drop, Geolocation and Offline Applications. You'll also discover how to include video and audio on your pages without plug-ins, and how to draw interactive vector graphics with SVG.",
    "author": "Rob Crowther",
    "category": "Internet"
},
{
    "bookid": 10,
    "title": "Secrets of the JavaScript Ninja",
    "price": 250,
    "isbn": "193398869X",
    "pageCount": 300,
    "publishedDate": "2012-12-27T00:00:00.000-0800",
    "thumbnailUrl": "https://s3.amazonaws.com/AKIAJC5RLADLUMVRPFDQ.book-thumb-images/resig.jpg",
    "shortDescription": "   Secrets of the Javascript Ninja is definitely a book for anyone looking to significantly improve their Javascript knowledge and skills.       Ryan Doherty, Web Development Engineer, Mozilla",
    "author": "John Resig",
    "category": "Java"
}
```