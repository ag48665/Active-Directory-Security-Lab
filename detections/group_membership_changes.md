# Group Membership Changes Detection

## Description

This detection identifies changes to security group membership using Windows Security Event ID 4732.

Monitoring group membership changes is important because attackers may add accounts to privileged groups to gain elevated access, maintain persistence, or escalate privileges within the environment.

---

## Data Source

* Windows Security Event Logs
* Event ID: 4732
* Source: WinEventLog:Security

---

## Detection Logic

### SPL Query

```spl
index=* EventCode=4732
```

---

## MITRE ATT&CK Mapping

| Technique ID | Technique            |
| ------------ | -------------------- |
| T1098        | Account Manipulation |

---

## Investigation Guidance

When reviewing group membership changes, analysts should verify:

* User account added to the group
* Security group name
* Account that performed the action
* Time of the change
* Whether the change was authorized
* Whether the group grants administrative privileges

Potential indicators of suspicious activity include:

* Addition of users to Administrators groups
* Addition of accounts to Domain Admins
* Unexpected privilege assignments
* Group membership changes outside business hours
* Multiple account modifications in a short period of time

---

## Expected Result

The search returns Windows Security events where a user account was added to a security-enabled group.

These events help analysts identify unauthorized privilege assignments and account manipulation activity.

---

## Validation

The detection was validated using Windows Security Event ID 4732 events collected in Splunk Enterprise.

### Evidence

See:

```text
screenshots/group_membership_changes.png
```
