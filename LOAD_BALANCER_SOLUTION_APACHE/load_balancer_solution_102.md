# Load balancer solution with apache2 102


#### configuring apache2 as a load balancer
---
![Installing apache2](https://github.com/user-attachments/assets/68b2155a-4b9c-4e8e-95b3-2adc0d77cea9)
---
+ Installing the neccessary dependencies for configuring apache2 as a load balancer

+ Configuring apache2 as a load balancer

```
sudo apt update
sudo apt install apache2 -y
sudo apt install libxml2-dev

# enabling Modules for apache working as a load balancer

sudo a2enmod rewrite
sudo a2enmod proxy
sudo a2enmod proxy_balancer
sudo a2enmod proxy_http
sudo a2enmod headers
sudo a2enmod lbmethod_bytraffic

# After enabling modules restart apache2 services

sudo systemctl restart apache2.service
```

---
![Apache2 Status](https://github.com/user-attachments/assets/a9df4554-bf54-4dd6-89f0-d81b259f133c)
---

+ Make sure apache2 is running

```
sudo systemctl status apache2
```
---
![Load balancer configurations](https://github.com/user-attachments/assets/6dbb1ae9-e99a-4124-a687-266efcb3e0d2)
---

+ Configuring apache2

```
sudo vi /etc/apache2/sites-available/000-default.conf

# Add this configuration into this section <VirtualHost *:80>  </VirtualHost>

<Proxy "balancer://mycluster">
               BalancerMember http://<WebServer1-Private-IP-Address>:80 loadfactor=5 timeout=1
               BalancerMember http://<WebServer2-Private-IP-Address>:80 loadfactor=5 timeout=1
               ProxySet lbmethod=bytraffic
               # ProxySet lbmethod=byrequests
        </Proxy>

        ProxyPreserveHost On
        ProxyPass / balancer://mycluster/
        ProxyPassReverse / balancer://mycluster/

# Restart apache server

sudo systemctl restart apache2
```
---
![config test](https://github.com/user-attachments/assets/198595e6-c3d3-4f5a-9deb-ae61bf4b660e)
---


+ Confirm that the configuration works
```
Visit the site http://<Load-Balancer-Public-IP-Address-or-Public-DNS-Name>/index.php
```
