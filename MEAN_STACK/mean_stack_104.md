# Mean stact web implementation 104

#### installing express and setting up routes  to the server

---
![creating files](https://github.com/user-attachments/assets/fb1b0683-322a-47e2-8049-46bb34618997)
![installing express and mongoose](https://github.com/user-attachments/assets/b33c5a07-60df-4b97-beeb-ddfbfb39aeca)
---


+ install express mongoose

+ create dir called apps and move into it

+ create a file called route.js

```
const Book = require('../models/book');
const path = require('path');

module.exports = function(app) {
  app.get('/book', async (req, res) => {
    try {
      const books = await Book.find();
      res.json(books);
    }catch (err) {
      res.status(500).json({ message: 'Error fetching books', error: err.message });
     }
});

app.post('/book', async(req, res) => {
  try{
    const book = new Book ({
    name : req.body.name,
    isbn : req.body.isbn,
    author : req.body.author,
    pages : req.body.pages
  });

  const savedbook = await book.save();
  res.status(201).json({
	message: 'Successfully added a book',
  	book : savedbook
  });

  }catch (err) {
    res.status(400).json({ message: 'Error adding book', error: err.message });
    }
   });

   app.delete('/book/:isbn', async (req, res) => {
     try {
       const result = await Book.findOneAndDeletef({ isbn: req.params.isbn });
       if (!result) {
         return res.status(404).json({ message: 'Book not found' });
	 }
	 res.json({
	   message: 'Successfully deleted the book',
	   book : result
	 });
	} catch (err) {
	  res.status(500).json({ message: 'Error deleting book', error: err.message });
	 }
	});

	app.get('*', (req, res) => {
	  res.sendFile(path.join(__dirname, '../public', 'index.html'));
	  });
	 });
```

----
![script for the book.js](https://github.com/user-attachments/assets/f4f70a34-c999-424a-abd8-3c9694c795d7)
----

+ in the apps folder create a folder called models

+ move into the folder and create a file called book.js

```

mkdir models && cd models

emacs book.js

#### book.js scripts

const mongoose = require('mongoose');

const bookSchema = new mongoose.Schema({
      name : {type, String, required: true},
      isbn : {type, String, required: true, unique: true, index: true},
      author : {type, String, required: true},
      pages : {type, Number, required: true, min: 1}
      }, {
      	 timestamps: true
      })

module.exports = mogoose.model('Book', bookSchema);

```

+ then save the file
