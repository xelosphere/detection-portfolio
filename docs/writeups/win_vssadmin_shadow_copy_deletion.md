# Volume Shadow Copy Deletion via Vssadmin

**Rule file:** `rules/impact/win_vssadmin_shadow_copy_deletion.ym`
**ATT&CK:** Impact – T1490 (Inhibit System Recovery)
**Log source:** Windows / Process Creation / vssadmin.exe
**Severity:** High

## The technique

Adversaries will oftentimes delete backups on computers to prevent easy recovery of data, as is the case in most ransomeware, to pressure victims into paying.

## Detection logic

This detection looks for anyone running vssadmin.exe, regardless of the full path, and looks specifically for a command contains both the words "delete" and "shadows."

## False positives

An administrator, under a registered administrator account clearing the backups for routine maintenance. Check to see if there is a service ticket put in place for this activity or confirm with the administrator themselves whether this was something they did. Also check to see if this was done during a routine maintenance window. The most common benign trigger is usually backup or imagine software doing this atuomatically.

## Tuning

This rule catches the most common path, but attackers may use other tools to delete shadow copies such as "wbadmin, bcdedit, etc."

## Translations

Output of `sigma convert` for at least one target platform (SPL and/or KQL).

```spl
# paste converted query here
```
