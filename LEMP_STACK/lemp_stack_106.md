# web stack LEMP 106

#### Testing php with nginx

---
![creating a file](https://github.com/user-attachments/assets/348687b2-8bf7-45f8-a9f2-9af8ab5cecec)
* creating a file inside the projectLEMP directory
```
sudo emacs /var/www/projectLEMP/info.php  # creating a file
```
---
![writing content into the file](https://github.com/user-attachments/assets/c3f96583-ed81-45f4-9e6b-ca5b80309a08)
+ writing content into the info.php file
```
<?php
   phpinfo();   # writing content into file
```
---
![Screenshot_2024-10-02_15_23_32](https://github.com/user-attachments/assets/4989f399-583b-4e3b-af01-eeb08253f987)
* checking if the result is as expected
* remove the file once test is satisfied
```
http://`ipaddress`/info.php # from the browser 
curl localhost/info.php  # from the terminal
sudo rm /var/www/projectLEMP/info.php  # removes the info.php file
```
