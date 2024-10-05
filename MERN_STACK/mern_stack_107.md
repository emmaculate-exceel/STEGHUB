# Mern web stack implementation 107

## frontend creation
---
![create react app](https://github.com/user-attachments/assets/a9373908-5c30-4f00-8db8-f98ed6cd1eb6)

+ create a react app
+ install concurrently
+ install nodemon
```
npx create-react-app client
npx install concurrently --save-dev
npx install nodemon --save-dev
```
---
![reconfiguring package.json](https://github.com/user-attachments/assets/db26623d-5b10-43ac-95fe-315014fbef48)

+ reconfigured the package.json file in the todo directory
+ added a one more line to the package.json file of the client
```
### for package.json in todo dir
"scripts": {
"start": "node index.js",
"start-watch": "nodemon index.js",
"dev": "concurrently \" "npm run start-watch\" \"cd client && npm start\""
### for package.json in client
"proxy": "http://localhost:5000"
```
---
![run development](https://github.com/user-attachments/assets/6010f342-686b-480a-a3b6-e4053fe1e307)
+ confirm that everything is running as should
```
npm run dev # test developemnt
```
