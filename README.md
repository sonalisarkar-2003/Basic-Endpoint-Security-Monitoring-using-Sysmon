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

**Event ID 7 - Image Loaded (DLL)**

Detect DLL hijacking and malicious DLLs

<img width="916" height="334" alt="image" src="https://github.com/user-attachments/assets/41bbc893-cf6e-4227-b492-8ed9275e5404" />

***PoC 4. Event 7 - DLL Side‑Loading***

**Event ID 8 - CreateRemoteThread**

Indicates that a process created a thread in another process

<img width="956" height="617" alt="image" src="https://github.com/user-attachments/assets/359efaaa-cd31-41fd-be32-cb9633d39189" />

***PoC 5. Event 8 - Remote Thread Injection***

**Event ID 10 - Process Access** 

Records when one process opens another process.

<img width="948" height="325" alt="image" src="https://github.com/user-attachments/assets/67cf28b6-dc65-4899-9aab-61df67d8e64e" />

***PoC 6. Event 10 - LSASS Access***

**Event ID 11 - File Create**

Records when a file is created or overwritten. 


<img width="982" height="588" alt="image" src="https://github.com/user-attachments/assets/596c12ff-41dd-494a-8352-125df025b8e5" />

***PoC 7. Event 11 - File Creation***

**Event IDs 12-14 - Registry Events**

Record registry key and value creation, modification, deletion, and renaming. 

<img width="981" height="629" alt="image" src="https://github.com/user-attachments/assets/a427de3b-3437-4c05-b031-97dce346fb0e" />

***PoC 8. Event 13 - Registry Modification***

**Event ID 16 - Configuration Change**

Records when the Sysmon configuration is updated.  

<img width="902" height="726" alt="image" src="https://github.com/user-attachments/assets/a242f0fe-7c76-40eb-b3d9-2f214a01c970" />

***PoC 9. Event 16 - Config State Change***

**Event IDs 22 - DNS Query**

Records DNS queries issued by a process, regardless of whether the query succeeds


<img width="971" height="699" alt="image" src="https://github.com/user-attachments/assets/08d7fc01-0e2a-494e-9574-07eeafa0bb29" />

***PoC 10. Event 22 - DNS Query***

**Event ID 23 - File Delete**
Records file deletion activity. 


<img width="872" height="728" alt="image" src="https://github.com/user-attachments/assets/5ba37ab2-5bb1-4a51-ab3b-d19a2be7207c" />

***PoC 11. Event 13 - File Deletion***

**Event ID 25 - Process Tampering** 

Generated when Sysmon detects process image manipulation techniques.


<img width="1001" height="655" alt="image" src="https://github.com/user-attachments/assets/9589cf86-0b61-474e-b0a6-c35012d7a063" />

***PoC 12. Event 25***

**Event ID 255 - Error**

Indicates internal Sysmon errors


<img width="1249" height="279" alt="image" src="https://github.com/user-attachments/assets/e9fdb6cc-47a1-4987-b99b-31c1555c2181" />

***PoC 13. Event 255 - Driver Communication Error***


## WHAT CAN SYSMON DETECT ????

<img width="1290" height="911" alt="image" src="https://github.com/user-attachments/assets/e7a6da7b-f8f9-40e8-98a8-da2a6120bf1f" />

***Fig7.  Most Relevant Data Components Within Enterprise Sub-Techniques ©GitHub***

## MAPPING TELEMETRY TO MITRE ATT&CK

***Table 1. Sysmon-MITRE ATT&CK Mapping***

<img width="1859" height="555" alt="image" src="https://github.com/user-attachments/assets/0f1b0a0c-d11d-435c-8de6-d7cd87486ea7" />

## SIEM INTEGRATION

<img width="1716" height="684" alt="image" src="https://github.com/user-attachments/assets/21ced321-bd26-4ae0-a416-942cc2f9e5e5" />

## WAZUH DEPLOYMENT AND INTEGRATION

**WAZUH SERVER**

<img width="1003" height="609" alt="image" src="https://github.com/user-attachments/assets/b3ccba14-dd9c-4b1f-949a-004a0f8c3dff" />

*https://documentation.wazuh.com/current/deployment-options/virtual-machine/virtual-machine.html*

**WAZUH AGENT**

<img width="940" height="609" alt="image" src="https://github.com/user-attachments/assets/0a98982f-002e-4624-930b-e91247bf9fd7" />

*https://documentation.wazuh.com/current/installation-guide/wazuh-agent/wazuh-agent-package-windows.html*

<img width="866" height="465" alt="image" src="https://github.com/user-attachments/assets/298adeab-3e73-4c07-b4a3-1c698e35ff62" />

***Fig8. Wazuh OVA Login Screen***

<img width="866" height="465" alt="image" src="https://github.com/user-attachments/assets/a9a5548a-7c27-4ec5-a4db-fecc210ce4f9" />

***Fig9. Wazuh Server IP Configuration***

<img width="492" height="424" alt="image" src="https://github.com/user-attachments/assets/732eb6e7-f6a9-41cd-9276-3ab9871f1df4" />

***Fig10. Wazuh Agent***

