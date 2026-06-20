# <Detection name>

**Rule file:** `rules/<tactic>/<file>.yml`
**ATT&CK:** <Tactic> – <Technique ID and name>
**Log source:** <product / service / event IDs>
**Severity:** <level>

## The technique

What is the adversary doing, and why? Describe the behavior in plain language and link it to the ATT&CK technique.

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
