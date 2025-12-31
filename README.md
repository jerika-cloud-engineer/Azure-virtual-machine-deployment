# Azure-virtual-machine-deployment
This project demonstrates deploying a virtual machine on Azure using the CLI, including setting up a VNet, NSG, and SSH access.
# Azure VM Deployment (CLI Project)

This project demonstrates how I used the Azure CLI in the Cloud Shell to create and configure a virtual machine, network security group (NSG), and virtual network (VNet).

## 🔧 Tools Used
- Azure CLI
- Azure Portal
- Cloud Shell
- Bash scripting

## 🧠 Project Overview

- Created a **resource group** called `silkcake-group2`
- Created a **virtual network (VNet)** with subnet
- Created a **network security group (NSG)** with an SSH rule (port 22)
- Deployed a **Ubuntu 2204 virtual machine** named `silkcake-vm`
- Assigned a **public IP** and verified it was running

## 💻 Azure CLI Commands Used

```bash
az vm create \
  --resource-group silkcake-group2 \
  --name silkcake-vm \
  --image Ubuntu2204 \
  --vnet-name silkcake-vnet \
  --subnet silkcake-subnet \
  --nsg nsg-silkcake \
  --admin-username jerikaadmin \
  --authentication-type password \
  --admin-password "Bluecake777$" \
  --public-ip-sku Standard \
  --size Standard_D2s_v3 \
  --location westus

az network nsg rule create \
  --resource-group silkcake-group2 \
  --nsg-name nsg-silkcake \
  --name allow-ssh \
  --protocol Tcp \
  --direction Inbound \
  --priority 1000 \
  --source-address-prefixes "*" \
  --source-port-ranges "*" \
  --destination-port-ranges 22 \
  --access Allow

## 📚 What I Learned
- How to troubleshoot image size and location issues
- How to use the `az` CLI tool to fully deploy infrastructure
- Importance of security group rules when enabling SSH access
- How to verify a VM is running via CLI and view IP addresses

### Final CLI Command
![Final CLI](./screenshots/final-cli-command.PNG)

### Azure Portal VM Screenshot
![Portal Screenshot](./screenshots/azure-portal-vm.JPG)
