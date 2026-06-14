# Failed Logons Detection

## Description

Detects failed Windows authentication attempts using Security Event ID 4625.

## SPL Query

```spl
index=* EventCode=4625