# Exam AZ-140 - Microsoft Azure Virtual Desktop Specialty

Study guide for Microsoft Azure Exam AZ-140. Configuring and Operating Microsoft Azure Virtual Desktop.

## Overview

<https://docs.microsoft.com/en-us/learn/certifications/azure-virtual-desktop-specialty/>

Target audience: Microsoft Azure administrators with subject matter expertise in planning, delivering, and managing virtual desktop experiences and remote apps, for any device, on Azure.

Candidates for this certification should have experience in Azure technologies, including virtualization, networking, identity, storage, backups, resilience, and disaster recovery. They should understand on-premises virtual desktop infrastructure technologies as they relate to migrating to Azure Virtual Desktop. These professionals use the Azure portal and Azure Resource Manager (ARM), PowerShell and Azure Command-Line Interface.

### Preparations

- Online training (Free) <https://docs.microsoft.com/en-us/learn/certifications/azure-virtual-desktop-specialty/?tab=tab-learning-paths>

- Instructor-led (Paid) <https://docs.microsoft.com/en-us/learn/certifications/azure-virtual-desktop-specialty/?tab=tab-instructor-led>

## Skills measured and links

### Plan an Azure Virtual Desktop Architecture (10-15%)

#### Design the Azure Virtual Desktop architecture

- assess existing physical and virtual desktop environments
- assess network capacity and speed requirements for Azure Virtual Desktop
- recommend an operating system for an Azure Virtual Desktop implementation 
- plan and configure name resolution for Active Directory (AD) and Azure Active Directory 

#### Domain Services (Azure AD DS)

- plan a host pools architecture
- recommend resource groups, subscriptions, and management groups
- configure a location for the Azure Virtual Desktop metadata
- calculate and recommend a configuration for performance requirements
- calculate and recommend a configuration for Azure Virtual Machine capacity requirements

#### Design for user identities and profiles

- select an appropriate licensing model for Azure Virtual Desktop based on requirements
- recommend an appropriate storage solution (including Azure NetApp Files versus Azure Files)
- plan for Azure Virtual Desktop client deployment
- plan for user profiles
- recommend a solution for network connectivity
- plan for Azure AD Connect for user identities

### Implement an Azure Virtual Desktop Infrastructure (25-30%)

#### Implement and manage networking for Azure Virtual Desktop

- implement Azure virtual network connectivity
- manage connectivity to the internet and on-premises networks
- implement and manage network security
- manage Azure Virtual Desktop session hosts by using Azure Bastion
- monitor and troubleshoot network connectivity

#### Implement and manage storage for Azure Virtual Desktop

- configure storage for FSLogix components
- configure storage accounts
- configure disks
- create file shares

#### Create and configure host pools and session hosts

- create a host pool by using the Azure portal
- automate creation of Azure Virtual Desktop host and host pools by using PowerShell, 

#### Command-Line Interface (CLI), and Azure Resource Manager templates

- create a host pool based on Windows client or Windows Server session hosts
- configure host pool settings
- manage licensing for session hosts that run Windows client or Windows Server
- assign users to host pools
- apply OS and application updates to a running Azure Virtual Desktop host
- apply security and compliance settings to session hosts

#### Create and manage session host images

- create a gold image
- modify a session host image
- install language packs in Azure Virtual Desktop
- deploy a session host by using a custom image
- plan for image update and management
- create and use a Shared Image Gallery
- troubleshoot OS issues related to Azure Virtual Desktop

### Manage Access and Security (10-15%)

#### Manage access

- plan and implement Azure roles and role-based access control (RBAC) for Azure Virtual Desktop
- manage local roles, groups and rights assignment on Azure Virtual Desktop session hosts
- configure user restrictions by using Azure AD group policies and AD policies

#### Manage security

- plan and implement Conditional Access policies for connections to Azure Virtual Desktop
- plan and implement multifactor authentication in Azure Virtual Desktop
- manage security by using Azure Security Center
- configure Microsoft Defender Antivirus for session hosts

### Manage User Environments and Apps (20-25%)

#### Implement and manage FSLogix

- plan for FSLogix
- install and configure FSLogix
- configure Profile Containers
- configure Cloud Cache
- migrate user profiles to FSLogix

#### Configure user experience settings

- configure Universal Print
- configure user settings through group policies and Endpoint Manager policies
- configure persistent and non-persistent desktop environments
- configure Remote Desktop Protocol (RDP) properties on a host pool
- configure session timeout properties
- troubleshoot user profile issues
- troubleshoot Azure Virtual Desktop clients

#### Install and configure apps on a session host

- configure dynamic application delivery by using MSIX App Attach
- implement application masking
- deploy an application as a RemoteApp
- implement and manage OneDrive for Business for a multi-session environment
- implement and manage Microsoft Teams AV Redirect
- implement and manage browsers and internet access for Azure Virtual Desktop sessions
- create and configure an application group
- troubleshoot application issues related to Azure Virtual Desktop

### Monitor and Maintain an Azure Virtual Desktop Infrastructure (20-25%)

#### Plan and implement business continuity and disaster recovery

- plan and implement a disaster recovery plan for Azure Virtual Desktop
- design a backup strategy for Azure Virtual Desktop
- configure backup and restore for FSLogix user profiles, personal virtual desktop infrastructures (VDIs), and golden images

#### Automate Azure Virtual Desktop management tasks

- configure automation for Azure Virtual Desktop
- automate management of host pools, session hosts, and user sessions by using 

#### PowerShell and Azure Command-Line Interface (CLI) 

- implement autoscaling in host pools

#### Monitor and manage performance and health

- monitor Azure Virtual Desktop by using Azure Monitor
- monitor Azure Virtual Desktop by using Azure Advisor
- customize Azure Monitor workbooks for Azure Virtual Desktop monitoring
- optimize session host capacity and performance
- manage active sessions and application groups
- monitor and optimize autoscaling results
