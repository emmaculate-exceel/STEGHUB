# Installing Apache2 and updating firewall 103


*Apache is a widely used webserver software that is developed and maintained by apache software foundation .

* the  apache web server is one of the most popular web servers in the world and well documented.
![installing and checking apache service](https://github.com/user-attachments/assets/1472db95-0bc6-4497-8358-6d3dbecce784)




```
sudo apt install apache2
sudo systemctl start apache2
sudo systemctl status apache2
```

### Checking if the apache 2 service is running
![checking apache2 status information](https://github.com/user-attachments/assets/51be4b77-3aad-48d8-9ba0-8a6ca1b68720)


```
curl localhost or curl http://localhost:80
```
* from the local computer you curl <server ip address>
* from the browser you type in the <server public ip>:80 into the url bar and type enter	 
