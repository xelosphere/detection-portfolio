![Validate detections](https://github.com/xelosphere/detection-portfolio/actions/workflows/sigma-check.yml/badge.svg)

# Detection Portfolio

A portfolio of detection rules I'm building as I learn detection engineering.
Rules are written in Sigma — a vendor-neutral format — and mapped to MITRE ATT&CK,
so each one can be translated to different SIEM query languages (KQL, SPL, YARA-L).

This is a work in progress. I add detections as I write and fully understand them,
each with a short write-up explaining the technique it catches, the logic, expected
false positives, and how I'd tune it.

## Structure
rules/   detections, organized by MITRE ATT&CK tactic
docs/    write-ups and a template for documenting each detection

## License
MIT — see LICENSE.
