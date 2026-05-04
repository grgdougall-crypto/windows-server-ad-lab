# Windows Server Active Directory Lab

## Overview
This project documents my hands-on practice building a Windows Server 2022 environment using Active Directory, DNS, DHCP, shared folders, NTFS permissions, and Group Policy.

The goal of this lab is to simulate real-world IT support and system administration tasks commonly performed in entry-level IT roles.

---

## Skills Practiced
- Active Directory user and group management  
- Organizational Unit (OU) structure  
- DNS and DHCP configuration  
- Shared folders and NTFS permissions  
- Group Policy basics  
- Troubleshooting user access issues  

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

I created a simulated business environment with department-based users, groups, and shared folders.

I configured:

- User accounts and security groups for multiple departments  
- Organizational Units (OUs) to structure the environment  
- Shared folders with NTFS permissions configured using department-level security groups
- DNS and DHCP services, including scope configuration and scope options (DNS server and domain integration)

I also tested user access and troubleshot permission issues to better understand how systems interact in a real-world environment.

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

Configured a DHCP scope with defined IP address range, subnet mask, and lease duration to support client device connectivity.

---

### DHCP Scope Options (DNS & Domain Configuration)
<img src="screenshots/dhcp-scope-options.png" width="700">

Configured DHCP scope options including DNS server and domain name to enable proper name resolution and domain integration.

---

### Shared Folder NTFS Permissions (Advanced)
<img src="screenshots/ntfs-permissions-advanced.png" width="700">

Applied advanced NTFS permissions using security groups to enforce department-level access control and secure shared resources.

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

### General Takeaways
These issues reinforced the importance of:
- Proper planning of AD structure before implementation  
- DNS as a critical dependency for domain functionality  
- Ensuring DHCP and DNS work together correctly  
- Using security groups (not individual users) for scalable permission management  
- Testing access from the user perspective to validate configurations  
