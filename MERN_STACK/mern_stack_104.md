# Mern web stack 104

#### Models

---
![installing mongoose](https://github.com/user-attachments/assets/3ce4ab57-d673-4a61-8b82-a929a9265494)
+ installing mongose
* create a directory called models
* move into the directory called models
+ create a file called todo.js
```
npm install mongoose # install mongoose
mdkir models # create a folder called models
cd models # move into models directory
touch todo.js
```
---
![editing script](https://github.com/user-attachments/assets/1a6cc0a6-ac4f-4f53-a2d6-e3bf9e93b255)
* editing the todo.js file
```
const mongoose = require('mongoose');
const Schema = mongoose.Schema;


// create schema for todo
const TodoSchema = new Schema ({
      action: {
      type : String,
      require : [true, 'The todo field is required']
      }
});


// create a model for the todo
const Todo = mongoose.model('todo', TodoSchema);

module.exports = Todo
```
---
![Updating our api.js file](https://github.com/user-attachments/assets/31c35390-8522-42b0-a573-e690823aba73)

* now in our previous task we created a filed called api.js
+ we'll need to go to the file and edit it
+ we'll delete the content of the file and replace it with this
```
const express = require('express');
const router = express.Router();
const Todo = require('../models/todo');

router.get('/todos', (req, res, next) => {

/// this will return all the data, exposing only the id and the action field to the client
Todo.find{}, 'action')
.then(data => res.json(data))
.catch(next)
});

router.post('/todos', (req, res, next) => {
	if (req.body.action) {
	   Todo.create(req.body){
	   .then(data => res.json(data))
	   .catch(next)
	} else {
	  res.json({
	  error: "The input field is empty"
	  })
	}
	})

	router.delete('/todos', (req, res, next) => {
		Todo.findOneAndDelete({"_id": req.params.id})
		.then(data => res.json(data))
		.catch(next)
		})

module.exports = router;
```

	
