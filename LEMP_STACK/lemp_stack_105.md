# Web Stack Implementation 105

#### Configuring Nginx to Use PHP Processor

---
![creating a directory for pojectLEMP](https://github.com/user-attachments/assets/23be7331-cd99-4290-8132-beb0f07cd601)

+ creating a directory for projectLEMP
```
sudo mkdir /var/www/projectLEMP # creating directory for projectLEMP
```
---
![changing ownership](https://github.com/user-attachments/assets/6871b18f-bc6a-402e-98d3-03e1eb8e643c)

+ changing owner permissions for the projectLEMP
```
sudo chown -R $USER:$USER /var/www/projectLEMP # changing owners permissions
```
---
![trying to edit config file](https://github.com/user-attachments/assets/cd51575b-f6ae-4ea2-b212-bc4e1dd99188)

* creating a configuration for the nginx server using your preferred terminal editor
```
sudo emacs /etc/nginx/sites-available/projectLEMP # creating a config file
```
---
![writing configuration](https://github.com/user-attachments/assets/6444c0a6-634b-47fc-b2e6-4c96c969a680)

+ writing my configuration directives for nginx to serve my content as i have always wanted
```
server {

       listen 80;
       server_name projectLEMP www.projectLEMP;
       root /var/www/projectLEMP;

       index index.html index.htm index.php;

       location / {
                try_files $uri  $uri/ =404;
        }

        location ~ \.php$ {
                 include snippets/fastcgi-php.conf;
                 fastcgi_pass unix:/var/run/php/php8.3-fpm.sock;
        }

        location ~ /\.ht {
                 deny all;
        }
}
```
---
![Symbolic link](https://github.com/user-attachments/assets/6807fb5e-7e46-46af-b32c-35340be71f10)

+ creating a symbolic link for nginx site-enabled folder to complete my nginx configuration
```
sudo ln -s /etc/nginx/sites-available/projectLEMP /etc/nginx/sites-enabled/ # symbolic link
```
---
![checking configurations](https://github.com/user-attachments/assets/f811bbc4-e772-4a3f-ab58-8471bde45acd)

+ checking nginx configurations for errors or any issues.
```
sudo nginx -t # testing nginx configurations for any issues
```

---
![unlinking nginx default](https://github.com/user-attachments/assets/d2c81c8e-5340-4c41-82a6-49a34faf1527)

+ deactivating nginx default configuration in order for nginx to apply the new configuration rules
```
sudo unlink /etc/nginx/sites-available/default # delete the nginx default config
```
---
![restart nginx](https://github.com/user-attachments/assets/b1a7e223-6b6a-42a3-b747-36d878520c5d)

+ restart/reloading nginx service
```
sudo systemctl reload nginx
```
---
![custom output](https://github.com/user-attachments/assets/e02da78c-92a9-4c90-83e7-4944a4c9a121)

* creating my own demo file to test nginx if it's serving my content as should
```
sudo echo 'Hello LAMP from hostname' $(TOKEN=`curl -X PUT "http://169.254.169.254/latest/api/token" -H "X-aws-ec2-metadat-token-ttl-seconds: 21600"` &&  curl -H "X-aws-ec2-metadata-token: $TOKEN" -s http://169.254.169.254/latest/meta-data/public-hostname) 'with public IP' $(TOKEN=`curl -X PUT "http://169.254.169.154/latest/api/token" -H "X-aws-ec2-metadata-token-ttl-seconds: 21600"` && curl -H "X-aws-ec2-metadata-token: $TOKEN" -s http://169.254.169.254/latest/meta-data/public-ipv4) > /var/www/projectlamp/index.html
```
---
![confirm nginx is serving content](https://github.com/user-attachments/assets/0bc4edda-4eeb-4cf3-8b2b-1b842f317dc8)

+ confirm nginx is serving my content as should from the terminal and from my browser.
```
curl localhost # from the terminal
http://<server_ip_address>:80 # from the browser
```
