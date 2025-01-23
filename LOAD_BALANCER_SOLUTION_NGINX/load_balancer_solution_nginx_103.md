# Registering new domain name and configuring secured connection using SSL/TLS certificates

---
* After you have registered a new domain name with any registar of choice

* Then you'll assign an ip to the Nginx LB server then associate your domain name with the Elastic ip.


* Once all the necessary stuff is done the next line of action will be to Configure Nginx to recognize the new domain name .
---
![Installing certbot](https://github.com/user-attachments/assets/111c816b-f750-4f21-aa42-eca9489f91ba)
---

* Now let's go back to our nginx.conf file

* Then replay the previous domain name with the current domain name.

* Now we'll move on to the next one which is installing certbot to ensure SSL on the website

```
sudo apt systemctl status snapd # Ensuring that snap deamon is running
sudo snap install --classic certbot # This line installs certbot for ssl certificate
```

+ All you have to do from there on is follow the prompt carefully.

+ Then follow the below steps

```
sudo ln -s /snap/bin/certbot /usr/bin/certbot
sudo certbot --nginx
```

* You can try the secured access using https://<domain name> to reach out to your domain Now your so called website should be reachable using HTTPS which a secured protocol a service the uses (TCP port 443) for the website
---
![Installing Certbot](https://github.com/user-attachments/assets/fc14ba27-ada8-45c5-9a93-4b2ef8268eb9)
---
### Setting up periodical renewal of your SSL/TLS certifates

* By default letsEncrypt certificates is valid for 90 days. so it's recommended to renew it at least every 60 days or more frequently.

+ Here's a command for renewing the certificates if the need be

```
sudo certbot renew --dry-run
```
---
![Configuring Cron jobs](https://github.com/user-attachments/assets/3c3db3fd-8bb8-45d3-bfd0-ee25d907beff)
---

+ But honestly the best way or should i say best practice is to have scheduled job that runs the renew command periodically and for this reason let us configure a cron job that will run the command twice a day .
```
crontab -e
## add the following line
* */12 * * *   root /usr/bin/certbot renew > /dev/null 2>&`
```

+ Mind you, you can also change the interval of the cronjob if twice daily is quite too often for you and you might not like it 



