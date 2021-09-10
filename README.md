# Exam AZ-140 - Microsoft Azure Virtual Desktop Specialty

Study guide for Microsoft Azure Exam AZ-140. Configuring and Operating Microsoft Azure Virtual Desktop.

## Overview

<https://docs.microsoft.com/en-us/learn/certifications/azure-virtual-desktop-specialty/>

Target audience: Microsoft Azure administrators with subject matter expertise in planning, delivering, and managing virtual desktop experiences and remote apps, for any device, on Azure.

Candidates for this certification should have experience in Azure technologies, including virtualization, networking, identity, storage, backups, resilience, and disaster recovery. They should understand on-premises virtual desktop infrastructure technologies as they relate to migrating to Azure Virtual Desktop. These professionals use the Azure portal and Azure Resource Manager (ARM), PowerShell and Azure Command-Line Interface.

### Preparations

- Online training (Free) <https://docs.microsoft.com/en-us/learn/certifications/azure-virtual-desktop-specialty/?tab=tab-learning-paths>

- Instructor-led (Paid) <https://docs.microsoft.com/en-us/learn/certifications/azure-virtual-desktop-specialty/?tab=tab-instructor-led>

- Another Study Guide #1 - <https://ravikirans.com/az-140-azure-exam-study-guide/>

- Another Study Guide #2 - <https://charbelnemnom.com/az-140-exam-study-guide-configuring-and-operating-windows-virtual-desktop-on-microsoft-azure/>

- Another Study Guide #3 - <https://www.thomasmaurer.ch/2021/02/az-140-study-guide-windows-virtual-desktop-on-microsoft-azure/>

- Another Study Guide #4 (Video series) - <https://youtu.be/DZNc1DQxEEA>

## Skills measured and links

### Plan an Azure Virtual Desktop Architecture (10-15%)

#### Design the Azure Virtual Desktop architecture

- assess existing physical and virtual desktop environments
  - Azure Virtual Desktop assessment - <https://docs.microsoft.com/en-us/azure/cloud-adoption-framework/scenarios/wvd/migrate-assess>
    - Use Movere as your data collection tool to have the data you need to develop personas and answer these questions by using data in Azure Migrate
    - Lakeside Software, is integrated with Azure Migrate within the virtual desktop infrastructure migration goals section. The vendor can help you map out a plan for Azure Virtual Desktop deployment, including personas, host pools, applications, and user profiles.
    - Use User personas - distinct personas will be required to support all of the users in migration scenario Defining personas will come as a result of bucketing users based on the following criteria: Personal pools, Density, Performance, GPU, Region, Business unit, User Count, Sessions count
    - Both Movere and Lakeside scans of the current on-premises environment can provide data about the applications that are run on end-user desktops. By using that data, you can create a list of all applications required per each persona.
    - Do any applications need to be installed for the persona to use this desktop? Unless the persona uses 100 percent web-based software as a service applications, you'll likely need to configure a custom master VHD image for each persona, with the required applications installed on the master image.
    - Does this persona need Microsoft 365 applications? If so, you'll need to select an image from the gallery that has Microsoft 365 apps included or add Microsoft 365 to a customized master VHD image.
    - Is this application compatible with Windows 10 Enterprise multi-session? If an application isn't compatible, a personal pool might be required to run the custom VHD image. For assistance with application and Azure Virtual Desktop compatibility issues, see the desktop application assure service.
    - Are mission-critical applications likely to suffer from latency between the Azure Virtual Desktop instance and any back-end systems? If so, you might want to consider migrating the back-end systems that support the application to Azure.
  - Virtual machine sizing guidelines - <https://docs.microsoft.com/en-us/windows-server/remote/remote-desktop-services/virtual-machine-recs>
    - Multi-session - All VMs should have more than two cores, VMs should not have more than 32 cores. Recommended VM size is between 4 vCPUs and 24 vCPUs. We don't recommend using 2 cores or 32 or more cores for standard and larger environments.
    - Single-session- at least two physical CPU cores per VM (typically four vCPUs with hyperthreading).
    - use Premium SSD storage in your OS disk for production workloads
    - B-series burstable VMs are a good choice for users who don't always need maximum CPU performance.

