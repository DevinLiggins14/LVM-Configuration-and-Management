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

 ##  Step 1: Create a 500M partition on /dev/sdb

### **Prerequisites**  
- At least 2GB RAM and 10GB disk space.
- Add [Hard Disk to Virtual Machine](https://computingforgeeks.com/add-extra-hard-disk-to-virtualbox-vm/).  
- Root or sudo privileges to create and manage physical volumes, volume groups, and logical volumes. 


```bash
# Create a resource group
az group create --name aks-demo-rg --location eastus

# Create the AKS cluster
az aks create --resource-group aks-demo-rg --name aks-demo --location eastus2 --node-count 2 --enable-managed-identity --generate-ssh-keys
```