<img width="785" height="429" alt="image" src="https://github.com/user-attachments/assets/dd19c33d-a474-449f-915e-69815ca33890" />

***Fig11. OSSEC-Config***

<img width="801" height="429" alt="image" src="https://github.com/user-attachments/assets/ab98e039-1fbb-4b23-8f73-e8e262b33e6c" />

***Fig12. Server Ip address*** 

<img width="802" height="561" alt="image" src="https://github.com/user-attachments/assets/108ab507-8e07-45d4-b50d-e40269c247f8" />

***Fig13. Configuration to collect Sysmon logs***

<img width="880" height="490" alt="image" src="https://github.com/user-attachments/assets/7b745247-185f-46c5-9166-315af9fafbc1" />

***Fig14. Wazuh Dashboard Login interface***

<img width="1071" height="490" alt="image" src="https://github.com/user-attachments/assets/ee76108f-bb6d-4ece-af49-2336d7789a66" />

***Fig15. Dashboard displaying active agents***

<img width="1146" height="518" alt="image" src="https://github.com/user-attachments/assets/b3b94f05-b88f-4267-b9af-47e7627d60d1" />

***Fig16. Endpoint overview***

## Use Case: Detecting Fileless PowerShell Execution 

**1. Execution of Suspicious Command**

<img width="1044" height="183" alt="image" src="https://github.com/user-attachments/assets/63e7670a-98ba-45ac-bc5c-38df6b02c78c" />

***PoC 1. Execution of command***

**COMMAND:**

*powershell.exe -nop -w hidden -c "Write-Host 'Testing Fileless Detection'”*

~ powershell.exe - Launch Microsoft PowerShell interpreter

~ -nop - No Profile

~ -w hidden - Window Hidden

~ -c - Command

~ Write-Host - Display text on PowerShell Console

~ “Testing files Detection” -  Message printed to console

**2. Sysmon Logging**

<img width="909" height="873" alt="image" src="https://github.com/user-attachments/assets/01c6fbbf-3d63-49bd-ac92-af12094c8b27" />

***PoC 2. Sysmon Event ID 1 Log*** 

<img width="939" height="626" alt="image" src="https://github.com/user-attachments/assets/041bb613-fe93-45fc-807e-04d57684068b" />

***PoC 3. Sysmon Event ID 11 log***

**3. Wazuh Alerts**

<img width="1826" height="723" alt="image" src="https://github.com/user-attachments/assets/6a41c962-aeba-4496-8908-ca9093b79957" />

***PoC 4. Alerts in Wazuh server***

**4. Wazuh Alert analysis**

<img width="1761" height="943" alt="image" src="https://github.com/user-attachments/assets/66e4552c-3a00-4c3d-8d55-b4a49045e175" />
<img width="1536" height="941" alt="image" src="https://github.com/user-attachments/assets/f0f132fa-f291-44ae-8681-51c67481eaec" />
<img width="1318" height="952" alt="image" src="https://github.com/user-attachments/assets/66d713c8-5bcd-40fb-b8f1-d9c06d70fcac" />

***PoC 5. Alert of Event ID 1 in Wazuh***

**Table 2. Comparison of Sysmon raw telemetry and Wazuh-enriched security alerts**

<img width="1816" height="921" alt="image" src="https://github.com/user-attachments/assets/4d94222d-7ad4-4432-ae8f-9c55b3aec706" />

## TOOLS & TECHNOLOGIES

<img width="1928" height="748" alt="image" src="https://github.com/user-attachments/assets/c71e55c9-2e3d-43fe-87bf-44c6e639e6c3" />

## CHALLENGES

<img width="1816" height="676" alt="image" src="https://github.com/user-attachments/assets/2b1f1bcd-4946-43fb-9653-da6ec98729cc" />

## RECOMMENDATIONS

<img width="1817" height="672" alt="image" src="https://github.com/user-attachments/assets/48abe425-e337-462d-89d8-c586650e00c5" />

## CONCLUSION

Every process, connection, file, and registry change leaves a digital footprint. Sysmon captures these footprints, enabling security teams to detect, investigate and respond to threats with greater confidence.

Combined with Wazuh SIEM, these footprints become meaningful security insights through automated analysis, alerts and aesthetic dashboard visualization. 

**Sysmon doesn't stop cyberattacks but it ensures they leave a trail.** 

## REFERENCES

 ~ Microsoft Learn (2026): **Sysmon Overview - Official documentation**

*https://learn.microsoft.com/en-us/windows/security/operating-system-security/sysmon/overview*

~ Blumira YouTube Channel: **Sysmon 101: Leveling Up Windows Security**

*https://www.youtube.com/watch?v=iCQscXs3Sio*

~ Wazuh Blog (2024): **Using Wazuh to monitor Sysmon events**

*https://wazuh.com/blog/using-wazuh-to-monitor-sysmon-events/*

~ CSNP Blog (2023): **Sysmon - Enhanced logging for Windows**

*https://csnp.org/blog/sysmon-enhanced-logging-for-windows*

~ **Integrating Sysmon with Wazuh to Detect Fileless Malware**

*https://www.youtube.com/watch?v=nuhMcsF8mCg*





















  

















  



























































