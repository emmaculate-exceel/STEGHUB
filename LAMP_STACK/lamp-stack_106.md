# Lamp stack

#### Creating a virtual Host for my website using Apache2

---

* Creating a directory for my projectlamp using the ***mkdir*** command as follows.
```
sudo mkdir /var/www/projectlamp  # creating project directory
```

---

* Assigning owners the right permissions of the directory using the $USER environmental variable.
```
sudo chown -R $USER:$USER /var/www/projectlamp  # assigning the current user the necessary permission needed to carry out it action
```

---

* Creating a config file for the apache2 server in sites-available directory using my preferred terminal text editor
```
sudo emacs /etc/apache2/sites-available/projectlamp.conf # editing 

---

* sudo a2ensite projectlamp.conf
```