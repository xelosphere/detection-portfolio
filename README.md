![Validate detections](https://github.com/xelosphere/detection-portfolio/actions/workflows/sigma-check.yml/badge.svg)

# Detection Portfolio

A growing library of detection content written as platform-agnostic [Sigma](https://sigmahq.io/) rules, each mapped to [MITRE ATT&CK](https://attack.mitre.org/). Every rule is documented with the technique it catches, the logic behind it, expected false positives, and tuning notes.

The goal isn't to collect rules — it's to demonstrate detection-engineering thinking: starting from an attacker technique, understanding the relevant log source, writing logic that catches the behavior, and reasoning about fidelity and tuning.

## Why Sigma

Sigma is a vendor-neutral detection format. One rule here converts to KQL (Microsoft Sentinel / Defender), SPL (Splunk), YARA-L (Google SecOps), and more, using the [sigma CLI](https://github.com/SigmaHQ/sigma-cli). Writing detections once and translating them across platforms is the core skill of a modern detection engineer.

## Structure

```
rules/                  Detections, organized by MITRE ATT&CK tactic
  credential_access/
  execution/
  defense_evasion/
  persistence/
  initial_access/
docs/
  writeup_template.md   Template for documenting a detection
  writeups/             One write-up per rule
```

## Detections

| Detection | Tactic | Technique | Log source |
|---|---|---|---|
| Brute force – multiple failed logons | Credential Access | T1110.001 | Windows Security (4625) |
| Encoded PowerShell command | Execution | T1059.001 / T1027 | Windows process creation |
| Security event log cleared | Defense Evasion | T1070.001 | Windows Security (1102) |
| User added to local Administrators | Persistence / Priv-Esc | T1098 / T1078.003 | Windows Security (4732) |
| Successful risky Entra ID sign-in | Initial Access | T1078.004 | Entra ID sign-in logs |

## Validate and convert

```bash
# Validate all rules parse correctly
sigma check rules/

# Convert a rule to Splunk SPL
sigma convert -t splunk rules/execution/win_process_powershell_encoded_command.yml

# List available backends to find the right target for KQL / SecOps
sigma plugin list
```

See [SETUP.md](SETUP.md) for getting the tooling installed and pushing this repo to GitHub.

## License

MIT — see [LICENSE](LICENSE).
