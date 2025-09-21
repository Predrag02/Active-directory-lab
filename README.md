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

<img width="342" height="548" alt="s12" src="https://github.com/user-attachments/assets/b183ec11-da1f-4413-8a13-f46701ef6024" />

In VirtualBox, under Tools → NAT Networks, we click on "Create" to set up a network for our virtual machines.

<img width="961" height="548" alt="s1" src="https://github.com/user-attachments/assets/7f8bb885-394a-4453-b731-ddd471c71e9e" />

After creating the network, we configure the network name and IPv4 scope in the general options.

<img width="341" height="220" alt="s2" src="https://github.com/user-attachments/assets/c5c58863-2ee0-4abd-82e4-fd0b4a3691df" />

Once finished, we should see the changes under the NAT networks tab as shown in the picture.

<img width="1218" height="140" alt="s3" src="https://github.com/user-attachments/assets/9a5925fd-1b9d-4894-9731-cc8fecddf3f3" />

Next, we configure each virtual machine to use the newly created network.

<img width="625" height="491" alt="s4" src="https://github.com/user-attachments/assets/3405d030-fe09-4478-a2c7-2b8136a9ab2d" />

First, we configure the Ubuntu server.

<img width="820" height="285" alt="s5" src="https://github.com/user-attachments/assets/42a8c2c5-0468-42ff-9918-ff0bf90df4f6" />

 
In the 50-cloud-init.yaml file, we set the IPv4 address according to our network scheme.


<img width="478" height="46" alt="s6" src="https://github.com/user-attachments/assets/1f3b19f9-5e39-4d40-a6f5-994503065394" />
<img width="746" height="797" alt="s7" src="https://github.com/user-attachments/assets/17c167b4-d047-438f-92b6-9383ea5456c0" />



Then we download the Splunk Enterprise .deb version for Linux from the official website.


<img width="824" height="289" alt="s9" src="https://github.com/user-attachments/assets/9f83e7f5-7e5b-4cfa-9fdf-c7306cc2deea" />

 
To install this file on the Ubuntu server, we create a shared folder in VirtualBox. 

<img width="634" height="493" alt="s10" src="https://github.com/user-attachments/assets/ed29c7f7-6a84-4076-b600-fa177ad07179" />

<img width="634" height="493" alt="s11" src="https://github.com/user-attachments/assets/75715b0e-26af-4a41-a654-95f91ad30abc" />

We install the tools and drivers necessary for VirtualBox interaction. 

<img width="1056" height="559" alt="s12" src="https://github.com/user-attachments/assets/fb30b0b9-3400-497d-b32c-c3f02bf73232" />

 
We add our user (splunk) to the vboxsf group and create a shared folder with access to the Splunk installation file.

 

<img width="437" height="127" alt="s13" src="https://github.com/user-attachments/assets/1d99683f-106c-457f-9fae-b3303d823844" />







We use the mount command to link the shared folder with the Ubuntu server; the picture below shows how it looks.
 
<img width="1055" height="684" alt="s14" src="https://github.com/user-attachments/assets/3baa2088-7fed-48f1-91da-04d89e9fbd79" />







We start the Splunk installation on the server.

  <img width="1055" height="684" alt="s15" src="https://github.com/user-attachments/assets/476fb1cc-3054-476d-8e44-ce303243e1c3" />
  <img width="1266" height="798" alt="s16" src="https://github.com/user-attachments/assets/c33aa94a-982b-4728-ad0b-864e83c848d2" />
  
After installation, we configure Splunk to start automatically on system boot.
 
<img width="1266" height="78" alt="s17" src="https://github.com/user-attachments/assets/e8981aaf-d106-48b2-a8c0-2128d845b992" />

Once Splunk is installed, we move to the Windows machine and set the IPv4 address and DNS.


 <img width="1019" height="775" alt="s18" src="https://github.com/user-attachments/assets/162692db-16d6-424a-a89d-63bbaea9cdc7" />






