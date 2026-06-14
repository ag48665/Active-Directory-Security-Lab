\# Active Directory Security Lab



\## Overview



This project demonstrates Active Directory security monitoring using Splunk Enterprise and Windows Security Event Logs.



The goal of this lab is to analyze authentication activity, identify suspicious logon behavior, monitor privileged access, detect account creation, and review group membership changes using Splunk SPL searches.



\---



\## Environment



| Component  | Details                |

| ---------- | ---------------------- |

| SIEM       | Splunk Enterprise 10.4 |

| Endpoint   | Windows 11             |

| Log Source | WinEventLog:Security   |

| Framework  | MITRE ATT\&CK           |



\---



\## Detection Use Cases



This lab includes the following Windows Security Event monitoring use cases:



\* Failed Logons — Event ID 4625

\* Successful Logons — Event ID 4624

\* Privileged Logons — Event ID 4672

\* User Account Creation — Event ID 4720

\* Group Membership Changes — Event ID 4732



\---



\## Detection 1 – Failed Logons



\### Objective



Detect failed authentication attempts that may indicate password guessing or brute-force activity.



\### SPL Query



```spl

index=\* EventCode=4625

```



\### MITRE ATT\&CK



| Technique ID | Technique   |

| ------------ | ----------- |

| T1110        | Brute Force |



\### Evidence



!\[Failed Logons](screenshots/failed\_logons.png)



\---



\## Detection 2 – Successful Logons



\### Objective



Monitor successful authentication events and identify valid account usage.



\### SPL Query



```spl

index=\* EventCode=4624

```



\### MITRE ATT\&CK



| Technique ID | Technique      |

| ------------ | -------------- |

| T1078        | Valid Accounts |



\### Evidence



!\[Successful Logons](screenshots/successful\_logons.png)



\---



\## Detection 3 – Privileged Logons



\### Objective



Detect logons that receive elevated privileges.



\### SPL Query



```spl

index=\* EventCode=4672

```



\### MITRE ATT\&CK



| Technique ID | Technique      |

| ------------ | -------------- |

| T1078        | Valid Accounts |



\### Evidence



!\[Privileged Logons](screenshots/privileged\_logons.png)



\---



\## Detection 4 – User Account Creation



\### Objective



Detect creation of new user accounts that may indicate unauthorized account creation or persistence.



\### SPL Query



```spl

index=\* EventCode=4720

```



\### MITRE ATT\&CK



| Technique ID | Technique      |

| ------------ | -------------- |

| T1136        | Create Account |



\### Evidence



!\[User Account Creation](screenshots/user\_account\_creation.png)



\---



\## Detection 5 – Group Membership Changes



\### Objective



Detect changes to security group membership that may indicate privilege escalation or account manipulation.



\### SPL Query



```spl

index=\* EventCode=4732

```



\### MITRE ATT\&CK



| Technique ID | Technique            |

| ------------ | -------------------- |

| T1098        | Account Manipulation |



\### Evidence



!\[Group Membership Changes](screenshots/group\_membership\_changes.png)



\---



\## Detection Summary



| Detection                | Windows Event ID | Status    |

| ------------------------ | ---------------- | --------- |

| Failed Logons            | 4625             | Validated |

| Successful Logons        | 4624             | Validated |

| Privileged Logons        | 4672             | Validated |

| User Account Creation    | 4720             | Validated |

| Group Membership Changes | 4732             | Validated |



\---



\## Skills Demonstrated



\* Active Directory Security Monitoring

\* Windows Security Event Log Analysis

\* Splunk SPL Development

\* Authentication Monitoring

\* Privileged Access Monitoring

\* Account Change Detection

\* MITRE ATT\&CK Mapping

\* SOC Analyst Workflow

\* Detection Engineering

\* Blue Team Analysis



\---



\## Key Takeaways



\* Windows Security Event Logs provide valuable visibility into authentication and account activity.

\* Splunk enables effective monitoring of failed logons, successful logons, privileged access, and account changes.

\* Mapping detections to MITRE ATT\&CK helps document security coverage.

\* Active Directory security monitoring is a core SOC analyst skill.



\---



\## Author



\*\*Agata Gabara\*\*



Cybersecurity Analyst | SOC Analyst | Threat Hunter



GitHub: https://github.com/ag48665



