# Mean stack web development 103

#### Installing mongodb

---
![setting up mongodb certificates](https://github.com/user-attachments/assets/8b5e6933-31a0-4263-a77b-ff8437a4e4a7)
---
+ setting up an enviroment for mongodb
+ getting mongdb setup file for downloading
+ creating a source list for easy update of mongodb
```
sudo apt install -y gnupg curl
curl -fsSL https://www.mongodb.org/static/pgp/server-7.0.asc | sudo gpg -o /usr/keyshare/keyrings/mongodb-server-7.0.gpg --dearmor

echo "deb [ arch=amd64,arm64 signed-by=/usr/share/keyrings/mongodb-server-7.0.gpg ] https://repo.mongodb.org/apt/ubuntu jammy/mongodb-org/7.0 multiverse" | sudo tee /etc/apt/souces.list.d/mongodb-org-7.0.list
```
---
![installing mongodb](https://github.com/user-attachments/assets/eaff2125-d29e-4797-b048-6414d4bd5f8d)

![mongodb status](https://github.com/user-attachments/assets/35605fca-5190-4779-8e94-8372a13e02b0)

![installing node and body-parser](https://github.com/user-attachments/assets/21003695-1192-4e48-afc0-06db0b751590)
---
+ installing mongodb
+ start mongodb service
+ mongodb status
+ install npm
+ install body parser
+ install books

```
sudo apt install mongodb # install mongodb
sudo systemctl start mongodb # start mongo service
sudo apt install npm # install npm
sudo apt install body-parser # install body parser
```
---
![creating a server file](https://github.com/user-attachments/assets/93ea696c-723c-4ff1-b0c6-abc0d27661ca)

---

+ create dir callled books and cd into it
+ initialize npm
+ create or edit a file called server
```
mkdir Books # create dir
cd Books # move into Books
npm init # initialize npm
vi server.js # edit or create this file with the below config settings

const express = require('express');
const bodyParser = require('body-parser');
const mongoose = require('mongoose');
const path = require('path');

const app = express();
const PORT = process.env.PORT || 3300;

/// Mongodb Connection

mongoose.connect('mongodb://localhost:27017/test', {
  useNewUrlParser: true,
  useUnifiedTopology: true,
})
.then(() => console.log('Mongodb connected'))
.catch(err => console.err('Mongo connection error': ,err));

app.use(express.static(path.join(__dirname, 'public')));
app.use(bodyParser.json());

require('./apps/routes')(app);

app.listen(PORT, () => {
    console.log(`Server up : http://localhost:${PORT}`);
})
```

+ save the file


