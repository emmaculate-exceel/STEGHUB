# Web Stack Implementation 105

#### Configuring Nginx to Use PHP Processor

---



+ creating a directory for projectLEMP
```
sudo mkdir /var/www/projectLEMP # creating directory for projectLEMP
 ```

---





+ changing owner permissions for the projectLEMP
```
sudo chown -R $USER:$USER /var/www/projectLEMP # changing owners permissions
```
---



* creating a configuration for the nginx server using your preferred terminal editor
```
sudo emacs /etc/nginx/sites-available/projectLEMP # creating a config file
```
---



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





+ creating a symbolic link for nginx site-enabled folder to complete my nginx configuration
```
sudo ln -s /etc/nginx/sites-available/projectLEMP /etc/nginx/sites-enabled/ # symbolic link
```
---



+ checking nginx configurations for errors or any issues.
```
sudo nginx -t # testing nginx configurations for any issues
```

---


+ activating my configuration in order for nginx to apply the new configuration rules
```
sudo unlink /etc/nginx/sites-available/default # delete the nginx default config
```
---



+ restart/reloading nginx service
```
sudo systemctl reload nginx
```
---



* creating my own demo file to test nginx if it's serving my content as should
```
sudo echo 'Hello LAMP from hostname' $(TOKEN=`curl -X PUT "http://169.254.169.254/latest/api/token" -H "X-aws-ec2-metadat-token-ttl-seconds: 21600"` &&  curl -H "X-aws-ec2-metadata-token: $TOKEN" -s http://169.254.169.254/latest/meta-data/public-hostname) 'with public IP' $(TOKEN=`curl -X PUT "http://169.254.169.154/latest/api/token" -H "X-aws-ec2-metadata-token-ttl-seconds: 21600"` && curl -H "X-aws-ec2-metadata-token: $TOKEN" -s http://169.254.169.254/latest/meta-data/public-ipv4) > /var/www/projectlamp/index.html
```
---




+ confirm nginx is serving my content as should from the terminal and from my browser.
```
curl localhost # from the terminal
http://<server_ip_address>:80 # from the browser
```
