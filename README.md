# Azure Corporate Network Infrastructure and Security Lab

**Project by Samuel Gebu**

## Project Overview

As part of my journey toward becoming an Azure Administrator and Cloud Engineer, I decided to build a corporate network environment in Microsoft Azure.

My goal was to understand how organizations deploy virtual machines, separate network resources, control traffic between servers, and securely manage their infrastructure.

Rather than focusing only on theory, I wanted hands-on experience configuring and troubleshooting a working cloud network.

## Project Objectives

- Build a corporate virtual network in Microsoft Azure.
- Separate infrastructure into Management, Server, Application, and Database subnets.
- Deploy and manage Windows Server virtual machines.
- Configure Network Security Groups (NSGs).
- Restrict unnecessary communication between subnets.
- Set up secure administrative access.
- Deploy an IIS web server.
- Test network connectivity using PowerShell.

## Technologies Used

- Microsoft Azure
- Azure Virtual Network
- Azure Virtual Machines
- Network Security Groups
- Windows Server 2025
- Remote Desktop Protocol (RDP)
- Internet Information Services (IIS)
- Windows PowerShell

## Network Architecture

I created a virtual network called `VNET-CORP-LAB` and divided it into four subnets.

| Subnet | IP Address Range | Purpose |
|---|---|---|
| Management | 10.20.1.0/24 | Administrative access |
| Servers | 10.20.2.0/24 | Server infrastructure |
| Application | 10.20.3.0/24 | Application hosting |
| Database | 10.20.4.0/24 | Database infrastructure |

The environment includes four Windows Server virtual machines:

- `VM-MGMT-01`
- `VM-SERVER-01`
- `VM-APP-01`
- `VM-DB-01`

## Implementation

### 1. Virtual Network Configuration

I started by creating a resource group and an Azure Virtual Network.

I then configured four separate subnets to organize the environment according to the roles of the servers.

### 2. Virtual Machine Deployment

I deployed Windows Server virtual machines into their respective subnets.

This gave me practical experience with Azure VM deployment, network interfaces, private IP addressing, and virtual machine administration.

### 3. Network Security

I configured Network Security Groups to control inbound traffic.

The security rules were designed to allow only necessary connections, including RDP administration, HTTP traffic, and planned SQL Server communication.

### 4. Remote Desktop Configuration

One of the challenges I encountered was connecting to the Management VM through Remote Desktop.

I investigated the connection using PowerShell, reviewed the NSG configuration, reset the administrator credentials, and repaired the RDP configuration.

After troubleshooting, I successfully connected to the Management VM and used it to administer other servers.

### 5. IIS Web Server Deployment

I installed Internet Information Services on the Application VM.

To verify the deployment, I opened the IIS welcome page from the Management VM using the Application VM's private IP address.

This confirmed that the web server was accessible over the configured network.

### 6. Network Connectivity Testing

I used the PowerShell `Test-NetConnection` command to check communication between virtual machines.

The tests included:

- Management to Server over RDP: Successful.
- Management to Application over RDP: Blocked as intended.
- Management to Application over HTTP: Successful.

These tests helped me understand how network security rules affect communication between different subnets.

## Challenges and Lessons Learned

This project helped me understand that deploying cloud infrastructure involves more than creating resources.

I learned how important it is to configure network security correctly, troubleshoot connectivity issues, and test whether systems can communicate as intended.

The Remote Desktop troubleshooting was especially valuable because it required me to investigate different possible causes rather than assume the problem was with the virtual machine itself.

## Current Progress

The virtual network, subnet segmentation, Windows Server deployment, NSG configuration, and IIS connectivity testing have been completed.

The next stage involves completing SQL Server configuration and validating database connectivity from the Application subnet.

## Conclusion

Building this environment has strengthened my understanding of Azure networking, Windows Server administration, and cloud security.

I plan to continue improving the lab as I develop my skills in Azure Administration, Cloud Networking, and Cloud Engineering.

**Author: Samuel Gebu**
