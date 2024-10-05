# Mern web stack implementation 107

## frontend creation
---



+ create a react app
+ install concurrently
+ install nodemon
```
npx create-react-app client
npx install concurrently --save-dev
npx install nodemon --save-dev
```

---




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



+ confirm that everything is running as should
```
npm run dev # test developemnt
```
