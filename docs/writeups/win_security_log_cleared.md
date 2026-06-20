# Windows Security Event Log Cleared

**Rule file:** `rules/defense_impairment/win_security_log_cleared.yml`
**ATT&CK:** Defense Impairment – T1685.005 (Disable or Modify Tools: Clear Windows Event Logs) (was formerly T1070.001 and was reissued as T1685.005 in ATT&CK v19.)
**Log source:** Windows / Security / Event ID 1102
**Severity:** High

## The technique

The threat actor is clearing logs to hide the activity of an intrustion. They are covering their tracks so none can see what they touched or how they got in to begin with.

## Detection logic

This detection looks for the Windows event 1102 which triggers when the Windows Security audit log is manually cleared. This event ID is enough for this detection as clearing security logs requires high level admin priveleges and must be done manually.

## False positives

An administrator, under a registered administrator account clearing the logs for routine maintenance. Check to see if there is a service ticket put in place for this activity or confirm with the administrator themselves whether this was something they did. Also check to see if this was done during a routine maintenance window.

## Tuning

Excluding known maintenance servers or admin accounts; raising the priority if this activity happens outside business hours or on sensitive systems.

## Translations

Output of `sigma convert` for at least one target platform (SPL and/or KQL).

```spl
# paste converted query here
```