Then we download and install the Splunk Forwarder from the Splunk website.
 


<img width="1024" height="838" alt="s20" src="https://github.com/user-attachments/assets/26da2618-4868-42b4-ad44-296fd980a159" />





We set the username as admin and let the system generate the password automatically.

 <img width="1024" height="838" alt="s21" src="https://github.com/user-attachments/assets/7ab391d4-4b99-4e48-a489-77fcd7cbb1bd" />

Next, we configure the forwarding settings to send logs to the Splunk server address.
 



<img width="1024" height="838" alt="s22" src="https://github.com/user-attachments/assets/27c455ee-66f5-43e1-8850-17b14527449f" />




After installation, we download Sysmon for generating logs on the Windows machine. 




<img width="1024" height="838" alt="s23" src="https://github.com/user-attachments/assets/9a8e19eb-d8c9-44af-b3e7-f7038b0fd81a" />





We use a configuration file for Sysmon from Olaf Hartong's GitHub repository.

 

<img width="1024" height="775" alt="s24" src="https://github.com/user-attachments/assets/5782da9b-fa8a-4584-972e-d746228f05ec" />





We run Sysmon installation in PowerShell with the -i flag to specify the configuration file.

<img width="1024" height="775" alt="s25" src="https://github.com/user-attachments/assets/871ff14e-cd94-4ed4-8073-f79629c4f75f" />

<img width="1024" height="775" alt="s26" src="https://github.com/user-attachments/assets/7e045742-c5f9-45f5-af17-20a3e052a432" />

Then we create the inputs.conf file in the local Splunk folder and configure the index and log types.

<img width="1024" height="775" alt="s27" src="https://github.com/user-attachments/assets/5068e9cc-46d8-4ae8-934b-98deb89064f1" />

<img width="1024" height="788" alt="s28" src="https://github.com/user-attachments/assets/df1998de-2a90-4a8d-866b-4dbb5ea56bcd" />


  
We also set the service to run under the Local System account for maximum privileges.

<img width="398" height="466" alt="s29" src="https://github.com/user-attachments/assets/a5c18755-a2c4-42ef-9c8f-81c9ccf35087" />

 
The Splunk configuration for the Windows server is identical to the Windows client configuration.




In the browser, entering 192.168.10.10:8000 opens the Splunk login page.

 

<img width="1024" height="838" alt="s19" src="https://github.com/user-attachments/assets/6c43109b-f693-465c-823c-13b2fc1b2cc4" />






After logging in, we see the Splunk dashboard..


 


<img width="1022" height="829" alt="s30" src="https://github.com/user-attachments/assets/23e2f0e8-8e2f-4c24-b83d-bc9ae7b04c8e" />





Next, we create the index defined in the inputs.conf file for the Splunk forwarder to send logs.
 


<img width="1022" height="829" alt="s31" src="https://github.com/user-attachments/assets/fbeae961-3bd7-4ec0-8690-04a4198f11a0" />





We also configure the port on which the server will receive logs (9997 is the default).

<img width="1022" height="829" alt="s32" src="https://github.com/user-attachments/assets/08f7b3f8-4261-4440-b757-4e7acf6502be" />

<img width="1022" height="829" alt="s33" src="https://github.com/user-attachments/assets/47baa825-577e-4257-a00d-a45ec31b4b81" />

<img width="1022" height="829" alt="s34" src="https://github.com/user-attachments/assets/a3372a58-9d5d-4280-b494-fe774e564122" />


In the search bar, we can search all logs sent to index=endpoint.
 



<img width="1022" height="829" alt="s35" src="https://github.com/user-attachments/assets/d048ed5c-4d0a-4dd8-8171-eeb8612a7f7b" />




Next, we configure the Windows Server by setting its IPv4 address.
 




<img width="1023" height="732" alt="s36" src="https://github.com/user-attachments/assets/6dded9da-c313-4c69-9df6-c2f79d794be0" />




In the Manage dropdown menu, we start the domain controller installation by selecting Role-based or feature-based installation.
 


