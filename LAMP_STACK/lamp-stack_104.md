# lamp stack implementation 104
### Installing mysql


##### mysql is a database management system(RDBMS) that uses structure Query language	for accessing and managing data


```
sudo apt install mysql-server
sudo mysql
```



```
ALTER USER 'root'@'localhost' IDENTIFIED WITH 'mysql_native_password' BY 'PassWord.1';
exit
```



#### securing mysql installation by improving mysql security



```
sudo mysql_native_password
```
* follow the prompt and customize it to your taste