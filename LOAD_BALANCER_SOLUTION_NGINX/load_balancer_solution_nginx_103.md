# Registering new domain name and configuring secured connection using SSL/TLS certificates

---
* After you have registered a new domain name with any registar of choice

* Then you'll assign an ip to the Nginx LB server then associate your domain name with the Elastic ip.


* Once all the necessary stuff is done the next line of action will be to Configure Nginx to recognize the new domain name .

---

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

### Setting up periodical renewal of your SSL/TLS certifates

* By default letsEncrypt certificates is valid for 90 days. so it's recommended to renew it at least every 60 days or more frequently.

+ Here's a command for renewing the certificates if the need be

```
sudo certbot renew --dry-run
```

+ But honestly the best way or should i say best practice is to have scheduled job that runs the renew command periodically and for this reason let us configure a cron job that will run the command twice a day .
```
crontab -e
## add the following line
* */12 * * *   root /usr/bin/certbot renew > /dev/null 2>&`
```

+ Mind you, you can also change the interval of the cronjob if twice daily is quite too often for you and you might not like it 



