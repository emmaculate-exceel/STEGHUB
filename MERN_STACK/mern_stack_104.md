# Mern web stack 104

#### Models

---




+ installing mongose
* create a directory called models
* move into the directory called models
+ create a file called todo.js
---





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




* no in our previous task we created a filed called api.js
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

	