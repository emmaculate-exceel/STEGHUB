# Lamp stack

#### Creating a virtual Host for my website using Apache2

---
![creating a directory for the config file](https://github.com/user-attachments/assets/1cd12866-7208-4373-8cc6-b07c2c154435)

* Creating a directory for my projectlamp using the ***mkdir*** command as follows.
```
sudo mkdir /var/www/projectlamp  # creating project directory
```

---
![Granting users the required permissions](https://github.com/user-attachments/assets/964ffa88-32e4-4395-9d8b-44d5e6cf3fa1)

* Assigning owners the right permissions of the directory using the $USER environmental variable.
```
sudo chown -R $USER:$USER /var/www/projectlamp # assigning the current user the necessary permission needed to carry out it action
```
---
![configuring projectlamp.conf file for apache2](https://github.com/user-attachments/assets/156ba5cb-6957-4e80-86ea-9d6960701f58)


* Creating a config file for the apache2 server in sites-available directory using my preferred terminal text editor
```
sudo emacs /etc/apache2/sites-available/projectlamp.conf # configuration file for apache2 
```
---
![running the necessary command to enhance the config file](https://github.com/user-attachments/assets/12c46864-5e92-4dc9-a49c-3b6857628ce4)
![Screenshot_2024-10-01_06_23_53](https://github.com/user-attachments/assets/2a4a69e7-d63d-4265-95be-000e39cc9a7f)


* now one has to run the below commands for the configurations to be effective
```
sudo a2dissite 000-default # dissable the default virtual host
sudo a2ensite projectlamp.conf # enable the custom virtual host
sudo apache2ctl configtest # checking config file to make sure there are no syntax error or configuration problem.
sudo systemctl reload apache2 # make sure to reload the apache2 service else the newly configured file won't work.
```
