# web stack LEMP 106

#### Testing php with nginx

---



* creating a file inside the projectLEMP directory
```
sudo emacs /var/www/projectLEMP/info.php  # creating a file
```

---



+ writing content into the info.php file
```
<?php
   phpinfo();   # writing content into file
```
---





* checking if the result is as expected
* remove the file once test is satisfied
```
http://`ipaddress`/info.php # from the browser 
curl localhost/info.php  # from the terminal
sudo rm /var/www/projectLEMP/info.php  # removes the info.php file
```
