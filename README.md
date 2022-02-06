# Exam AZ-140 - Microsoft Azure Virtual Desktop Specialty

Study guide for Microsoft Azure Exam AZ-140. Configuring and Operating Microsoft Azure Virtual Desktop.

## Overview

<https://docs.microsoft.com/en-us/learn/certifications/azure-virtual-desktop-specialty/>

Target audience: Microsoft Azure administrators with subject matter expertise in planning, delivering, and managing virtual desktop experiences and remote apps, for any device, on Azure.

Exam contains around 55 Questions.

Candidates for this certification should have experience in Azure technologies, including virtualization, networking, identity, storage, backups, resilience, and disaster recovery. They should understand on-premises virtual desktop infrastructure technologies as they relate to migrating to Azure Virtual Desktop. These professionals use the Azure portal and Azure Resource Manager (ARM), PowerShell and Azure Command-Line Interface.

### Preparations

- Online training (Free) <https://docs.microsoft.com/en-us/learn/certifications/azure-virtual-desktop-specialty/?tab=tab-learning-paths>

- Instructor-led (Paid) <https://docs.microsoft.com/en-us/learn/certifications/azure-virtual-desktop-specialty/?tab=tab-instructor-led>

- Another Study Guide #1 - <https://ravikirans.com/az-140-azure-exam-study-guide/>

- Another Study Guide #2 - <https://charbelnemnom.com/az-140-exam-study-guide-configuring-and-operating-windows-virtual-desktop-on-microsoft-azure/>

- Another Study Guide #3 - <https://www.thomasmaurer.ch/2021/02/az-140-study-guide-windows-virtual-desktop-on-microsoft-azure/>

- Another Study Guide #4 (Video series) - <https://youtu.be/DZNc1DQxEEA>

- Questions Examples - <https://www.itexams.com/exam/AZ-140>

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
  
- assess network capacity and speed requirements for Azure Virtual Desktop
  - AZ-140 ep05 | AVD Network Planning - <https://youtu.be/O3AaPTWzpi4>
    - Network guidelines - <https://docs.microsoft.com/en-us/windows-server/remote/remote-desktop-services/network-guidance>
    - Workload type - Recommended bandwidth: Light 1.5 Mbps, Medium 3 Mbps, Heavy 5 Mbps, Power 15 Mbps
    - Workload type - Recommended bandwidth: About 1024 × 768 px 1.5 Mbps, About 1280 × 720 px 3 Mbps, About 1920 × 1080 px 5 Mbps, About 3840 × 2160 px (4K) 15 Mbps
    - Check out the Azure Virtual Desktop experience estimator, latency up to 150 ms shouldn’t impact user experience that doesn't involve rendering or video. Latencies between 150 ms and 200 ms should be fine for text processing. Latency above 200 ms may impact user experience.
    - use the tool every two to three months to make sure the optimal location hasn't changed as Azure Virtual Desktop rolls out to new areas. - <https://docs.microsoft.com/en-us/azure/virtual-desktop/connection-latency>
  - Remote Desktop Protocol (RDP) bandwidth requirements - <https://docs.microsoft.com/en-us/azure/virtual-desktop/rdp-bandwidth>
    - The best way to understand bandwidth requirements is to monitor real user connections. Monitoring can be performed by the built-in performance counters or by the network equipment.
    - there's no need to limit bandwidth utilization as limiting may affect user experience. Yet in the constrained networks you may want to limit network utilization. You can use policy-based Quality of Service (QoS) within Group Policy to set the predefined throttle rate.

- recommend an operating system for an Azure Virtual Desktop implementation
  - Supported virtual machine OS images - <https://docs.microsoft.com/en-us/azure/virtual-desktop/overview#supported-virtual-machine-os-images>
  - x64 operating system images:
    - Windows 10 Enterprise multi-session
    - Windows 10 Enterprise
    - Windows 7 Enterprise
    - Windows Server 2019
    - Windows Server 2016
    - Windows Server 2012 R2
  - Windows Servers deployments requires also CAL with SA
  - Windows 7 doesn't support FSLogix
  - Multi-session image can be used only in Azure - License constraint

- plan and configure name resolution for Active Directory (AD) and Azure Active Directory Domain Services (Azure AD DS)
  - Configure Active Directory, Azure AD DNS - <https://www.youtube.com/watch?v=kfOYWFpoglQ>
  - Understand, AD Name Resolution, DNS, Configure Azure DNS, Azure AD Domain Services, DNS Conditional Forwarders, AVD DNS Email Discovery, private link names resolution
  - Multiple forests with AD DS and Azure AD - <https://docs.microsoft.com/en-us/azure/architecture/example-scenario/wvd/multi-forest>
  - Multiple forests with AD DS, Azure AD, and Azure AD DS - <https://docs.microsoft.com/en-us/azure/architecture/example-scenario/wvd/multi-forest-azure-managed>

