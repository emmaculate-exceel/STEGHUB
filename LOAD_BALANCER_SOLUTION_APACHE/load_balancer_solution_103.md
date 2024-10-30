# Load balancer solution with apache2 103

####  Optional step configure local DNS name resolution


---



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


---

+ Now you can update the apache2 load balancer configuration to this

```
BalancerMember http://Web1:80 loadfactor=5 timeout=1
BalancerMember http://Web2:80 loadfactor=5 timeout=1
```

---


---


+ Output after curling the the ipaddress
