# Tooling website deployment automation with continous integration 102

#### Setting up Jenkins on my ubuntu server


---
![installing javajdk](https://github.com/user-attachments/assets/21f8c96a-d189-452b-9c0f-8b7c6aef108e)

---


+ update my server

+ install java jdk headless cause jenkins will a depency to run as it should.
```
sudo apt update
sudo apt-get install default-jdk-headless
```

---
![adding jenkins repository](https://github.com/user-attachments/assets/30c862a2-4bd1-4689-8eb8-e2179ec7434f)

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
![jenkins status](https://github.com/user-attachments/assets/49e0ba34-ac3e-49e1-a222-781656da872f)
---

+ check jenkins status 
```
sudo systemctl status jenkins
```

### NOTE:

by default jenkins uses port 8080 so make sure that the port inboud rule is open for jenkins to relate and connect successfully .

---
![jenkins on the browser](https://github.com/user-attachments/assets/00d27238-8dcc-4b25-98b8-c4e14c6e51a0)
---

+ From the browser connect to the <serverip>:8080

+ You will be prompted to create a default admin passwordd for the page

+ which can be retrieved from the below directory from your server
```
/var/lib/jenkins/secrets/initialAdminPassword
```

---
![customize jenkins account](https://github.com/user-attachments/assets/021d1795-9657-4def-9db5-412357fbc132)
---


+ Customize your jenkins account

+ Upon plugin installation and account creation (create an admin user and you will get you jenkins server address)

+ Then installation is complete

y