- plan a host pools architecture
  - AZ-140 ep03 - <https://youtu.be/FLbcayyodqk>
  - Naming conventions, tagging strategy, region, validation pools (AVD Updates, testing on users), type of host pool (personal, pooled, remote app), breadth first vs depth first LB, automatic/direct assignment for personal, RDP Properties, VM size, Monitoring, AVD Roles Contributor and Reader on host pool level, BCDR

- recommend resource groups, subscriptions, and management groups
  - AZ-140 ep01 - <https://youtu.be/EG_Zqdm7OQ0>
  - Understand waterfall hierarchy - management groups, subscriptions, resource groups, resources
  - Resource quotas and limits, API calls throttling limits, cost management, regions

- configure a location for the Azure Virtual Desktop metadata
  - Data locations for Azure Virtual Desktop - <https://docs.microsoft.com/en-us/azure/virtual-desktop/data-locations>
  - WVD Service Metadata are: Workspace Names, Host Pool Names, Application Group Names, User Principal Names (UPN)
  - WVD Service Metadata locations are not available globally. The customer controls the selection of the WVD service metadata service region.
  - On the host pool level: The regions you selected is where the metadata for this host pool and its related objects will be stored. Make sure you choose the regions inside the geography you want the service metadata to be stored in.

- calculate and recommend a configuration for performance requirements
  - Virtual machine sizing guidelines - <https://docs.microsoft.com/en-us/windows-server/remote/remote-desktop-services/virtual-machine-recs>
    - Multi-session - All VMs should have more than two cores, VMs should not have more than 32 cores. Recommended VM size is between 4 vCPUs and 24 vCPUs. We don't recommend using 2 cores or 32 or more cores for standard and larger environments.
    - Single-session- at least two physical CPU cores per VM (typically four vCPUs with hyperthreading).
    - use Premium SSD storage in your OS disk for production workloads
    - B-series burstable VMs are a good choice for users who don't always need maximum CPU performance.
    - Cloud cache should use SSD disks

- calculate and recommend a configuration for Azure Virtual Machine capacity requirements
  - AZ-140 ep04 | Plan Your AVD Session Hosts - <https://youtu.be/HNCZ2pzr9mo>
  - When Availability Set is used it can support only 200 VMs without it can support 400 VMs. AS doesn't help with personal VM. For pooled it makes perfect sense but limit is 200 VMs per AS.
  - Azure subscription can have quota limits on SKU and region, you might need to create support ticket to increase quota

#### Design for user identities and profiles

- select an appropriate licensing model for Azure Virtual Desktop based on requirements
  - Customers are eligible to access Windows 10 single and multi-session and Windows 7 with Windows Virtual Desktop (WVD) if they have one of the following licenses:
    - Microsoft 365 E3/E5
    - Microsoft 365 A3/A5/Student Use Benefits
    - Microsoft 365 F1
    - Microsoft 365 Business
    - Windows 10 Enterprise E3/E5
    - Windows 10 Education A3/A5
    - Windows 10 VDA per user
  - Customers are eligible to access Server workloads with Windows Virtual Desktop (WVD) if they have one of the following licenses: RDS CAL license with active Software Assurance (SA)

- recommend an appropriate storage solution (including Azure NetApp Files versus Azure Files)
  - AZ-140 ep07 - <https://youtu.be/tXVxuDbbNi4>
  - FSLogix has four components (user profiles, office profiles, application masking, java version control)
  - You need to understand, How much storage you need for profiles (Ideally get average number from existing environment).
  - You can use simple math AVG profile size * number of users
  - Make sure Profiles are stored as VHDx files and make sure they use Dynamic disks settings
  - Align profile share with host pools (at minimum one share per host pool)
  - User logon requires 50 IOPs per user and later after user is on average is 10 IOPs per users. How many users might be logging on simultaneously?
  - You can use Azure Files, Azure NetApp Files, Storage Spaces Direct (self service 2+ VMs, NOT recommended).
    Keep region aligned. - <https://docs.microsoft.com/en-us/azure/virtual-desktop/store-fslogix-profile>
    - Do NOT use Azure NetApp Files only for AVD and if you have less than 7000 users. Snapshots and DR/Replication is available.
    - Think about large file share for Azure Files on standard tier, ZRS 20K IOPs, Up to 300 MiB/sec. Snapshots and Backup is available. Limited DR options.

