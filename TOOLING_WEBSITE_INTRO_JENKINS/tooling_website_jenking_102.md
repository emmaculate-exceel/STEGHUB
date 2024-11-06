# Tooling website deployment automation with continous integration 102

#### Setting up Jenkins on my ubuntu server


---


---


+ update my server

+ install java jdk headless cause jenkins will a depency to run as it should.
```
sudo apt update
sudo apt-get install default-jdk-headless
```

---


---

+ adding jenkins repository to my ubuntu repo

+ adding jenkins to my source list directory

+ updating ubuntu server

+ installing jenkins
```
wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key/ | sudo apt-key add -
sudo sh -c 'echo deb https://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
sudo apt update
sudo apt-get install jenkins
```

---


---

+ check jenkins status 
```
sudo systemctl status jenkins
```

### NOTE:

by default jenkins uses port 8080 so make sure that the port inboud rule is open for jenkins to relate and connect successfully .

---


---

+ From the browser connect to the <serverip>:8080

+ You will be prompted to create a default admin passwordd for the page

+ which can be retrieved from the below directory from your server
```
/var/lib/jenkins/secrets/initialAdminPassword
```

---


---


+ Customize your jenkins account

+ Upon plugin installation and account creation (create an admin user and you will get you jenkins server address)

+ Then installation is complete

