# Virtual Machine Configuration and Website Deployment

> **Evidence note:** The screenshots in this guide come from an earlier Azure VM lab. They illustrate the same technologies used in the Smart Hospital project, but they are **not screenshots of the current deployment**. Commands shown as examples are reproducible instructions, not a claim that every command was executed during the original lab.

## 1. Windows Server: install and verify IIS

The historical screenshots show the Windows VM `VMWebServer01` accessed through Azure Bastion. Server Manager was opened, **Add Roles and Features** was selected, and the **Web Server (IIS)** role with **IIS Management Console** was chosen. The installation wizard displayed a **pending restart warning**; a restart should be completed when required before proceeding.

### GUI procedure

1. Connect to the Windows Server VM through an approved management path (Azure Bastion was used in the earlier lab).
2. Open **Server Manager → Manage → Add Roles and Features**.
3. Select **Role-based or feature-based installation** and the target VM.
4. Select **Web Server (IIS)** and accept the required management tools.
5. Review the selected role services, click **Install**, and restart if prompted.
6. Test the site locally at `http://localhost` or through the VM's intended HTTP endpoint.

The earlier screenshot of the blue **Internet Information Services** welcome page confirms that the default IIS site was served successfully at the time of that test. It does **not** demonstrate that the hospital website's own files had already been deployed.

### Equivalent PowerShell commands (reference)

Run PowerShell as administrator on Windows Server:

```powershell
# Install IIS and the management console
Install-WindowsFeature -Name Web-Server -IncludeManagementTools

# Confirm IIS is installed
Get-WindowsFeature Web-Server

# Check the World Wide Web Publishing Service
Get-Service W3SVC

# Test HTTP locally
Invoke-WebRequest http://localhost -UseBasicParsing
```

### Deploy static website files (example, not verified from screenshots)

For a static HTML/CSS/JavaScript website, a common deployment approach is to place files in the IIS site's configured physical directory (often `C:\inetpub\wwwroot` for the default site). **Back up existing content first** and verify the site's actual physical path in IIS Manager.

```powershell
# Example only: copy a prepared website folder to the default IIS web root
Copy-Item -Path "C:\website-source\*" -Destination "C:\inetpub\wwwroot\" -Recurse -Force

# Check the deployed entry point
Test-Path "C:\inetpub\wwwroot\index.html"

# Test the site
Invoke-WebRequest http://localhost -UseBasicParsing
```

For a public site, configure the correct hostname binding and a valid TLS certificate for HTTPS. In Azure, permit only the required web traffic in the NSG, and restrict RDP to approved administrative access.

## 2. Ubuntu: install and verify Nginx

The historical terminal screenshots show an Ubuntu **24.04 LTS** session, an Nginx package installation, and the result of `sudo systemctl status nginx`. The status output reported **active (running)**, confirming the Nginx service was running during the earlier lab.

### Commands documented by the screenshots

```bash
# Install Nginx
sudo apt install nginx -y

# Check Nginx service status
sudo systemctl status nginx
```

### Recommended reproducible setup

```bash
sudo apt update
sudo apt install nginx -y
sudo systemctl enable --now nginx
sudo nginx -t
sudo systemctl status nginx
curl -I http://localhost
```

The terminal also displayed a **pending kernel upgrade** message. Schedule a maintenance restart if required and recheck the service after reboot.

### Deploy a static portal (example, not verified from screenshots)

The following creates a separate static website root and a basic Nginx virtual host. Replace the example folder and hostname with the actual portal configuration.

```bash
# Create a directory for portal content
sudo mkdir -p /var/www/hospital-portal

# Example: copy prepared files into the site directory
sudo cp -r /home/azureuser/portal-files/. /var/www/hospital-portal/

# Ensure Nginx can read the content
sudo chmod -R a+rX /var/www/hospital-portal

# Create a site configuration
sudo nano /etc/nginx/sites-available/hospital-portal
```

Example configuration for a **static** portal:

```nginx
server {
    listen 80;
    server_name portal.example.com;

    root /var/www/hospital-portal;
    index index.html;

    location / {
        try_files $uri $uri/ =404;
    }
}
```

Enable the site and validate the configuration:

```bash
sudo ln -s /etc/nginx/sites-available/hospital-portal /etc/nginx/sites-enabled/hospital-portal
sudo nginx -t
sudo systemctl reload nginx
curl -I -H 'Host: portal.example.com' http://localhost
```

**Important:** The hostname `portal.example.com` is a placeholder, not the project's actual DNS record. The lab's documented DNS zone is `vp-cloudelab.xyz`. If this is an internal-only portal, configure private access and do not expose it publicly. Add TLS before handling any sensitive traffic.

## 3. What the historical screenshots establish

| Evidence | Supported conclusion | Not established |
|---|---|---|
| Windows Server Manager dashboard | VM management session opened | Final website content |
| Add Roles and Features wizard | IIS role selected for installation | Every later configuration step |
| IIS welcome page | Default IIS web page served during the test | Hospital site files or HTTPS |
| Ubuntu terminal login | Ubuntu VM shell accessible | Portal content deployment |
| Nginx package output | Nginx package installation performed | Website virtual host configuration |
| `systemctl status nginx` output | Nginx service active and running | Public DNS/HTTPS or portal functionality |

## 4. How to validate the current Smart Hospital deployment

- Confirm the correct VM names, OS versions, and assigned IP addresses in the Azure portal.
- Check the configured IIS site path, bindings, and content on Windows.
- Check `sudo nginx -T`, `sudo systemctl status nginx`, and the deployed web root on Ubuntu.
- Confirm the DNS records and the HTTPS certificate configuration.
- Test connectivity from the **intended** client network.
- Record current screenshots only after rechecking the configuration.

**Security reminder:** Never publish VM passwords, secret values, connection strings, or patient information. Historical public IP addresses shown in screenshots should not be assumed to be current.