- plan for Azure Virtual Desktop client deployment
  - AZ-140 ep10 - <https://youtu.be/-ce3mqwvyBI>
  - Multi-monitor or integrated apps (RAIL) is only on Windows client / MacOS client
  - Teams optimizations is only on Windows Desktop Clients
  - SSO with ADFS is Windows Desktop Clients only and HTML5 Only

- plan for user profiles
  - AZ-140 ep08 - <https://youtu.be/tFyLeg1f8BQ>
    - Profiles are designed to roam from one VM to another (attached virtual drive to session host) and are stored on SMB file share
    - In AVD you DO NOT need preserve/backup office profiles (it is cached data), you do not have to maintain/shrink.
    - You should separate User profiles and office profiles. Different DR/Backup, share strategy
    - Shrink user profiles - <https://github.com/FSLogix/Invoke-FslShrinkDisk>
    - Consider office profiles exclusions. E.g. Teams has 5GB storage which can be excluded.
    - Attaching via VHD locations from file shares (can be multiple shares/regions), another option is Cloud Cache
    - Cloud cache (lives in hidden space on C drive with writes locally and later replicates to file share/can be multiple)
    - Cloud cache can be preferred but takes longer for user to logon (couple of seconds) and consider C drive performance (specifically with pooled environments). Do NOT use additional disks
  - Three types of host pools
    - Pooled Desktop Host pools - typically requires FSLogix unless kind of jump box use case
    - Remote Apps pools - Usage of FSLogix depends.if applications needs to be personalized
    - Personal Host pools - do NOT need FSLogix
  - Do antivirus exclusions for FSLogix profiles during logon time - <https://docs.microsoft.com/en-us/azure/architecture/example-scenario/wvd/windows-virtual-desktop-fslogix#antivirus-exclusions>
  - On FSLogix level, set "Delete Local Profile When VHD Should Apply" for new environments only
  - "Size In MBs" (works only for new Disks) 30000 MBs good upper limit with dynamic disks
  - Volume Types - prefer VHDx (newer format + more capabilities) over VHD
  - Flip/Flop Profile Directory Name (user name first in file on network share)
  - Do not use concurrent connections for profiles (use one file share with one host pool)

- recommend a solution for network connectivity
  - Understanding Azure Virtual Desktop network connectivity - <https://docs.microsoft.com/en-us/azure/virtual-desktop/network-connectivity>
    - Reverse connect transport - it is using outbound connectivity to the Azure Virtual Desktop infrastructure over the HTTPS connection. On start of a session host, the Agent Loader service opens TLS 1.2 AVD broker's persistent communication channel between session host and Azure Virtual Desktop infrastructure.
  - Quality of Service (QoS) for Azure Virtual Desktop - <https://docs.microsoft.com/en-us/azure/virtual-desktop/rdp-quality-of-service-qos>
    - RDP Shortpath - allows real-time RDP traffic that's sensitive to network delays to "cut in line" in front of traffic that's less sensitive. If the client is in perimeter it can connect directly (after broker/gateway) via ER/VPN to VM over fast UDP.
    If you support a large group of users experiencing any of the problems (Jitter , Packet loss, Delayed round-trip time), you probably need to implement QoS. To address quality issues, we recommend that you first use QoS, then add bandwidth only where necessary. For QoS to be effective, you must apply consistent QoS settings throughout your organization. Any part of the path that fails to support your QoS priorities can degrade the quality RDP session.

- plan for Azure AD Connect for user identities
  - AZ-140 ep09 - <https://youtu.be/9kO68Euy--g>
  - AD + AD Connect -> AAD or AAD -> Azure AD DS is required
  - For AD users/groups are part of AD; For AAD DS users/groups are part of AAD
    Where you created objects initially - this is where you have to manage them

### Implement an Azure Virtual Desktop Infrastructure (25-30%)

#### Implement and manage networking for Azure Virtual Desktop

- implement Azure virtual network connectivity
  - AZ-140 ep12 - <https://youtu.be/kjqFUN78lso>
    - On VNET in DNS set Custom DNS1, Custom DNS2 and fallback to Azure DNS
    - Hub VNET to four subnets (GW, Firewall, Bastion + NSG, AD + NSG)

- manage connectivity to the internet and on-premises networks
  - Hub-spoke network topology in Azure - <https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/hybrid-networking/hub-spoke>
  - Implement a secure hybrid network - <https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/dmz/secure-vnet-dmz>

- implement and manage network security
  - NSG Rules List - <https://docs.microsoft.com/en-us/azure/virtual-desktop/safe-url-list#virtual-machines>
  - Use Azure Firewall to protect Azure Virtual Desktop deployments - <https://docs.microsoft.com/en-us/azure/firewall/protect-azure-virtual-desktop>

