# Brute Force – Multiple Failed Logons

**Rule file:** `rules/credential_access/win_security_brute_force_failed_logons.yml`
**ATT&CK:** Credential Access – T1110.001 (Brute Force: Password Guessing)
**Log source:** Windows Security log, Event ID 4625 (failed logon)
**Severity:** High (correlation rule)

## The technique

An attacker who has a valid username but not the password will try many passwords in quick succession (guessing), or try one common password against many accounts (spraying). Both generate a burst of failed authentication events. T1110.001 covers the guessing variant against a single account.

## Detection logic

This detection is built in two parts, which is the important lesson:

- A **base rule** (`win_failed_logon`) matches a single Event ID 4625. By itself this fires constantly and is useless as an alert — it's set to `informational` on purpose.
- A **correlation rule** counts those events, grouped by `TargetUserName` and `Computer`, and fires when there are **10 or more within 5 minutes**. That threshold + grouping is what turns raw noise into a real signal.

The takeaway: a field match is not a detection. Context — count, time window, what you group by — is what makes it one.

## False positives

- A user who recently changed their password while a phone, mapped drive, or scheduled task still holds the old one can rack up failures fast.
- Service accounts with expired credentials retrying in a loop look identical to spraying.

During triage, check whether the failures come from one source, one logon type, and whether the account is a service account. A human guessing and a broken service have very different shapes.

## Tuning

- Baseline your environment first — some shops legitimately see more than 10 failures in 5 minutes for shared kiosks. Raise the threshold or exclude those hosts.
- Split logon types (`LogonType`) — network (3) vs interactive (2) behave differently.
- Pair with a follow-on **successful** logon (4624) for the same account to catch a guess that eventually worked; that combination is a much higher-fidelity alert.

## Translations

Convert with: `sigma convert -t splunk rules/credential_access/win_security_brute_force_failed_logons.yml`

```spl
# paste the sigma CLI output here once you've installed the splunk backend
```
