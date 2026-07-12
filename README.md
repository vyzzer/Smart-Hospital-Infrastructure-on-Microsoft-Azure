# Smart-Hospital-Infrastructure-on-Microsoft-Azure
# Smart Hospital Infrastructure on Microsoft Azure

## Project Overview

This project demonstrates the deployment and management of a Smart Hospital Infrastructure using Microsoft Azure. The solution includes networking, virtual machines, storage, security, monitoring, backup, and DNS management.

---

## Resource Group

![Resource%20Group](Screenshot/Resource%20Group.png)

Created Resource Group **RG-HealthcarePlus** in Central India.

---

## Virtual Network and Subnets

![VNet](Screenshot/VNet%20(1).png)

Configured:
- VNet-Healthcare
- default subnet
- appSubnet
- managementSubnet
- AzureBastionSubnet

---

## Users and RBAC

![Users & RBAC](Screenshot/Users%26RBAC%20(1).png)

Created:
- doctors
- frontoffice
- management

Assigned users and roles.

---

## Network Security Group

![NSG](Screenshot/NSG%20(1).png)

Configured inbound rules:
- HTTP (80)
- HTTPS (443)
- RDP (3389)
- SSH (22)

---

## Windows Server IIS Website

![IIS](Screenshot/IIS%20(1).png)

Hosted HealthcarePlus Hospital website using IIS.

---

## Ubuntu Linux Nginx Portal

![Nginx](Screenshot/Nginx%20(1).png)

Hosted internal hospital portal using Nginx.

---

## Azure Storage Account

![Storage](Screenshot/Storage%20(1).png)

Created:
- documents
- reports
- logs
- images

containers for hospital data.

---

## Azure File Share

![File Share](Screenshot/FileShare%20(1).png)

Created:
- hospitalshare
- patientrecords

---

## Azure Key Vault

![Key Vault](Screenshot/KeyVault%20(1).png)

Stored:
- DbPassword
- StorageKey

---

## Azure DNS

![DNS](Screenshot/DNS%20(1).png)

Configured:
- vp-cloudelab.xyz
- www record
- portal record

---

## Azure Monitor and Log Analytics

![Monitor](Screenshot/Monitor%20(1).png)

Configured:
- Log Analytics Workspace
- Monitoring
- Alerts

---

## Recovery Services Vault and Backup

![Backup](Screenshot/Backup%20(1).png)

Configured VM backup and recovery.

---

## Cost Management

![Cost Management](Screenshot/CostManagement.png)

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