- manage Azure Virtual Desktop session hosts by using Azure Bastion
  - Learn here how to Manage your Windows Virtual Desktop host pools with Azure Bastion - <https://techcommunity.microsoft.com/t5/azure-virtual-desktop/learn-here-how-to-manage-your-windows-virtual-desktop-host-pools/m-p/783620>

- monitor and troubleshoot network connectivity
  - Monitoring Azure virtual network - <https://docs.microsoft.com/en-us/azure/virtual-network/monitor-virtual-network>
  - Troubleshooting connectivity problems between Azure VMs - <https://docs.microsoft.com/en-us/azure/virtual-network/virtual-network-troubleshoot-connectivity-problem-between-vms>
  - Troubleshoot Networking in Microsoft Azure - <https://msandbu.org/troubleshoot-networking-in-microsoft-azure/>

#### Implement and manage storage for Azure Virtual Desktop

- configure storage for FSLogix components
  - AZ-140 ep13 - <https://youtu.be/-GEHbrvEQdY>
  - Storage options for FSLogix profile containers in Azure Virtual Desktop - <https://docs.microsoft.com/en-us/azure/virtual-desktop/store-fslogix-profile>
- configure storage accounts
  - 15 characters or less for storage account (AAD Authentication/NETBIOS limit)
  - Use Private Link for storage, update NSG smb outbound to port 445 on TCP from subnet to private link IP
  - AD Integration with Azure File Share
  - User groups per user type and region
  - standard storage with large fileshare will be good option for majority of use cases (you do not want many VMs in host pool anyway)
    This might be different for pooled environment #of users * 50 IOPs must be < 20000 (SA standard with large file share feature enabled)
  - For storage prefer ZRS, unless cloud cache does replication. In this case LRS is just fine
  - Soft delete is enabled by default on file share. You do not need Azure backups in this case
  - Join Storage to the domain - On File Share/Configuration (NOT Azure AD domain services), use link at very bottom (domain join this storage account), part one enable AD DS authentication

- configure disks
  - Azure Ephemeral disks - <https://www.basvankaam.com/2020/07/01/what-er-azure-ephemeral-disks-how-to-use-them-with-wvd-and-why-you-should-care/>
  - AVD With Ephemeral OS Disks - <https://getnerdio.com/academy/how-to-speed-up-windows-virtual-desktop-with-ephemeral-os-disks-and-saving-on-storage-costs-too/>

- create file shares
  - Create a profile container with Azure Files and AD DS - <https://docs.microsoft.com/en-us/azure/virtual-desktop/create-file-share>
  - One fileshare per host pool
    Download AzFilesHybrid module via Azure Bastion to Azure VM/AD, three PS files, from DOC get main PS file which uses other PS files.
    Provide subscription, RG, SA name, computer account, OU, Encryption type
    After join, in the Azure SA/Config at the bottom AD DS integration option shows domain it integrated to and file share will show Active Directory Configured
  - Assign Permission on the share 1. Azure Files and 2. Windows NTFS
    Use somebody in Domain Admin role and in RBAC assign role "storage file data smb share elevated contributor" to this user. This user will have rights to set NTFS permissions
    And also in RBAC set users security group via RBAC into "share contributor" role
  - On some VM attach the file share with user in elevated role (PS script is on the file share) and on NTFS level assign permissions to users security group (will have modify only)

#### Create and configure host pools and session hosts

- create a host pool by using the Azure portal
  Tutorial: Create a host pool with the Azure portal - <https://docs.microsoft.com/en-us/azure/virtual-desktop/create-host-pools-azure-marketplace?tabs=azure-portal>

- automate creation of Azure Virtual Desktop host and host pools by using PowerShell, Command-Line Interface (CLI), and Azure Resource Manager templates
  - New-AzWvdHostPool
  - az desktopvirtualization hostpool create
  - ARM Template to Create and provision new Windows Virtual Desktop hostpool - <https://github.com/Azure/RDS-Templates/tree/master/ARM-wvd-templates/CreateAndProvisionHostPool>

#### Command-Line Interface (CLI), and Azure Resource Manager templates

- create a host pool based on Windows client or Windows Server session hosts
  - Image, you can choose either Gallery or Storage blob - <https://docs.microsoft.com/en-us/azure/virtual-desktop/create-host-pools-azure-marketplace?tabs=azure-portal#virtual-machine-details>
