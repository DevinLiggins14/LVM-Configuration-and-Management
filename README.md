# LVM-Configuration-and-Management
<h2>Description</h2>
In this project we will create a logical volume and filesystem and configure it
<br />
<br/>  LVM architecture: <br/>
<img src="https://github.com/user-attachments/assets/efb220bf-185b-4211-8cf7-01338bb4d52b"/>


<h2>Languages and Utilities Used</h2>

Bash

<h2>Environments Used </h2>

- <b>CentOS Stream release 9 release 5.14.0-503.el9.x86_64 </b>

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


## Step 4: Create the volume group 

```Bash
# Create VG vg99
vgcreate vg99 /dev/sdb1
```

<img src="https://github.com/user-attachments/assets/f2ef23b3-a6e5-4257-9645-3304d4040b6d"/>

## Step 5: Create a logical volume

```Bash
# Create a logical volume called data using 200M of vg99
lvcreate -n data -L 200M vg99
```

<img src="https://github.com/user-attachments/assets/31bc0fee-1464-4766-808c-d56d7fb91b9a"/>
<br/> Confirm: <br/>
<img src="https://github.com/user-attachments/assets/eee8f526-570a-4ba6-81bf-24024d296a55"/>

## Step 6: Create an ext4 filesystem on the logical volume

```Bash
# Create an ext4 FS on the data LV
mkfs.ext4 /dev/mapper/vg99-data
```

<img src="https://github.com/user-attachments/assets/6990cd10-99f8-4b7e-8b64-23c841d26c1c"/>

## Step 7: Create a mount point and mount the filesystem

```Bash
# Create and mount the ext4 FS on /data
mkdir /data
mount /dev/mapper/vg99-data /data
```

## Step 8: Verify and unmount the filesystem

```Bash
# Verify the ext4 FS mounted on /data and unmount
df -hT
umount /data
```

<img src="https://github.com/user-attachments/assets/22b28559-2e4a-484d-a16c-f1ef8dbc56a1"/>
<img src="https://github.com/user-attachments/assets/acef934e-b1a2-4b5c-b74b-2937f6e4bddc"/>











