# Volume Shadow Copy Deletion via Vssadmin

**Rule file:** `rules/impact/win_vssadmin_shadow_copy_deletion.ym`
**ATT&CK:** Impact – T1685.005 (Inhibit System Recovery)
**Log source:** Windows / Process Creation / vssadmin.exe
**Severity:** High

## The technique



## Detection logic

Walk through what the rule actually matches and why those fields/values. Explain any thresholds or correlation.

## False positives

What benign activity looks similar, and how an analyst should distinguish it during triage.

## Tuning

How you'd reduce noise in a real environment (baselining, allow-lists, additional context, parent-process filtering, etc.).

## Translations

Output of `sigma convert` for at least one target platform (SPL and/or KQL).

```spl
# paste converted query here
```