- configure host pool settings
  - Customize Remote Desktop Protocol (RDP) properties for a host pool - <https://docs.microsoft.com/en-us/azure/virtual-desktop/customize-rdp-properties>
  - Configure the Azure Virtual Desktop load-balancing method - <https://docs.microsoft.com/en-us/azure/virtual-desktop/configure-host-pool-load-balancing>
- manage licensing for session hosts that run Windows client or Windows Server
  - Apply Windows license to session host virtual machines - <https://docs.microsoft.com/en-us/azure/virtual-desktop/apply-windows-license>
- assign users to host pools
  - Configure the personal desktop host pool assignment type - <https://docs.microsoft.com/en-us/azure/virtual-desktop/configure-host-pool-personal-desktop-assignment-type>
- apply OS and application updates to a running Azure Virtual Desktop host
  - Configure the software update point - <https://docs.microsoft.com/en-us/azure/virtual-desktop/configure-automatic-updates#configure-the-software-update-point>
- apply security and compliance settings to session hosts
  - Session host security best practices - <https://docs.microsoft.com/en-us/azure/virtual-desktop/security-guide#session-host-security-best-practices>

#### Create and manage session host images

- create a gold image
  - AZ-140 ep14 - <https://youtu.be/teOD3z0PIZ0>
    - You can use custom script VM Extension to configure fslogix - powershell script from storage account with parameters like where fslogix share is located, etc.
    - Create image from some existing/customized, do sysprep (OOBE,Generalize, shutdown), capture image
    - Azure Image Builder is preferred, shared image gallery
    - sysprep has limit how many times it can be used and sometimes destroys custom optimizations
    - install apps via xml config files - setup.exe /configure myconfig.xml
    - Office Deployment Tool - <https://www.microsoft.com/en-us/download/details.aspx?id=49117>
    - OneDrive should be installed explicitly for all users with setup.exe /allusers flag
  - AZ-140 ep15 - <https://youtu.be/AzufupX2zOI>
    - Custom Image allows only 20 VMs to be deployed simultaneously
      You can overcome this with Shared Image Gallery and more replicas
    - For pool environment use premium disks on hosts
    - Start VM on connect - works only with personal host pools. (You can enable the start VM on Connect feature for personal or pooled host pools) - <https://docs.microsoft.com/en-us/azure/virtual-desktop/start-virtual-machine-connect>, requires to assigne role to "Azure Virtual Desktop"
    Update-AzWvdHostPool -ResourceGroupName <resourcegroupname> -Name <hostpoolname> -StartVMOnConnect:$true
    The Remote Desktop client has an indicator that lets the user know the PC is being powered on while they're connecting.
      AVD service needs to have permissions to start VM. In RBAC assign WVD service to custom role.
- modify a session host image
  - Add new VMs with the latest version to the hostpool (it will use latest image version from gallery)
  - Enable drain mode on old session host
- install language packs in Azure Virtual Desktop
  - Add language packs to a Windows 10 multi-session image - <https://docs.microsoft.com/en-us/azure/virtual-desktop/language-packs>
  - Add languages to a Windows 11 Enterprise image - <https://docs.microsoft.com/en-us/azure/virtual-desktop/windows-11-language-packs>
- deploy a session host by using a custom image
  - Add new VMs with the latest version to the hostpool (it will use latest image version from gallery)
- plan for image update and management
  - Shared Image Galleries overview - <https://docs.microsoft.com/en-us/azure/virtual-machines/shared-image-galleries>
- create and use a Shared Image Gallery
  - Create a gallery for storing and sharing images - <https://docs.microsoft.com/en-us/azure/virtual-machines/create-gallery>
- troubleshoot OS issues related to Azure Virtual Desktop
  - Troubleshooting Azure Virtual Desktop - <https://docs.microsoft.com/en-us/azure/virtual-desktop/troubleshoot-set-up-overview>

### Manage Access and Security (10-15%)

#### Manage access

- plan and implement Azure roles and role-based access control (RBAC) for Azure Virtual Desktop
  - Built-in roles for Azure Virtual Desktop - <https://docs.microsoft.com/en-us/azure/virtual-desktop/rbac>
  - Delegated access in Azure Virtual Desktop - <https://docs.microsoft.com/en-us/azure/virtual-desktop/delegated-access-virtual-desktop>
- manage local roles, groups and rights assignment on Azure Virtual Desktop session hosts
  - How to manage the local administrators group on Azure AD joined devices - <https://docs.microsoft.com/en-us/azure/active-directory/devices/assign-local-admin>
  - Assign users or groups through application groups
  - Automatic or direct assignment - <https://docs.microsoft.com/en-us/azure/virtual-desktop/configure-host-pool-personal-desktop-assignment-type>

