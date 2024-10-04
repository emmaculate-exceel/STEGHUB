# Mern web stack 105

#### MongoDB database
---






+ sign up for a share cluster free account
+ select aws as the cloud provider
+ choose a region near you
---





+ allow access to mongodb from anywhere
+ make sure to change the deleting time from 6hrs to 1 week
+ create a mongodb database in mLab
---





+ create a .env file
+ emacs .env
```
DB = 'mongodb+srv://<username>:<password>@<network-address>/<dbname>?retryWrites=true&w=majority'
```
---




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





* start the service
```
node index.js
```