# Mern web stack 103

#### Installing expressJS on the server
---





+ install expressJS
+ confirm the index.js file created via express
* install the dotenv module
```
npm install express # install express.js
touch index.js # create a index.js file
npm install dotenv # install the dotenv module
```
---





* edit the index.js file
```
const express = require('express');
require ('dotenv').config();

const app = express();

const port = process.env.PORT || 5000;

app.use((req, res, next) => {
res.header("Access-Control-Allow-Origin", "\*");
res.header("Access-Control-Allow-Headers", "Origin, X-requested-With, Content-Type, Accept");
next();
});

app.use((req, res, next) => {
res.send('Welcome to Express');
});

app.listen(port, () => {
console.log('Server running on ${port});
});

node index.js
```

---






+ confirm the output
+ 
```
curl http://localhost:5000 # checking your ouput from the terminal
http:<ipaddress>:5000 # checking the output from the browser
```

---



* create directory routes
* move into the directory
* create a file called app.js
+ edit the app.js file
```
mkdir routes # create directory
cd routes # move into the route directory
touch app.js # create file app.js
emacs app.js #
```
---





* code snippet
```
const express = require('express');
const router = express.router();

router.get('/todos', (req, res, next) => {

});

router.post('/todos', (req, res, next) => {

});

router.delete('/todos', (req, res, next) => {

});

module.exports = router;
```
