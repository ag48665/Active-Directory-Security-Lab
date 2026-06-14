# User Account Creation Detection

## Description

This detection identifies newly created user accounts using Windows Security Event ID 4720.

New account creation should be monitored because attackers may create local or domain accounts for persistence, privilege escalation, or unauthorized access.

---

## Data Source

* Windows Security Event Logs
* Event ID: 4720
* Source: WinEventLog:Security

---

## Detection Logic

### SPL Query

```spl
index=* EventCode=4720
```

---

## MITRE ATT&CK Mapping

| Technique ID | Technique      |
| ------------ | -------------- |
| T1136        | Create Account |

---

## Investigation Guidance

When reviewing user account creation events, analysts should verify:

* Newly created account name
* Account that performed the creation
* Hostname or domain controller involved
* Creation time
* Whether the account creation was expected
* Whether the account was added to privileged groups afterward

Potential indicators of suspicious activity include:

* Unexpected account creation
* Account creation outside business hours
* Creation of accounts with suspicious names
* New accounts followed by privileged group membership changes
* New accounts created shortly after failed logon activity

---

## Expected Result

The search returns Windows Security events where a new user account was created.

These events help analysts detect unauthorized account creation and potential persistence activity.

---

## Validation

The detection was validated using Windows Security Event ID 4720 events collected in Splunk Enterprise.

### Evidence

See:

```text
screenshots/user_account_creation.png
```