- configure user restrictions by using Azure AD group policies and AD policies
  - Administer Group Policy in an Azure Active Directory Domain Services managed domain - <https://docs.microsoft.com/en-us/azure/active-directory-domain-services/manage-group-policy>

#### Manage security

- plan and implement Conditional Access policies for connections to Azure Virtual Desktop
  - Create a Conditional Access policy - <https://docs.microsoft.com/en-us/azure/virtual-desktop/set-up-mfa#create-a-conditional-access-policy>
  (New Policy, User/Groups assignments, Azure Virtual Desktop (App ID 9cdead84-a844-4324-93f2-b2e6bb768d07), Mobile/Desktop Client, Condition, Require MFA, Sign in freq (hours))
  - AVD Identity Security | Azure Virtual Desktop - #11- <https://youtu.be/31DQ8JuLQes>
- plan and implement multifactor authentication in Azure Virtual Desktop
  - Enable Azure multifactor authentication for Azure Virtual Desktop - <https://docs.microsoft.com/en-us/azure/virtual-desktop/set-up-mfa>
- manage security by using Azure Security Center
  - AVD Security best practices - <https://docs.microsoft.com/en-us/azure/virtual-desktop/security-guide>
  - Protecting Windows Virtual Desktop environments with Azure Security Center - <https://azure.microsoft.com/de-de/blog/protecting-windows-virtual-desktop-environments-with-azure-security-center>
- configure Microsoft Defender Antivirus for session hosts
  - Deployment guide for Microsoft Defender Antivirus in a virtual desktop infrastructure (VDI) environment - <https://docs.microsoft.com/en-us/microsoft-365/security/defender-endpoint/deployment-vdi-microsoft-defender-antivirus?view=o365-worldwide>

### Manage User Environments and Apps (20-25%)

#### Implement and manage FSLogix

- plan for FSLogix
  - Implement and manage FSLogix - <https://docs.microsoft.com/en-us/learn/modules/implement-manage-fslogix/>
  - FSLogix for the enterprise - <https://docs.microsoft.com/en-us/azure/architecture/example-scenario/wvd/windows-virtual-desktop-fslogix>
  - A Practical Guide to FSLogix Containers Capacity Planning and Maintenance - <https://stealthpuppy.com/fslogix-containers-capacity/>
  - The SECRET to FSLogix - <https://youtu.be/ffZZGVTYHFk>
  - Always separate Profile and Office Container
  - You can benefit from having different performance characteristics for storage for Profiles and Office Containers
  - Shrinks FSLogix Profile and O365 dynamically - Invoke-FslShrinkDisk.ps1 -Path \\server\share -Recurse -PassThru - <https://github.com/FSLogix/Invoke-FslShrinkDisk>
- install and configure FSLogix
  - Install FSLogix - <https://docs.microsoft.com/en-us/fslogix/install-ht>
- configure Profile Containers
  - Configure Profile Container - <https://docs.microsoft.com/en-us/fslogix/configure-profile-container-tutorial>
- configure Cloud Cache
  - Configure Cloud Cache - <https://docs.microsoft.com/en-us/fslogix/configure-cloud-cache-tutorial>
- migrate user profiles to FSLogix
  - Migrate existing user profiles to FSLogix Profile Containers - <https://www.christiaanbrinkhoff.com/2020/02/14/youtube-how-to-migrate-from-upd-to-fslogix-profile-container-profiles-to-windows-virtual-desktop/>
    - Convert-UPDProfile -ProfilePath “C:\Users\UserDisk1.vhd” -Target “\\Server\FSLogixProfiles$” -MaxVHDSize 20 -VHDLogicalSectorSize 512 -VHD -IncludeRobocopyDetails -LogPath C:\temp\Log.txt`
    - Convert-RoamingProfile -ParentPath <String> -Target <String> -VHDMaxSizeGB <UInt64> -VHDLogicalSectorSize <String> [-VHD][-IncludeRobocopyDetail] [-LogPath <String>] [-WhatIf] [-Confirm] [<CommonParameters>]`





#### Configure user experience settings

- configure Universal Print
  - Introduction To Microsoft Universal Print - <https://youtu.be/ZtM_fEg6-Jg>
- configure user settings through group policies and Endpoint Manager policies
- configure persistent and non-persistent desktop environments
- configure Remote Desktop Protocol (RDP) properties on a host pool
  - Customize Remote Desktop Protocol (RDP) properties for a host pool - <https://docs.microsoft.com/en-us/azure/virtual-desktop/customize-rdp-properties>
  You can customize using the Azure portal or by using the -CustomRdpProperty parameter in the Update-AzWvdHostPool cmdlet. Properties like: Multi-monitor mode, Drive redirections (Drives, clipboard, printers, COM ports, smart cards, devices, and usbdevicestore), Remote audio mode, VideoPlayback, EnableCredssp
  You can have also custom RDP properties.
