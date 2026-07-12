# Smart-Hospital-Infrastructure-on-Microsoft-Azure
# Smart Hospital Infrastructure on Microsoft Azure

## Project Overview

This project demonstrates the deployment and management of a Smart Hospital Infrastructure using Microsoft Azure. The solution includes networking, virtual machines, storage, security, monitoring, backup, and DNS management.

---

## Resource Group

![Resource Group](screenshots/Resource%20Group.png)

Created Resource Group **RG-HealthcarePlus** in Central India.

---

## Virtual Network and Subnets

![VNet](screenshots/VNet%20(1).png)
![VNet](screenshots/VNet%20(2).png)
![VNet](screenshots/VNet%20(3).png)

Configured:
- VNet-Healthcare
- default subnet
- appSubnet
- managementSubnet
- AzureBastionSubnet

---

## Users and RBAC

![Users&RBAC](screenshots/Users%26RBAC%20%20(1).png)
![Users&RBAC](screenshots/Users%26RBAC%20%20(2).png)
![Users&RBAC](screenshots/Users%26RBAC%20%20(3).png)

Created:
- doctors
- frontoffice
- management

Assigned users and roles.

---

## Network Security Group

![NSG](screenshots/NSG%20(1).png)
![NSG](screenshots/NSG%20(2).png)
![NSG](screenshots/NSG%20(3).png)

Configured inbound rules:
- HTTP (80)
- HTTPS (443)
- RDP (3389)
- SSH (22)

---

## Windows Server IIS Website

![IIS](screenshots/IIS%20(1).png)
![IIS](screenshots/IIS%20(2).png)
![IIS](screenshots/IIS%20(3).png)
![IIS](screenshots/IIS%20(4).png)
![IIS](screenshots/IIS%20(5).png)
![IIS](screenshots/IIS%20(6).png)
![IIS](screenshots/IIS%20(7).png)



Hosted HealthcarePlus Hospital website using IIS.

---

## Ubuntu Linux Nginx Portal

![Nginx](screenshots/Nginx%20(1).png)
![Nginx](screenshots/Nginx%20(2).png)
![Nginx](screenshots/Nginx%20(3).png)
![Nginx](screenshots/Nginx%20(4).png)
![Nginx](screenshots/Nginx%20(5).png)

Hosted internal hospital portal using Nginx.

---

## Azure Storage Account

![Storage](screenshots/Storage%20(1).png)
![Storage](screenshots/Storage%20(2).png)
![Storage](screenshots/Storage%20(3).png)
![Storage](screenshots/Storage%20(4).png)
![Storage](screenshots/Storage%20(5).png)
![Storage](screenshots/Storage%20(6).png)


Created:
- documents
- reports
- logs
- images

containers for hospital data.

---

## Azure File Share

![File Share](screenshots/FileShare%20(1).png)
![File Share](screenshots/FileShare%20(2).png)
![File Share](screenshots/FileShare%20(3).png)
![File Share](screenshots/FileShare%20(4).png)

Created:
- hospitalshare
- patientrecords

---

## Azure Key Vault

![Key Vault](screenshots/KeyVault%20(1).png)
![Key Vault](screenshots/KeyVault%20(2).png)
![Key Vault](screenshots/KeyVault%20(3).png) 
![Key Vault](screenshots/KeyVault%20(4).png)
![Key Vault](screenshots/KeyVault%20(5).png)
![Key Vault](screenshots/KeyVault%20(6).png)

Stored:
- DbPassword
- StorageKey

---

## Azure DNS

![DNS](screenshots/DNS%20(1).png)
![DNS](screenshots/DNS%20(2).png)
![DNS](screenshots/DNS%20(3).png)
![DNS](screenshots/DNS%20(4).png)
![DNS](screenshots/DNS%20(5).png)

changing the nameserver to Azure from domain provider

![DNS](screenshots/DNS%20(6).png)

Configured:
- vp-cloudelab.xyz
- www record
- portal record

---

## Azure Monitor and Log Analytics

![Monitor](screenshots/Monitor%20(1).png)
![Monitor](screenshots/Monitor%20(2).png)
![Monitor](screenshots/Monitor%20(3).png)
![Monitor](screenshots/Monitor%20(4).png)
![Monitor](screenshots/Monitor%20(5).png)
![Monitor](screenshots/Monitor%20(6).png)
![Monitor](screenshots/Monitor%20(7).png)

Configured:
- Log Analytics Workspace
- Monitoring
- Alerts

---

## Recovery Services Vault and Backup

![Backup](screenshots/Backup%20(1).png)
![Backup](screenshots/Backup%20(2).png)
![Backup](screenshots/Backup%20(3).png)
![Backup](screenshots/Backup%20(4).png)
![Backup](screenshots/Backup%20(5).png)
![Backup](screenshots/Backup%20(6).png)

Configured VM backup and recovery.

![Backuping](screenshots/Backuping%20(1).png)
![Backuping](screenshots/Backuping%20(2).png)
![Backuping](screenshots/Backuping%20(3).png)

---

## Cost Management

![Cost Management](screenshots/CostManagement.png)

Configured Azure Budget and cost monitoring.

---

## Conclusion

Successfully deployed and managed a Smart Hospital Infrastructure on Microsoft Azure using:

- Azure Virtual Network
- Windows Server IIS
- Ubuntu Nginx
- Azure Storage
- Azure File Share
- Azure Key Vault
- Azure DNS
- Azure Monitor
- Recovery Services Vault
- Cost Management

This project demonstrates Azure administration, security, monitoring, backup, and web hosting capabilities.
