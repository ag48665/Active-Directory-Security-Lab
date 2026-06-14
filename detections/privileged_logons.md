# Privileged Logons Detection

## Description

This detection identifies Windows logons that were assigned special privileges using Security Event ID 4672.

Privileged logons are important to monitor because they may indicate administrative access, privileged account usage, or potential misuse of elevated permissions.

---

## Data Source

* Windows Security Event Logs
* Event ID: 4672
* Source: WinEventLog:Security

---

## Detection Logic

### SPL Query

```spl
index=* EventCode=4672
```

---

## MITRE ATT&CK Mapping

| Technique ID | Technique      |
| ------------ | -------------- |
| T1078        | Valid Accounts |

---

## Investigation Guidance

When reviewing privileged logon events, analysts should verify:

* Account name
* Logon time
* Hostname
* Privileges assigned
* Whether the account is expected to have administrative rights
* Whether the activity occurred during normal working hours

Potential indicators of suspicious activity include:

* Unexpected privileged logons
* Privileged access by standard user accounts
* Administrative logons outside normal hours
* Privileged logons after multiple failed authentication attempts
* Privileged activity from unfamiliar systems

---

## Expected Result

The search returns Windows Security events where an account was assigned special privileges during logon.

These events help analysts monitor administrative access and identify potentially suspicious privileged account usage.

---

## Validation

The detection was validated using Windows Security Event ID 4672 events collected in Splunk Enterprise.

### Evidence

See:

```text
screenshots/privileged_logons.png
```