- assess network capacity and speed requirements for Azure Virtual Desktop
  - Network guidelines - <https://docs.microsoft.com/en-us/windows-server/remote/remote-desktop-services/network-guidance>
  - Workload type - Recommended bandwidth: Light 1.5 Mbps, Medium 3 Mbps, Heavy 5 Mbps, Power 15 Mbps
  - Workload type - Recommended bandwidth: About 1024 × 768 px 1.5 Mbps, About 1280 × 720 px 3 Mbps, About 1920 × 1080 px 5 Mbps, About 3840 × 2160 px (4K) 15 Mbps
  - Check out the Azure Virtual Desktop experience estimator, latency up to 150 ms shouldn’t impact user experience that doesn't involve rendering or video. Latencies between 150 ms and 200 ms should be fine for text processing. Latency above 200 ms may impact user experience.
    - use the tool every two to three months to make sure the optimal location hasn't changed as Azure Virtual Desktop rolls out to new areas. - <https://docs.microsoft.com/en-us/azure/virtual-desktop/connection-latency>
  - Remote Desktop Protocol (RDP) bandwidth requirements - <https://docs.microsoft.com/en-us/azure/virtual-desktop/rdp-bandwidth>
    - The best way to understand bandwidth requirements is to monitor real user connections. Monitoring can be performed by the built-in performance counters or by the network equipment.
    - there's no need to limit bandwidth utilization as limiting may affect user experience. Yet in the constrained networks you may want to limit network utilization. You can use policy-based Quality of Service (QoS) within Group Policy to set the predefined throttle rate.
  - Understanding Azure Virtual Desktop network connectivity - <https://docs.microsoft.com/en-us/azure/virtual-desktop/network-connectivity>
    - Reverse connect transport - it is using outbound connectivity to the Azure Virtual Desktop infrastructure over the HTTPS connection. On start of a session host, the Agent Loader service opens TLS 1.2 AVD broker's persistent communication channel between session host and Azure Virtual Desktop infrastructure.
  - Quality of Service (QoS) for Azure Virtual Desktop - <https://docs.microsoft.com/en-us/azure/virtual-desktop/rdp-quality-of-service-qos>
    - RDP Shortpath - allows real-time RDP traffic that's sensitive to network delays to "cut in line" in front of traffic that's less sensitive.
    If you support a large group of users experiencing any of the problems (Jitter , Packet loss, Delayed round-trip time), you probably need to implement QoS. To address quality issues, we recommend that you first use QoS, then add bandwidth only where necessary. For QoS to be effective, you must apply consistent QoS settings throughout your organization. Any part of the path that fails to support your QoS priorities can degrade the quality RDP session.

- recommend an operating system for an Azure Virtual Desktop implementation
  - Supported virtual machine OS images - <https://docs.microsoft.com/en-us/azure/virtual-desktop/overview#supported-virtual-machine-os-images>
  - x64 operating system images:
    - Windows 10 Enterprise multi-session
    - Windows 10 Enterprise
    - Windows 7 Enterprise
    - Windows Server 2019
    - Windows Server 2016
    - Windows Server 2012 R2

- plan and configure name resolution for Active Directory (AD) and Azure Active Directory Domain Services (Azure AD DS)
  - Configure Active Directory, Azure AD DNS - <https://www.youtube.com/watch?v=kfOYWFpoglQ>
  - Understand, AD Name Resolution, DNS, Configure Azure DNS, Azure AD Domain Services, DNS Conditional Forwarders, AVD DNS Email Discovery
  - Multiple forests with AD DS and Azure AD - <https://docs.microsoft.com/en-us/azure/architecture/example-scenario/wvd/multi-forest>
  - Multiple forests with AD DS, Azure AD, and Azure AD DS - <https://docs.microsoft.com/en-us/azure/architecture/example-scenario/wvd/multi-forest-azure-managed>

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
