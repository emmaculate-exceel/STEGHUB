# Mern web stack 105

#### MongoDB database
---
![Signing up ](https://github.com/user-attachments/assets/05e316fd-e6a5-4273-81e0-e4056f05951f)

+ sign up for a share cluster free account
+ select aws as the cloud provider
+ choose a region near you
---
![configuring atlas](https://github.com/user-attachments/assets/26d66752-fe6e-4ca4-8ea0-59db1286a259)

+ allow access to mongodb from anywhere
+ make sure to change the deleting time from 6hrs to 1 week
+ create a mongodb database in mLab
---
![editing .env](https://github.com/user-attachments/assets/9c210366-0cea-4d25-9f74-ce3abb54ecc5)

+ create a .env file
+ emacs .env
```
DB = 'mongodb+srv://<username>:<password>@<network-address>/<dbname>?retryWrites=true&w=majority'
```
---
![editing index.js file](https://github.com/user-attachments/assets/76c6220c-8da9-4f62-9f3d-2f3583d49235)

+ edit the index.js file
+ update the content to this

```
const express = require('express');
const bodyParser = require('body-parser');
const mongoose = require('mongoose');
const routes = require('Routes');
const path = require('path');
require('dotenv').config();

const app = express();
const port = process.env.PORT || 5000;

// connection to the database
mongoose.connect(process.env.DB, { useNewUrlParser: true, useUnifiedTopology: true })
.then(() => console.log(`Database connected Successfully`))
.catch(err => console.log(err));

// since mongoose promise is depreciated , we overides it with node promise
mongoose.Promise = global.Promise;

app.use((req, res, next) => {
res.header("Access-Control-Allow-Origin", "\*");
res.header("Access-Control-Allow-Headers", "Origin", X-Requested-With, Content-Type, Acccept");
next();
});

app.use(bodyParser().json);

app.use('/api', routes);

app.use((err, req, res, next) => {
console.log(err);
next();
});

app.listen(port, () => {
console.log(`Server running on ${port}`);
});
```

---

![Start the service](https://github.com/user-attachments/assets/08e4557b-7d4e-46ac-b1ea-fa81e72df636)

* start the service
```
node index.js
```
