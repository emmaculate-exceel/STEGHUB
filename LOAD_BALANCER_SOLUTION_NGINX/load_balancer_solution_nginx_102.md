# Load balancing using Nginx
### Configuring Nginx as a load balancer

* You can either use load Apache as a load balancer or Nginx but in this case we'll go with Nginx

+ First we'll create and EC2 Virtual Machine on Ubuntu 20.04 or that of your choice and give it a name of choice as well .

+ configure it as you'll like it serve .
---
![Installing Nginx](https://github.com/user-attachments/assets/ee7ba860-3f05-4d18-90ab-fadf35731a8f)

```
sudo apt update
sudo apt install nginx
```
---
![Setting up Nginx configurations](https://github.com/user-attachments/assets/65fa284e-9d40-4ecf-94d0-67ca7a692602)


+ Configure Nginx Load balancer using the name of the Web server which has to be defined in the /etc/hosts

* Let's Open the default nginx configuration file
```
sudo vi,emacs or nano /etc/nginx/nginx.conf
# Then we'll pass the below configurations right into it

upstream <project name> {
         server Web1 weight=5;
         server Web2 weight=5;
}

server {
       listen 80;
       server_name www.<domain_name.com>;

       location / {
                proxy_pass http://<projectname;
                }
}

# Comment out the line
# include /etc/nginx/sites_enabled/*

```
---
![Testing the Outpu](https://github.com/user-attachments/assets/6e550df1-b9e8-4605-bdb5-ece853861f93)
---
+ Checking my final Output


* Restart Nginx and making sure the service is up and running

```
sudo systemctl restart nginx # restarting nginx for the new configuration to take place
sudo systemctl status nginx # checking if nginx is up and running
```
