# lamp stack 107

#### Enabling php on the website

---

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

+ then run the next command
```
sudo systemctl reload apache2 # this indicates we now have a new configuration and we have to reload the service in order for the service to pick up the new configuration
```

+ now it's time to create a php information page using the below command

```
sudo emacs /var/www/projectlamp/index.php

<?php
    phpinfo()
```

---



* now you can remove the config file since the whole process is tested and trusted.
```
sudo rm /var/www/projectlamp/index.php
```