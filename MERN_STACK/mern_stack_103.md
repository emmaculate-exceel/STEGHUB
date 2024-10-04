# Mern web stack 103

#### Installing expressJS on the server
---
![installing expressjs](https://github.com/user-attachments/assets/98ce9fb5-872b-4bba-8464-1f92878e3687)

+ install expressJS
+ confirm the index.js file created via express
* install the dotenv module
```
npm install express # install express.js
touch index.js # create a index.js file
npm install dotenv # install the dotenv module
```
---
![writing script](https://github.com/user-attachments/assets/dfeeab46-e74e-4976-ba6c-74c68d8e3750)

* writing a express.js script in to the index.js file
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
![output on terminal](https://github.com/user-attachments/assets/c605a2eb-e7a2-4332-b56f-342bf8863a6a)
![output on the web](https://github.com/user-attachments/assets/82ef2873-b338-414d-a58b-c852e63417b6)

+ confirming the output 
```
curl http://localhost:5000 # checking your ouput from the terminal
http:<ipaddress>:5000 # checking the output from the browser
```

---
![creating the route directory](https://github.com/user-attachments/assets/23e07401-9728-4353-b265-e5c072b75521)

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
![api code snippet](https://github.com/user-attachments/assets/e05b017b-91c4-4d1f-a53d-d35ce6074e9d)
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
