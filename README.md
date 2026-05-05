# Windows Server Active Directory Lab

## Overview

This project demonstrates the deployment of a Windows Server 2022 domain environment, including Active Directory, DNS, and DHCP, within an isolated Hyper-V lab network.

The lab emphasizes building, validating, and troubleshooting core services, with a focus on understanding how network and domain components interact in a real-world environment.

This project was built to reinforce foundational system administration skills relevant to entry-level IT support and infrastructure roles.

---

## Skills Practiced

- Active Directory user and group management, including creation of Organizational Units (OUs) and department-based structure  
- DNS configuration and troubleshooting to support domain services and name resolution  
- DHCP scope creation and configuration, including IP addressing and lease management  
- Configuration of DHCP scope options (DNS server and domain name) to enable domain connectivity  
- Shared folder creation with NTFS permissions using security groups for controlled access  
- Basic troubleshooting of network and domain issues (DNS resolution, DHCP assignment, access permissions)  
- Validation of system configurations through user testing and access verification  

---

## Tools Used

- Windows Server 2022  
- Windows 10/11 client VM  
- Hyper-V  
- Active Directory Users and Computers  
- DNS Manager  
- DHCP Manager  

---

## What I Built

I designed and implemented a simulated business IT environment using Windows Server 2022 to replicate common enterprise infrastructure components.

Key configurations included:

- Active Directory domain structure with Organizational Units (OUs) and user accounts aligned to business departments  
- DNS configuration to support domain services and internal name resolution  
- DHCP scope and scope options to automate IP addressing and ensure proper domain connectivity  
- Shared file system with NTFS permissions enforced through department-based security groups  

I validated system functionality by testing domain joins, user access, and resource permissions, and resolved configuration issues through troubleshooting DNS, DHCP, and access control dependencies.

---

## Network Configuration

- Domain: lab.local
- Server: Windows Server 2022 (Domain Controller)
- Client: Windows 10/11 VM
- Services: Active Directory, DNS, DHCP
- Internal Network: 10.0.50.0/24
- Domain Controller IP: 10.0.50.2
- DHCP Scope: 10.0.50.100–10.0.50.200

Note: The lab uses an isolated internal Hyper-V network to simulate a private enterprise environment.

---

## Client Integration & Group Policy

This phase of the lab focused on integrating a Windows client into the lab.local domain and validating centralized management through Active Directory, DHCP, and Group Policy. The client successfully received an IP address from the DHCP server, authenticated using domain credentials, and applied Group Policy settings including department-based drive mappings. This confirms end-to-end functionality of core domain services.

---

## Project Outcome

This lab demonstrates the ability to build and manage a functional Windows Server environment, including identity management, network services, and access control.

Through this project, I gained hands-on experience configuring core IT infrastructure and troubleshooting common issues related to DNS, DHCP, and user permissions.

This project reflects common responsibilities in entry-level IT roles, including user management, network configuration, and troubleshooting system access issues.

---

## Key Takeaways

This lab helped me understand how:
- Active Directory structures users and groups  
- Permissions control access to resources  
- Network services like DNS and DHCP support system functionality  
- Troubleshooting access issues requires both logical and systematic thinking

---

## How to Recreate This Lab

- Windows Server 2022 VM
- Active Directory Domain Services role installed
- DHCP configured with scope and options
- Shared folders with NTFS permissions by department

---

## Screenshots

### Active Directory Users and Groups
<img src="screenshots/ad-users-groups.png" width="700">

Created and organized user accounts within department-based Organizational Units (OUs), demonstrating structured Active Directory management.

---

### DHCP Scope Configuration
<img src="screenshots/dhcp-scope.png" width="700">

Configured a DHCP scope to dynamically assign IP addresses within the 10.0.50.0/24 subnet, enabling automated client network configuration.

---

### DHCP Scope Options (DNS & Domain Configuration)
<img src="screenshots/dhcp-scope-options.png" width="700">

Configured DHCP scope options including DNS server and domain name to enable proper name resolution and domain integration.

---

### Shared Folder NTFS Permissions (Advanced)
<img src="screenshots/ntfs-permissions-advanced.png" width="700">

Applied advanced NTFS permissions using security groups to enforce department-level access control and secure shared resources.

---

### Network Diagram
<img src="screenshots/network-diagram.png" width="700">

This diagram represents the structure of the lab environment, including the domain controller, organizational units, client systems, and shared resources. It highlights how Active Directory, DNS, DHCP, and NTFS permissions work together to manage users, devices, and access control within a domain environment.

---

#### Client Domain Join
<img src="screenshots/client-domain-joined.png" width="700">

Successfully joined the Windows client machine to the `lab.local` domain, confirming proper DNS resolution and domain connectivity.

---

#### Domain User Login
<img src="screenshots/domain-login-hr-user.png" width="700">

Verified domain authentication by logging in with a domain user account (`LAB\hr_user1`).

---

#### DHCP Address Leases
<img src="screenshots/dhcp-address-leases.png" width="700">

Confirmed DHCP functionality by verifying that IP addresses were dynamically assigned to both the domain controller and client machines.

---

#### Group Policy Results (gpresult)
<img src="screenshots/gpresult-drive-mapping.png" width="700">

Validated that the `Drive Mapping - Departments` Group Policy Object was successfully applied to the user.

---

#### Mapped Network Drive
<img src="screenshots/mapped-drive-hr.png" width="700">

Confirmed that the HR department network drive was automatically mapped via Group Policy, demonstrating successful centralized resource access control.

---

## Troubleshooting & Lessons Learned

During the lab, I encountered several common configuration issues and worked through them to better understand how Windows Server services interact.

### Active Directory / Domain Setup
- **Issue:** Initial confusion around domain structure and OU organization.
- **Cause:** Lack of planning for how users and departments should be logically grouped.
- **Fix:** Reorganized OUs into department-based structure (HR, Finance, IT, etc.) to better reflect a real-world environment.

---

### DNS Configuration
- **Issue:** Clients were unable to resolve domain names or join the domain.
- **Cause:** DNS was not properly configured or clients were not pointing to the domain controller as their DNS server.
- **Fix:** Verified DNS role was installed, ensured proper forward lookup zone was created, and confirmed clients were using the correct DNS server IP.

---

### DHCP Scope Issues
- **Issue:** Client machines were not receiving IP addresses automatically.
- **Cause:** DHCP scope was either not activated or improperly configured.
- **Fix:** Activated the DHCP scope and verified IP range, subnet mask, and lease settings were correctly defined.

---

### DHCP Scope Options (DNS & Domain)
- **Issue:** Clients received IP addresses but could not resolve domain resources.
- **Cause:** DNS server and domain name were not configured in DHCP scope options.
- **Fix:** Configured DHCP options (006 DNS Servers and 015 DNS Domain Name) to point to the domain controller and local domain.

---

### NTFS Permissions / Shared Folder Access
- **Issue:** Users were unable to access shared folders as expected.
- **Cause:** Incorrect or missing security group permissions.
- **Fix:** Assigned permissions using department-based security groups and verified effective access through testing with different user accounts.

---

### Client Domain Connectivity Issue
- **Issue:** Client machine was unable to join the domain.
- **Cause:** Incorrect DNS configuration pointing outside the domain.
- **Fix:** Updated client DNS settings to point to the domain controller.

---

### General Takeaways
These issues reinforced the importance of:
- Proper planning of AD structure before implementation  
- DNS as a critical dependency for domain functionality  
- Ensuring DHCP and DNS work together correctly  
- Using security groups (not individual users) for scalable permission management  
- Testing access from the user perspective to validate configurations  
