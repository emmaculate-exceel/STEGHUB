# Lemp web stack 102

#### Installing Nginx web server
---

* Nginx:==
Nginx is a high-performance open-source web server and reverse proxy that is also used for HTTP cache and load balancing. Nginx is known for its efficiency, scalability and the ability to handle a large number of concurrent connections.

---




+ installing nginx server

```
sudo apt install nginx > # Installing the nginx
```
---



 + checking for nginx service status
 `rgb(255,0,0)` Indicates nginx service is running with an issue with it configuration
 `rgb(0,255,0)` Indicates service is running without issues.
 `rgb(211,211,211)` Indicates nginx is not running
```
sudo systemctl status nginx > # check nginx status `rgb(0,255,0)` indicates nginx is running.
```

---




+ Testing the the nginx to see it serving content as expected from the host machine.
```
curl localhost > or

curl http://127.0.0.1:80
```
---



+ Testing nginx if serves content from another machine (which is any other <ip address>)
+ Or it can also be tested from any web browser at all .
```
http://<server ip address>
```