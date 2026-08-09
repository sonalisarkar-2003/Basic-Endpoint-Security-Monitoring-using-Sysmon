# Basic Endpoint Security Monitoring using Sysmon

## AGENDA
<img width="1794" height="613" alt="image" src="https://github.com/user-attachments/assets/d5dd4123-f7a9-488a-b247-01cdb802c8d9" />

## ABSTRACT
<img width="1676" height="811" alt="image" src="https://github.com/user-attachments/assets/de4306c2-92cb-4d3d-aad5-e7d0bc4425a7" />

## MICROSOFT SYSMON: YOUR ENDPOINT'S CCTV
<img width="605" height="250" alt="image" src="https://github.com/user-attachments/assets/d34eef2e-ee24-4df1-8f6a-9421979799de" />
Microsoft Sysmon (System Monitor) is a free Sysinternals tool developed by Microsoft that extends Windows event logging by recording detailed system activities.
It helps security teams detect threats, investigate incidents and improve endpoint visibility.

**Version**

~First released in 2014 

~Latest versions continue to receive updates (v15.21)

**Usage**

~Monitors Windows endpoint activities in real time.

**Popularity**

~Free and lightweight

## CAPABILITIES
<img width="661" height="700" alt="image" src="https://github.com/user-attachments/assets/1ba2b63e-62c7-4434-8735-53d76231748a" />

## INSTALLATION AND CONFIGURATION

**Step 1: Download Sysmon**

Download the latest Sysmon ZIP package from the official Microsoft Sysinternals page. 
https://learn.microsoft.com/en-in/sysinternals/downloads/sysmon

Extract the ZIP file to a folder.

<img width="947" height="474" alt="image" src="https://github.com/user-attachments/assets/8277b367-bfa0-4f2b-9201-d50d43b67b8f" />

***Fig1. Sysmon v15.21 Download Page***


**Step 2: Download a Configuration File**

Download a Sysmon configuration file (.xml). 

A commonly recommended one is the SwiftOnSecurity configuration.
https://github.com/SwiftOnSecurity/sysmon-config

<img width="947" height="464" alt="image" src="https://github.com/user-attachments/assets/b602b9e3-83cc-460a-b1fc-5c34257957f1" />

***Fig2. Sysmon Config GitHub Repo***

**Step 3: Open Command Prompt or PowerShell and Run as Administrator**

**Step 4: Navigate to the Sysmon Folder**

*cd C:\Program Files\Sysmon*

<img width="966" height="444" alt="image" src="https://github.com/user-attachments/assets/7b87d82d-2158-47e2-a62a-0d21ae7437bc" />

***Fig3. Sysmon Program Files Directory***

**Step 5: Install Sysmon**

Install Sysmon using the configuration file using command:

*.\Sysmon64.exe  -i .\sysmonconfig-export.xml*

<img width="965" height="463" alt="image" src="https://github.com/user-attachments/assets/b10f3a39-dd9c-43cb-9749-65d5e6b7d242" />

***Fig4. Sysmon Installation Success***

**Step 6: Verify in Event Viewer**

Events are stored in :

*Applications and Services Logs/Microsoft/Windows/Sysmon
/Operational*

<img width="967" height="490" alt="image" src="https://github.com/user-attachments/assets/4cfcce6c-af79-4bf5-bb8c-5c861f7e0c5d" />

***Fig5. Verify Installation of Sysmon in EventViewer***

<img width="946" height="490" alt="image" src="https://github.com/user-attachments/assets/1187493e-9c1e-4346-9aa4-13c9ba542bd6" />

***Fig6. Sysmon Logs***

## ENDPOINT TELEMETRY ARTIFACTS

**Event ID 1 - Process Creation**

Logs newly created processes with command line, hashes, parent process

<img width="926" height="204" alt="image" src="https://github.com/user-attachments/assets/122703a6-c2f5-4682-a90d-1c64658ba813" />

***PoC 1. Creating a Process***

<img width="1227" height="743" alt="image" src="https://github.com/user-attachments/assets/94e08a98-834b-4c1e-99d0-824dfa1037f8" />

***PoC 2. Process Creation Log***

**Event ID 3 - Network Connection**

Records outbound network connections initiated by processes. 

<img width="958" height="876" alt="image" src="https://github.com/user-attachments/assets/52d5569f-79ae-49cd-a93e-05b545569933" />

***PoC 3. Network Connection Log***

**Event ID 7 - Image Loaded (DLL)**

Detect DLL hijacking and malicious DLLs

<img width="916" height="334" alt="image" src="https://github.com/user-attachments/assets/4c5c8770-d7ce-483e-b172-823c3d9a6bdb" />

***PoC 4. Event 7 - DLL Side‑Loading***

**Event ID 8 - CreateRemoteThread**

Indicates that a process created a thread in another process

<img width="956" height="617" alt="image" src="https://github.com/user-attachments/assets/97332229-a33a-4794-85bc-4bba9f9b1ed4" />

***PoC 5. Event 8 - Remote Thread Injection***









