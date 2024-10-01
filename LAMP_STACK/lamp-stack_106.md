# Lamp stack

#### Creating a virtual Host for my website using Apache2

---

* Creating a directory for my projectlamp using the ***mkdir*** command as follows.
```
sudo mkdir /var/www/projectlamp  -# creating project directory-
```

---

* Assigning owners the right permissions of the directory using the $USER environmental variable.
```
sudo chown -R $USER:$USER /var/www/projectlamp  _# assigning the current user the necessary permission needed to carry out it action_
```

---

* Creating a config file for the apache2 server in sites-available directory using my preferred terminal text editor
```
sudo emacs /etc/apache2/sites-available/projectlamp.conf # editing 

---


```
sudo a2dissite 000-default _# dissable the default virtual host_
sudo a2ensite projectlamp.conf _# enable the custom virtual host_
sudo apache2ctl configtest _# checking config file to make sure there are no syntax error or configuration problem._
sudo systemctl reload apache2 _# make sure to reload the apache2 service else the newly configured file won't work._
```