<img width="1023" height="732" alt="s37" src="https://github.com/user-attachments/assets/31311d97-8fd7-438c-a20b-d7f4d7b52746" />




We select our Windows Server. 



<img width="1023" height="732" alt="s38" src="https://github.com/user-attachments/assets/c377cca8-4094-4aa8-84a9-89b7450e502c" />





Under Server Roles, we choose Active Directory Domain Services and click Add Features. 




<img width="1023" height="732" alt="s39" src="https://github.com/user-attachments/assets/5da9b30e-cac0-4ea7-93e1-3041d7989b81" />




We confirm the installation and proceed.

<img width="1023" height="732" alt="s40" src="https://github.com/user-attachments/assets/2156e7d4-5c71-4fe1-a355-f657180860a5" />

<img width="1023" height="732" alt="s41" src="https://github.com/user-attachments/assets/2c6ace6f-818e-4fba-aed3-9ee0bd73ca2c" />

  
After installation, we configure the domain.

 

<img width="1023" height="732" alt="s42" src="https://github.com/user-attachments/assets/e21673a2-303e-437d-8294-76abd373a980" />




We select Add a new forest and assign a domain name.
 



<img width="1023" height="732" alt="s43" src="https://github.com/user-attachments/assets/ee9e2e40-10cb-4ad5-8764-9873121e79c5" />





On the next page, we set the password and continue. 

<img width="1023" height="732" alt="s44" src="https://github.com/user-attachments/assets/aef33585-1f12-47ec-ba2c-4377048f6219" />
<img width="1023" height="732" alt="s45" src="https://github.com/user-attachments/assets/80e04506-bc9a-499e-90fa-b8320f2c5d73" />

  
If everything installs successfully, we see the domain name in front of the username.
 




<img width="1023" height="773" alt="s46" src="https://github.com/user-attachments/assets/a637dea5-e807-459c-b004-32965d2412c0" />




To add new users, we open Active Directory Users and Computers from the Tools menu. 



<img width="1023" height="773" alt="s47" src="https://github.com/user-attachments/assets/8a735e3f-9b2f-4e9d-906f-dc17e67b44db" />





Right-clicking the domain name, we first create an Organizational Unit . 



<img width="1023" height="773" alt="s48" src="https://github.com/user-attachments/assets/a187b0c7-2990-47a1-8fa8-d038555ba6d8" />





We created the OU named IT. 



<img width="1023" height="773" alt="s49" src="https://github.com/user-attachments/assets/44085c13-a9d8-405c-b3cc-97c6966952c4" />





Right-clicking the unit, selecting New → User, we create users, setting usernames and passwords. 

<img width="1023" height="773" alt="s50" src="https://github.com/user-attachments/assets/5580de54-088f-472b-9b0c-650579533c4c" />

<img width="1023" height="773" alt="s51" src="https://github.com/user-attachments/assets/d0105167-c52f-40bb-9d4f-8c88779ccd2f" />

<img width="1023" height="773" alt="s52" src="https://github.com/user-attachments/assets/00adedc6-c4cd-480f-8317-6d15d6afee1e" />

  
The same process is repeated for the HR department.

 

<img width="1023" height="773" alt="s53" src="https://github.com/user-attachments/assets/35cc57ed-2cda-44e4-8e74-b0a9b14f4331" />







After creating the accounts, we return to the Windows client and set its DNS server to the Windows Server IP address.


 
<img width="1023" height="832" alt="s56" src="https://github.com/user-attachments/assets/c3f4cf4e-192c-40a3-8e68-37ba7d6d9659" />






Then we go to PC Properties → Advanced System Settings.
 


<img width="1023" height="832" alt="s54" src="https://github.com/user-attachments/assets/c39dc7cf-f364-446c-9aff-bc6b350a2c40" />





Under the Computer Name tab, we click Change.
 



<img width="1023" height="832" alt="s55" src="https://github.com/user-attachments/assets/708c7b67-d0dd-4b11-964d-5a875331bb65" />




