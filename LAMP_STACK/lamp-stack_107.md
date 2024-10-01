# lamp stack 107

#### Enabling php on the website

---
![Editing config file](https://github.com/user-attachments/assets/2b5f962c-7702-4ff7-aed7-934714fded94)

* Editing the behavioral pattern of the ***/etc/apache2/mods-enabled/dir.conf file*** in your desired order/manner in which the index.php file is listed within the DirectoryIndex directive.

```
sudo emacs /var/www/mods-enabled/dir.conf
```
+ then using the below config file
```
<IfModule mod_dir.c>
	  #change this:
	  #DirectiveIndex index.html index.cgi index.pl index.php index.xhtml index.htm
	  #to This:
	  DirectiveIndex index.php index.html index.cgi index.pl index.xhtml index.htm
</IfModule>
```
---
![reloading apache2 service](https://github.com/user-attachments/assets/51a4508a-10a9-46d9-abf1-86bacac6749c)


+ then run the next command
```
sudo systemctl reload apache2 # this indicates we now have a new configuration and we have to reload the service in order for the service to pick up the new configuration
```
---
![creating an index.php file](https://github.com/user-attachments/assets/635f7a78-c5df-4406-a4e9-5d4852083df4)

+ now it's time to create a php information page using the below command

```
sudo emacs /var/www/projectlamp/index.php

<?php
    phpinfo()
```

![php report](https://github.com/user-attachments/assets/aff69244-9a51-44dd-9875-5dd5c47e8126)


---
* now you can remove the config file since the whole process is tested and trusted.
```
sudo rm /var/www/projectlamp/index.php
```
