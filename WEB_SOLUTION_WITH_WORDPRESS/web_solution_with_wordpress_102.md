# Web solution with wordpress 102


#### Preparing a web server

---





---

+ Launch an ec2 instance that is to be used as a web server

+ Create volumes for the instance and attach them to the instance

---




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





---

+ Marking each of the disk as a physical volume

```
sudo pvcreate /dev/nvme1n1 # creating a physical volume for partition 1
sudo pvcreate /dev/nvme2n1 # creating a physical volume for partition 2
sudo pvcreate /dev/nvme3n1 # creating a physical volume for partition 3
```
---



---

+ Adding the entire partition as one volume group

```
sudo vgcreate webdata-vg /dev/nvme1n1 /dev/nvme2n1 /dev/nvme3n1 # for all volumes at a time
```
---




---

+ Now we're using the lvcreate to create 2 logical drives for the machine

```
sudo lvcreate -n app-lv -L 14G webdata-vg # create 1 logical drives from webdata-vg
sudo lvcreate -n logs-lv -L 14G webdata-vg # create 2 logical drives from webdata-vg
```

---



---


+ Verify the entire disk setup

```
sudo vgdisplay -v #view complete setup - VG, PV, and LV
sudo lsblk
```
---



---

+ Formating logical volumes with ext4 filesystem

```
sudo mkfs -t ext4 /dev/webdata-vg/apps-lv
sudo mkfs -t ext4 /dev/webdata-vg/logs-lv
```
---



---

+ Create dirs for /var/www/html to store website files

+ Create dirs for logs /home/recovery/logs to store backups

+ Create dirs for Mount
```
sudo mount /dev/webdata-vg/apps-lv /var/www/html/ # Mount drives
sudo rysync -av /var/log  /home/recovery/logs/
```
---



---

+ Mount all volumes
```
sudo mount /dev/webdata-vg/logs-lv /var/log

## then restore the log file using the below command

sudo rsync -av /home/recovery/logs /var/log
```

---




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



---

+ test configuration

+ Reload system configuration

```
sudo mount -a # mount all drives

sudo systemctl daemon-reload
```

---




---


+ check setup
```
df -h # check disk file
```

+ current disk space
