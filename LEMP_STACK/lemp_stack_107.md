# Web stack implementation LEMP 107

### retrieving data from MySQL database with php
---
![mysql console](https://github.com/user-attachments/assets/17b17069-f493-42d2-bf36-073e6c5c3548)

+ Connecting to mysql console
+ create a database "example_database"
+ create a user "example_user"
+ grant permissions to user "example_user" to connect "example_database" from anywhere either local or remote
* exit mysql
```
sudo mysql # connect to console
CREATE DATABASE # create database
CREATE USER 'example_user' IDENTIFIED WITH mysql_native_password BY 'PassWord.1'; # create user
GRANT ALL ON example_database.* TO 'example_user'@'%'; # grant access to 'example_user' to 'example_database' from anywhere
exit # exit mysql console
```
---
![checking user permissions](https://github.com/user-attachments/assets/9cff858d-fe26-4fd1-9b7e-ef39390f1dcc)
* Checking if the new user has all necessary permissions
```
mysql -u example_user -p # checking if user is able to login
```
---
![database and users](https://github.com/user-attachments/assets/78599c4d-f119-4b94-a01f-0f843d28d023)

* confirms the newly created database and user 
```
SHOW DATABASES;
```
---
![creating table in database](https://github.com/user-attachments/assets/6b5fc68b-c081-451c-ac52-2a67d6dbdc37)

* Creating a table in the database
```
CREATE TABLE example_database.todo_list (
item_id INT AUTO_INCREMENT,
content VARCHAR(255),
PRIMARY KEY(item_id)
);
```
---
![insertion of content](https://github.com/user-attachments/assets/db72a8fc-bb6c-43e5-aca3-a0847fd38899)

* Inserting content into tables
```
INSERT INTO example_database.todo_list (content) VALUES ("my first important item");
SELECT * FROM example_database.todo_list;
```
---
![final output](https://github.com/user-attachments/assets/9717049e-e6c0-458a-881e-8d2d200af10d)

+ checking for the output either from the terminal or from the browser
```
curl localhost/todo_list.php
http://<ipaddress>/todo_list.php
```




