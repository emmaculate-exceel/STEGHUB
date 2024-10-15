# Devops tooling solution 


#### preparing my instance for the
---
![Installing nfs](https://github.com/user-attachments/assets/a2fbfdda-b41b-4b67-b050-580944e393bb)

![Status](https://github.com/user-attachments/assets/a2fab063-12fd-45d5-8135-469f4f99a7a8)
---

+ Create volumes for the instance

+ Create mount points for the instance

+ Installing the nfs server for the instance

+ Starting nfs-server
```
sudo yum -y update
sudo yum install nfs-utils -y
sudo systemctl start nfs-server.service
sudo systemctl enable nfs-server.service
sudo systemctl status nfs-server.service

```

---
![change permissions](https://github.com/user-attachments/assets/764873a7-2206-4db9-b112-fbbf75adb13d)

![change ownership](https://github.com/user-attachments/assets/a89e6049-5d9c-41d7-8f6d-03cd40c02905)
---

+ export mount point for the server

+ Change user permissions for the dir

+ Change Owner permissions for the dir

```
sudo chown -R nobody: /mnt/apps
sudo chown -R nobody: /mnt/logs
sudo chown -R nobody: /mnt/opt

sudo chmod -R 777 /mnt/apps
sudo chmod -R 777 /mnt/logs
sudo chmod -R 777 /mnt/opt

sudo systemctl restart nfs-server.service
```

---
![previous confg](https://github.com/user-attachments/assets/b2ce7f92-77f9-4e7d-851c-3cbe0ab2e7f5)

![current Config](https://github.com/user-attachments/assets/1e3c55a5-a90a-4611-b4bd-ddcc4aebb183)
---

+ Configure access to NFS Client

```

sudo vi /etc/exports

/mnt/apps <Subnet-CIDR>(rw,sync,no_all_squash,no_root_squash)
/mnt/logs <Subnet-CIDR>(rw,sync,no_all_squash,no_root_squash)
/mnt/opt <Subnet-CIDR>(rw,sync,no_all_squash,no_root_squash)

Esc + :wq!

sudo exportfs -arv
```
---
![NFS info](https://github.com/user-attachments/assets/f1906ecc-35e9-4878-b77a-ee50662328b6)
---

+ Check the port

```
rpcinfo -p | grep nfs
```