- configure session timeout properties
- troubleshoot user profile issues
- troubleshoot Azure Virtual Desktop clients


- AZ-140 ep20 - <https://youtu.be/w9LKFohyP0o>
  - Microsoft Endpoint manager MEM/Intune -> E5 see license in AAD -> Mobility and security
    - AD Connect (configure device options) -> Enable Hybrid Join (devices from AD are registered to Azure AD for access management)
      SCP in AD tells which tenant
      after sync in AAD in All devices you can see machines
      Devices enrollment via GPO or MDM or MAM or MEM (Auto Enroll)
  - Universal print (Azure Service) requires five steps (License, Connector, Register, Assign, Install) - works through groups
  - Secure Client Devices (Conditional access policy for WVD: usr grp, condition, Grant)
  - Secure Session Hosts (Configuration Profiles)



#### Install and configure apps on a session host

- configure dynamic application delivery by using MSIX App Attach
- implement application masking
- deploy an application as a RemoteApp
- implement and manage OneDrive for Business for a multi-session environment
- implement and manage Microsoft Teams AV Redirect
- implement and manage browsers and internet access for Azure Virtual Desktop sessions
- create and configure an application group
- troubleshoot application issues related to Azure Virtual Desktop


- AZ-140 ep16 - <https://youtu.be/8jGKoKzf9MM>
  - MSIX AppAttach (stored separately on different disk, like profiles)
    Package, Test, Expand, Copy (to file share), Grant (Azure file share and NTFS permissions for group), Mount, Assign
      Self signed cert is hard, prefer trusted certs
      Use VHD or cimFS, not vhdx, disk size should be 1:3 ratio, cimFS is faster and less resources (can be more cim files), should be preferred
      SMB Share Read for security group on Azure level on NTFS side permission modify
      Mount is over session host in host pool, can take up to 5 minutes
  - FSLogix app masking (install all apps to image and control what users can see)
    - Application Rules Editor, creates .fx.a (assignments) and .fx.r (rules) you can assign per user/group
    - Rules are stored in central location and GPO will copy to target location on session host
    - In App groups - grouping apps in hostpool (Desktop App or Remote App) you control
      Remote App groups can be only in pooled env but can be combined with Desktop App
      Max 50 Apps per App Group | 200 App Groups per Tenant


### Monitor and Maintain an Azure Virtual Desktop Infrastructure (20-25%)

#### Plan and implement business continuity and disaster recovery

- plan and implement a disaster recovery plan for Azure Virtual Desktop
  - This is GREAT summary (must read) - <https://docs.microsoft.com/en-us/azure/cloud-adoption-framework/scenarios/wvd/eslz-business-continuity-and-disaster-recovery#design-recommendations>
  - Business continuity and disaster recovery (BCDR) considerations for Azure Virtual Desktop - <https://docs.microsoft.com/en-us/azure/cloud-adoption-framework/scenarios/wvd/eslz-business-continuity-and-disaster-recovery>
    - You can reduce the time required to back up, restore, and replicate data by:
      - Separating the user profile and office container disks. FSLogix offers the option to place disks in separate storage locations.
      - In normal usage, the office disk can consume many more gigabytes than the profile disk and the office disk isn't required to be resilient. It's a cache of data and can be downloaded again from Microsoft 365 online services.
      - OneDrive can be used to redirect well-known folders (Desktop, Documents, Pictures, Screenshots, and Camera Roll) if present. This redirection enables the resilience of this data without needing special consideration in a BCDR scenario.
      - Backup, replication, and restore of the profile disk is quicker without the inclusion of the cache data.
      - FSLogix containers can be replicated with Native Azure Storage replication mechanisms, cross-region replication of Azure NetApp Files, or Azure File Sync for VM-based file servers. FSLogix cloud cache built-in mechanism.
      - Consider, Golden image cross region availability
      - You can use the Azure Backup service to protect profile and office container data when stored in either Azure Files Standard tier or Premium tier.
      - You can use Azure NetApp Files snapshots and policies for Azure NetApp Files on all tiers.
      - You can use Azure Backup to protect host pool VMs. This practice is supported even if host pool VMs are stateless.
  - Set up a business continuity and disaster recovery plan - https://docs.microsoft.com/en-us/azure/virtual-desktop/disaster-recovery
  AVD has BCDR to preserve metadata during outages. When an outage occurs in a region, the service infrastructure components will fail over to the secondary location.
    - Replicate the VMs in a secondary location. (both pooled and personal with ASR + VNET + one hostpool)
    - If you're using profile containers, set up data replication in the secondary location. (The FSLogix agent can support multiple profile locations if you configure the registry entries for FSLogix. If you need synchronous replication to minimize data loss, then we recommend you use FSLogix Cloud Cache instead.)
    - Make sure user identities you set up in the primary location are available in the secondary location.
    - Make sure any line-of-business applications relying on data in your primary location are failed over to the secondary location.
    - Recommend you only failover up to 100 VMs at a time. If you have more VMs than that, we recommend you fail them over in batches 10 minutes apart.
