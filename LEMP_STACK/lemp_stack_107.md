# Web stack implementation LEMP 107

### retrieving data from MySQL database with php
---


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



* Checking if the new user has all necessary permissions
```
mysql -u example_user -p # checking if user is able to login
```

---




* confirms the newly created database
```
SHOW DATABASES;
```
---





* Create a table in the database
```
CREATE TABLE example_database.todo_list (
item_id INT AUTO_INCREMENT,
content VARCHAR(255),
PRIMARY KEY(item_id)
);
```
---




* Inserting content into tables
```
INSERT INTO example_database.todo_list (content) VALUES ("my first important item");
SELECT * FROM example_database.todo_list;
```
---



+ checking for the output either from the terminal or from the browser
```
curl localhost/todo_list.php
http://<ipaddress>/todo_list.php
```




