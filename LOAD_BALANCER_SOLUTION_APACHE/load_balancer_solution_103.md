# Load balancer solution with apache2 103

####  Optional step configure local DNS name resolution


---
![Configuring the host file](https://github.com/user-attachments/assets/8fe1b227-a71e-43ef-b56c-73de1e3a93d6)
---


+ Configuring the hosts file

```
#Open this file on your LB server

sudo vi /etc/hosts

#Add 2 records into this file with Local IP address and arbitrary name for both of your Web Servers

<WebServer1-Private-IP-Address> Web1
<WebServer2-Private-IP-Address> Web2
```

---
![Updating the host file](https://github.com/user-attachments/assets/afd29784-6358-4954-935c-a1666f1d9826)
---

+ Now you can update the apache2 load balancer configuration to this

```
BalancerMember http://Web1:80 loadfactor=5 timeout=1
BalancerMember http://Web2:80 loadfactor=5 timeout=1
```

---
![curl the lb ip](https://github.com/user-attachments/assets/b7d27a13-f064-42ae-85f1-82470036e7b5)
---

+ Output after curling the the ipaddress for the load balancer
