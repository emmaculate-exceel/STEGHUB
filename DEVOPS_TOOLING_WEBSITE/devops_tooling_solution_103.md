# Devops Tooling Solution 103

#### Configuring the database server

---
![Installing mysql](https://github.com/user-attachments/assets/68bc5084-602e-4dbc-88d3-c05c5c0f52dd)
---


+ Installing mysql

+ Create a database name

+ Create a database user

+ Granting user permissions



#### Preparing the Web server

---
![Nfs installation](https://github.com/user-attachments/assets/70d73f4f-74e8-4df1-a565-b7eea72944d1)
---
+ Install NFS client

+ Configure NFS client

+ Mount NFS server for apps

```
sudo yum install nfs-utils nfs4-acl-tools -y
sudo mkdir /var/www
sudo mount -t nfs -o rw,nosuid <NFS-Server-Private-IP-Address>:/mnt/apps /var/www
```
---
![Old config](https://github.com/user-attachments/assets/c8d334de-3f7b-4468-9ade-e364b2d282e1)
![New config](https://github.com/user-attachments/assets/3a94a2cf-e630-4d1f-a6d7-a0b55459145c)
---

+ Edit the the fstab
```
sudo vi /etc/fstab
```

+ Then run the below commands
```
sudo yum install httpd -y

sudo dnf install https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm

sudo dnf install dnf-utils http://rpms.remirepo.net/enterprise/remi-release-8.rpm

sudo dnf module reset php

sudo dnf module enable php:remi-7.4

sudo dnf install php php-opcache php-gd php-curl php-mysqlnd

sudo systemctl start php-fpm

sudo systemctl enable php-fpm

setsebool -P httpd_execmem 1
```

---

![Toolinglogin](https://github.com/user-attachments/assets/ce524acd-f326-4b29-a86c-791a310e4171)
![adminpage](https://github.com/user-attachments/assets/d3d77094-e66c-48e8-b006-228a9b5a87b0)
---

