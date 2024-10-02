# Lemp web stack 102

#### Installing Nginx web server

---

* Nginx:==
Nginx is a high-performance open-source web server and reverse proxy that is also used for HTTP cache and load balancing. Nginx is known for its efficiency, scalability and the ability to handle a large number of concurrent connections.

---
![installing nginx](https://github.com/user-attachments/assets/336668fa-4a08-4e5a-a8b2-f6542523ed9f)




+ installing nginx server

```
sudo apt install nginx  # Installing the nginx
```
---
![nginx status](https://github.com/user-attachments/assets/8ebcc56e-47d0-425f-b3fe-021ac7ad5f46)

+ checking for nginx service status
+ RED Indicates nginx service is running with an issue with it configuration
+ GREEN Indicates service is running without issues.
+ GREY Indicates nginx is not running
```
sudo systemctl status nginx > # check nginx status `rgb(0,255,0)` indicates nginx is running.
```

---

![testing connection from the localhost](https://github.com/user-attachments/assets/a56a72be-8ffd-4e73-9f5a-730230c4f4e9)


+ Testing the the nginx to see it serving content as expected from the host machine.
```
curl localhost # or

curl http://127.0.0.1:80
```
---
![testing nginx from the browser](https://github.com/user-attachments/assets/f8f2efcc-90ee-4451-916e-754e3126b735)

+ Testing nginx if serves content from another machine (which is any other <ip address>)
+ Or it can also be tested from any web browser at all .
```
http://<server ip address>
```
