# Devops Tooling Solution 103

#### Configuring the database server

---




---


+ Installing mysql

+ Create a database name

+ Create a database user

+ Granting user permissions



#### Preparing the Web server

---



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



---