- design a backup strategy for Azure Virtual Desktop
  - Summarized here: <https://docs.microsoft.com/en-us/azure/cloud-adoption-framework/scenarios/wvd/eslz-business-continuity-and-disaster-recovery#design-recommendations>
- configure backup and restore for FSLogix user profiles, personal virtual desktop infrastructures (VDIs), and golden images
  - Summarized here: <https://docs.microsoft.com/en-us/azure/cloud-adoption-framework/scenarios/wvd/eslz-business-continuity-and-disaster-recovery#design-recommendations>



- AZ-140 ep17 - <https://youtu.be/OKaHNuo5ubg>
  - Backup (recovery in the same place), DR is recovery in another place
  - Three items to protect (images, profiles, VMs)
    - Images can be replicated to other regions with shared image gallery (be aware of replica limits for quick simultaneous provisioning)
    - Backup Profiles
      - Storage Spaces Direct use Azure Backup + MARS
      - Azure NetApp Files use snapshots (in Windows in folder properties in previous versions you can do restore from snapshot)
      - Azure Files use Azure Backup instead of snapshots
    - DR Profiles
      - Azure Files use replications (Premium has only LRS/ZRS)
      - Azure NetApp Files use cross region replication
      - Better option is to use cloud cache to replicate up to 4 regions (Use GPO for registry keys)
    - Backup VMs (personal only no fslogix at all)
    - DR VMs (personal only use ASR)
    - VMs Backup and DR not needed for pooled environments, use primary region and secondary region
    - True Regional DR, Images replicated, storages are around globe, cloud cache uses multiple regions but new host pool needs to be created/protected in another region which means another app group which means another new icon




#### Automate Azure Virtual Desktop management tasks

- configure automation for Azure Virtual Desktop
- automate management of host pools, session hosts, and user sessions by using PowerShell and Azure Command-Line Interface (CLI)
- implement autoscaling in host pools
  - Scale session hosts using Azure Automation - <https://docs.microsoft.com/en-us/azure/virtual-desktop/set-up-scaling-script>
    - Shutting down and deallocating session host VMs during off-peak usage hours, then turning them back on and reallocating them during peak hours. Scaling tool built with the Azure Automation account and Azure Logic App that automatically scales session host VMs. Combination of an Azure Automation account, a PowerShell runbook, a webhook, and the Azure Logic App to function. When the tool runs, Azure Logic App calls a webhook to start the Azure Automation runbook. The runbook then creates a job. For off peek time, the job will set the session host VMs to drain mode to prevent new sessions from connecting to the hosts. The job will then notify any currently signed in users to save their work, wait the configured amount of time, and then force the users to sign out.
      - Schedule VMs to start and stop based on Peak and Off-Peak business hours.
      - Scale out VMs based on number of sessions per CPU core.
      - Scale in VMs during Off-Peak hours, leaving the minimum number of session host VMs running.
  - Shut Down Unused Session Hosts in an Azure Virtual Desktop (WVD, AVD) Personal and Pooled Host Pool - <https://youtu.be/0PWO3OaZmeQ>
    - Supports Autostart, requires GPO disconnect idle sessions, logout disconnected sessions



- AZ-140 ep18 - <https://youtu.be/CXD2FbODG-E>
  - AZCLI, PowerShell, ARM Templates




#### Monitor and manage performance and health

- monitor Azure Virtual Desktop by using Azure Monitor
- monitor Azure Virtual Desktop by using Azure Advisor
- customize Azure Monitor workbooks for Azure Virtual Desktop monitoring
- optimize session host capacity and performance
- manage active sessions and application groups
- monitor and optimize autoscaling results

- AZ-140 ep19 - <https://youtu.be/Val6RL60YjE>
  - Windows Virtual Desktop click -> Click Insights -> Has data, Dashboard, Alerts, uses log analytics workspace
  - Configure Diag Settings on host pool, workspace, session hosts to store to LA add also VM performance counters, configure events button


