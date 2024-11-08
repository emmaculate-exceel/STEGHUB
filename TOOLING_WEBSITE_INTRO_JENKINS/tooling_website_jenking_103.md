# Tooling website deployment automation with continous integration 103


#### configuring jenkins to retrieve source codes from github using webhooks


---
![Enabling webhooks on github](https://github.com/user-attachments/assets/ce005b56-eb07-4ba8-b824-b096a76f87fb)
---

+ Enabling webhooks on github repository settings

---
![Enabling freestyle project](https://github.com/user-attachments/assets/20f04ba4-4e68-47c2-8ff4-577a3c10cb24)
---

+ Enabling freestyle project in jenkins

---
![adding github repo](https://github.com/user-attachments/assets/cc498ff4-0b17-483c-8b83-b4176aaf29a9)
---

+ Adding github repo url to the jenkins project .

---
![creating repo for project](https://github.com/user-attachments/assets/702753b1-91ff-4b07-ae84-24d1660da767)
---

+ Manually creating a build of my project into jenkins

---
![output of the request](https://github.com/user-attachments/assets/cc937e6e-7435-4c9b-88a5-da534c2b87a3)
---

+ Checking the output of the build in the jenkins console.

---
![Automatic build](https://github.com/user-attachments/assets/3ed30393-5e78-4cb2-bcb7-b7083f697088)
---

+ Creating an Automatic build for jenkins using using github hook trigger

---
![Status on jenkins](https://github.com/user-attachments/assets/0e8184fd-10fa-49fd-b1aa-4b292c2b26f1)
---

+ Checking the status on my jenkins console

---
![Terminal output](https://github.com/user-attachments/assets/b87984da-1f8c-407d-b1ef-c8b793aa9a5a)
---

+ checking the file location on my server
```
sudo ls /var/lib/jenkins/jobs/tooling_github/builds/<number>/archive/
```