We select Domain and enter the domain name we set on Windows Server (project.local). 



<img width="1023" height="832" alt="s57" src="https://github.com/user-attachments/assets/2ee14314-df20-4d17-ad15-62892b16cded" />




To save the changes, we log in using the Windows Server administrator account. 




<img width="1023" height="832" alt="s58" src="https://github.com/user-attachments/assets/992f6c61-9114-4543-8aaa-3b9f343ee5dc" />



If successful, we see a welcome message. 



<img width="1023" height="832" alt="s59" src="https://github.com/user-attachments/assets/a5af69a8-f3bc-4c15-8bd7-513f79e260f1" />



On the next login screen, we see the domain name below the login field; using the created domain credentials, we can log in.

<img width="1023" height="832" alt="s60" src="https://github.com/user-attachments/assets/9d965027-6497-4fc7-bf6b-f3591ab9d06f" />

<img width="1023" height="832" alt="s61" src="https://github.com/user-attachments/assets/4da628d3-7ef0-433c-8327-d042c17200f5" />

  
To simulate a brute-force attack, we configure the IPv4 address on the Kali Linux virtual machine.

  <img width="793" height="664" alt="s62" src="https://github.com/user-attachments/assets/cb086de7-9cdf-49c7-a126-cdd7dbba452c" />
  
<img width="793" height="664" alt="s63" src="https://github.com/user-attachments/assets/e0af4a86-2890-4b52-aa6d-dfdf4b55d8c7" />



We copy 20 passwords from rockyou.txt into password.txt, placing our correct password at the end. 


<img width="793" height="664" alt="s64" src="https://github.com/user-attachments/assets/0251e42b-9ba4-4749-b24c-78da1e36d173" />




To run the brute-force attack, we return to the Windows machine and go to Properties.
 


<img width="1021" height="836" alt="s65" src="https://github.com/user-attachments/assets/6ff0eae1-273a-4dc7-85f6-a6315b803616" />




Under Advanced System Settings → Remote, we enable Allow remote connections to this computer.
 

<img width="1021" height="836" alt="s66" src="https://github.com/user-attachments/assets/2b1a9bd6-2b4a-43c6-bb61-12cc5f328561" />





Clicking Select Users → Add, we add users allowed to use RDP (Remote Desktop Protocol).
 


<img width="1021" height="836" alt="s67" src="https://github.com/user-attachments/assets/44696f0e-8f89-476b-97b0-a64df6399913" />




The Remote Desktop Users window shows added users; after clicking OK and Apply, RDP is enabled, allowing brute-force attacks from Kali Linux.
 


<img width="1021" height="836" alt="s68" src="https://github.com/user-attachments/assets/2734d277-2385-4de1-9318-98f319543078" />




We use Hydra for the brute-force attack with the following flags: -l (username), -P (password list), -t (threads), and the target IP address. We specify rdp because we use the RDP protocol.
 



<img width="803" height="439" alt="image" src="https://github.com/user-attachments/assets/39a51e06-5720-444b-a679-694facd216ff" />








Back in the Splunk web interface, we search index=endpoint and EventCode=4625 (failed login code).
 


<img width="975" height="731" alt="image2" src="https://github.com/user-attachments/assets/813cc8d4-ea82-4437-a588-239f18138eff" />





Search results show multiple failed attempts within a second, indicating a brute-force attack.
 


<img width="975" height="731" alt="image" src="https://github.com/user-attachments/assets/c8fff335-b019-41f3-9401-5a40b7cfcdec" />





We then search for EventCode=4624 (successful login) to confirm successful access.
 


<img width="975" height="731" alt="image" src="https://github.com/user-attachments/assets/75db71f6-75b9-4e37-a98f-588041c86830" />





Clicking Show all lines reveals the attacking machine's name and IP address.


<img width="975" height="731" alt="image" src="https://github.com/user-attachments/assets/65a96a64-bb24-43af-959d-ad1d3f489b1f" />



