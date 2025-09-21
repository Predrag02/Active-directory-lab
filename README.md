# Active Directory

## Objective
The objective of this project is to design and deploy a comprehensive network security infrastructure using virtual machines in VirtualBox. The project aims to simulate a real-world IT environment with the following components:
Splunk Enterprise deployed on an Ubuntu server for security information and event management (SIEM) to monitor, analyze, and visualize security data.
Active Directory hosted on a Windows Server for centralized authentication and user management.
A Windows client machine to simulate end-user activity within the network.
A Kali Linux machine to simulate a potential attacker’s perspective, used for penetration testing and security assessments.
This project demonstrates the integration of different technologies to create a secure network environment, while providing real-time data analytics and monitoring capabilities through Splunk.

### Skills Learned
- Virtualization using VirtualBox
- Installation and configuration of Ubuntu Server and Windows Server
- Deployment and setup of Splunk Enterprise on Linux
- Configuration of Active Directory Domain Services (AD DS) on Windows Server
- Creation and management of users, groups, and organizational units in Active Directory
- Joining Windows machines to an Active Directory domain
- Basic networking setup (static IP, DNS configuration, etc.)
- Installation and configuration of Sysmon (System Monitor) for detailed Windows event logging
- Deployment and configuration of Splunk Universal Forwarder on Windows machines
- Log forwarding from Windows endpoints to Splunk using Universal Forwarder
- Creating and using Splunk dashboards, alerts, and SPL (Search Processing Language) queries
- Simulating a brute-force attack using Hydra on an Active Directory login interface
- Analyzing attack behavior and detecting brute force attempts through Sysmon logs in Splunk
- Conducting basic penetration testing and attack simulation using Kali Linux



### Tools Used
- Splunk Enterprise as a Security Information and Event Management (SIEM) system for log ingestion, analysis, and real-time security monitoring.
- Sysmon (System Monitor) for detailed Windows event logging to capture system-level events and enhance visibility into suspicious activity.
- Splunk Universal Forwarder to forward logs from Windows endpoints to the Splunk server for centralized analysis.
- Hydra for simulating a brute-force attack on Active Directory login credentials.
- Kali Linux as a penetration testing platform for simulating attacks and assessing the network's security posture.
- Active Directory for user management, authentication, and simulating real-world corporate network environments.

## Steps
Based on the diagram below, we create a network with an Ubuntu server hosting Splunk, a Windows Server 2022 machine serving as Active Directory, a Windows 10 client, and Kali Linux for attack simulation.
 


<img width="664" height="655" alt="s11" src="https://github.com/user-attachments/assets/c53e9200-9266-4d5c-a025-39ff09ff5685" />



We installed 4 virtual machines in VirtualBox: Windows Server 2022 with Active Directory, Windows 10, Ubuntu server with Splunk, and Kali Linux for attacks.
 


*Ref 1: Network Diagram*
