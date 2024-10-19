# LVM-Configuration-and-Management
<h2>Description</h2>
In this project we will create a logical volume and filesystem and configure it
<br />
<br/>  LVM architecture: <br/>
<img src="https://github.com/user-attachments/assets/efb220bf-185b-4211-8cf7-01338bb4d52b"/>


<h2>Languages and Utilities Used</h2>

Bash

<h2>Environments Used </h2>

- <b>CentOS Linux release 8.5.2111
 10 </b>

<h2>Project walk-through:</h2>
<br/>
<p align="center">

### **Prerequisites**  
- At least 2.5GB RAM and 10GB disk space.
- Add [Hard Disk to Virtual Machine](https://computingforgeeks.com/add-extra-hard-disk-to-virtualbox-vm/).  
- Root or sudo privileges to create and manage physical volumes, volume groups, and logical volumes. 

 ##  Step 1: Create a 500M partition on /dev/sdb

```bash
# Create a 500M partition on /dev/sdb
fdisk /dev/sdb
# new partition 
n
# primary partition
p
# partition number
1 or enter 
# default for first sector
press enter
# set size to 500M
+500M
# change partition type
t
# Select LVM type
8e
# print partition table to verify
p
# write changes
w
# Confirm
lsblk
```

<img src="https://github.com/user-attachments/assets/4efd3e6a-6ec7-4223-95f5-0f92c2e3d694"/> 
<img src="https://github.com/user-attachments/assets/4493ab23-d1db-4c59-8dbb-c289180e5318"/> 
<img src="https://github.com/user-attachments/assets/957d8097-8808-48bd-a729-def31ea701af"/> 

## Step 2: Update kernel about changes (if warning appears)

```Bash
# To force the new partition table
partprobe /dev/sdb
```

## Step 3: Identify the partition as a physical volume

```Bash
# Identify the sdb1 partition as a PV
pvcreate /dev/sdb1
```

<img src="https://github.com/user-attachments/assets/417662c3-b53c-445d-9ad5-8ab14521a023"/>















