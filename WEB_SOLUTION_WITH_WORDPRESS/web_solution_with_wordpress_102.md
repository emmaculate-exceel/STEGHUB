# Web solution with wordpress 102


#### Preparing a web server
---
![Screenshot_2024-10-09_08_21_23](https://github.com/user-attachments/assets/ef8ad1db-ce96-4390-b4bf-3a7a1ca4b327)
---

+ Launch an ec2 instance that is to be used as a web server

+ Create volumes for the instance and attach them to the instance

---
![disk check](https://github.com/user-attachments/assets/71d3261f-42ab-4781-a0e7-071362cd7008)
![disk part](https://github.com/user-attachments/assets/841a181e-2700-4ee0-bcea-048805dbad5b)
![disk partition](https://github.com/user-attachments/assets/8a23ccea-a4a7-4e40-9e9d-5c1083b7e482)
---

+ Open the terminal and start the configuration for the instance

+ Use lsblk command to inspect what device is attached to the server
```
lsblk # inspect device on the machine
df -h # inspect all mount devices
sudo gdisk /dev/nvme*n* # to initialize a partition on a non-volatile memory express ssd storage type
lsblk # inspect the new partition to see if partition works as expected
sudo yum install lvm2 # install lvm2 to check available partition
```

---
![physical volume](https://github.com/user-attachments/assets/2e53c13e-ea28-4e30-92ad-0639f42002bb)

---

+ Marking each of the disk as a physical volume

```
sudo pvcreate /dev/nvme1n1 # creating a physical volume for partition 1
sudo pvcreate /dev/nvme2n1 # creating a physical volume for partition 2
sudo pvcreate /dev/nvme3n1 # creating a physical volume for partition 3
```
---
![volume group](https://github.com/user-attachments/assets/11ea07cc-ba1a-489c-830c-33c2b9ad1ae8)
---

+ Adding the entire partition as one volume group

```
sudo vgcreate webdata-vg /dev/nvme1n1 /dev/nvme2n1 /dev/nvme3n1 # for all volumes at a time
```
---
![logical volume](https://github.com/user-attachments/assets/404a279a-17c9-4258-808f-a817caa70345)

---

+ Now we're using the lvcreate to create 2 logical drives for the machine

```
sudo lvcreate -n app-lv -L 14G webdata-vg # create 1 logical drives from webdata-vg
sudo lvcreate -n logs-lv -L 14G webdata-vg # create 2 logical drives from webdata-vg
```

---
![ volume group display for the disk](https://github.com/user-attachments/assets/91717206-1990-4b88-8e85-5ac5bee3b1ca)
![ new volume disk space ](https://github.com/user-attachments/assets/52865ca9-d5eb-4de8-967c-85f196c16a5a)
---

+ Verify the entire disk setup

```
sudo vgdisplay -v #view complete setup - VG, PV, and LV
sudo lsblk
```
---
![ formating logical volumes ](https://github.com/user-attachments/assets/8c1e1aa2-544a-4c05-9883-328860544211)
---

+ Formating logical volumes with ext4 filesystem

```
sudo mkfs -t ext4 /dev/webdata-vg/apps-lv
sudo mkfs -t ext4 /dev/webdata-vg/logs-lv
```
---
![ creating dirs for file system](https://github.com/user-attachments/assets/ad760f8e-2c6d-487b-8cd7-593f84288f88)
![ creating backups](https://github.com/user-attachments/assets/e67fd39a-2eba-4878-8b9e-c9f9d07056c9)
---

+ Create dirs for /var/www/html to store website files

+ Create dirs for logs /home/recovery/logs to store backups

+ Create dirs for Mount
```
sudo mount /dev/webdata-vg/apps-lv /var/www/html/ # Mount drives
sudo rysync -av /var/log  /home/recovery/logs/
```
---

![ mount all volumes](https://github.com/user-attachments/assets/4e1a2083-bd2e-4fa4-a005-1e36a0522349)
---

+ Mount all volumes
```
sudo mount /dev/webdata-vg/logs-lv /var/log

## then restore the log file using the below command

sudo rsync -av /home/recovery/logs /var/log
```

---
![fstab file](https://github.com/user-attachments/assets/392ecd47-46b2-4ef0-81bc-7d6314558b58)

---

+ Update the fstab file

+ edit fstab file 
```
sudo blkid 

sudo vi /etc/fstab

UUID=d0be04e8-fc37-4928-af70-fc3d6595ef71       /       xfs     defaults        0       0

# mounts for wordpress server

UUID=1efbb90a-1b78-4295-b134-79dd7a9f57d6       /var/www/html ext4 defaults     0       0

UUID=ed5272a5-5a30-49bb-89fe-5f73aa336a7b       /var/log ext4   defaults        0       0

UUID=a2e9d044-9192-497f-a8c6-27aa7940de18       /boot   xfs     defaults        0       0
UUID=7B77-95E7  /boot/efi       vfat    defaults,uid=0,gid=0,umask=077,shortname=winnt  0       2
```

---
![test configuration file](https://github.com/user-attachments/assets/b7631be9-a8f8-4fbf-85f3-81329e9e5a93)

---

+ test configuration

+ Reload system configuration

```
sudo mount -a # mount all drives

sudo systemctl daemon-reload
```

---
![disk check](https://github.com/user-attachments/assets/a29f432b-e9ae-488d-92ec-799508a23b2a)
---


+ check setup
```
df -h # check disk file
```

+ current disk space
