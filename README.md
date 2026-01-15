
# Enterprise Network Security & Monitoring Lab

## 📌 Project Overview
This project demonstrates the design, configuration, and security hardening of a **two-office enterprise network** using **Cisco Packet Tracer**.  
The lab focuses on **real-world network security controls** commonly used by Network Engineers, SOC Analysts, and IAM / IT Security Administrators.

The goal is to simulate how organizations **secure inter-office communication, protect access switches, enable secure device management, and monitor events centrally**.


## Network Architecture

### Office 1
- Network: `192.168.1.0/24`
- Router IP: `192.168.1.1`
- Devices:
  - PCs
  - Switch
  - Syslog Server: `192.168.1.100`

### Office 2
- Network: `192.168.2.0/24`
- Router IP: `192.168.2.1`
- Devices:
  - PCs
  - Switch
  - Syslog Server: `192.168.2.100`

### Inter-Office Link
- Network: `192.168.12.0/24`
- Used for routing traffic between Office 1 and Office 2



## Security Implementations

### Access Control Lists (ACLs)
- **Purpose:** Block traffic from **Office 2 → Office 1**
- **Configuration:**
  - Extended ACL created on **Office Router 1**
  - Applied:
    - **Inbound on Router 1**
    - **Outbound on Router 2**
- **Result:**
  - Office 2 users cannot access Office 1 network
  - Office 1 traffic remains unaffected



### Switch Port Security
- **Applied On:** Office 1 Switch
- **Port Secured:** `FastEthernet0/1`
- **Mode:** Sticky MAC
- **Maximum MAC:** 1
- **Violation Action:** Shutdown
- **Purpose:**
  - Prevent unauthorized devices from connecting
  - Automatically lock port if a different device is plugged in



### Secure Device Management (SSH)
- **Enabled On:** Office Router 1
- **Telnet:** Disabled (insecure)
- **SSH Version:** 2
- **Authentication:** Local username & password
- **Purpose:**
  - Secure remote administration
  - Encrypt credentials and management traffic
  - Follow enterprise security best practices


### Centralized Logging (Syslog)
- **Office 1 Router → Syslog Server:** `192.168.1.100`
- **Office 2 Router → Syslog Server:** `192.168.2.100`
- **Logged Events:**
  - Configuration changes
  - Interface up/down
  - Security-related actions
- **Purpose:**
  - SOC-style monitoring
  - Audit and incident investigation
  - Visibility across network devices



## Key Learning Outcomes
- Understanding inter-office routing and traffic flow
- Implementing network-layer security using ACLs
- Protecting access switches with port security
- Replacing Telnet with SSH for secure management
- Monitoring network activity using Syslog
- Applying real-world enterprise security practices


## Technologies Used
- Cisco Packet Tracer
- Cisco 2911 Routers
- Cisco Switches
- Static Routing
- Extended ACLs
- SSH
- Switch Port Security
- Syslog Monitoring




