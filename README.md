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

 ##  Step 1: Create AKS Cluster

### **Prerequisites**  
- Download and Install [Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli).  
- Setup and configure Azure CLI using the `az login` command.  
- Install and configure `kubectl` as mentioned [here](https://kubernetes.io/docs/tasks/tools/install-kubectl/).

```bash
# Create a resource group
az group create --name aks-demo-rg --location eastus

# Create the AKS cluster
az aks create --resource-group aks-demo-rg --name aks-demo --location eastus2 --node-count 2 --enable-managed-identity --generate-ssh-keys
```
