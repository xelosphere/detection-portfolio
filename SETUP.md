# Setup

## 1. Install the tools

You'll need [Git](https://git-scm.com/downloads) and Python 3.10+.

Install the Sigma CLI (used to validate and convert rules):

```bash
# pipx is cleanest (keeps it isolated); pip works too
pipx install sigma-cli
# or: pip install sigma-cli

# Add the backends you want to convert to
sigma plugin install splunk
sigma plugin list        # shows all available backends (Sentinel/KQL, etc.)
```

Validate that everything parses:

```bash
sigma check rules/
```

## 2. Put it on GitHub

### Option A — GitHub CLI (fastest)

```bash
cd detection-portfolio
git init
git add .
git commit -m "Initial commit: 5 starter detections"
gh repo create detection-portfolio --public --source=. --remote=origin --push
```

### Option B — Web + git

1. Create a new **public** repo named `detection-portfolio` on github.com (don't add a README — this repo already has one).
2. Then:

```bash
cd detection-portfolio
git init
git add .
git commit -m "Initial commit: 5 starter detections"
git branch -M main
git remote add origin https://github.com/<your-username>/detection-portfolio.git
git push -u origin main
```

## 3. Be ready to work

Your first sessions, in order:

1. Run `sigma check rules/` and confirm all five rules pass.
2. Pick the brute-force write-up in `docs/writeups/` as your model. Write the remaining four using `docs/writeup_template.md`.
3. Convert one rule to SPL and one to KQL, and paste the output into that rule's write-up under a "Translations" heading. That single step is what proves you're platform-agnostic.
4. From then on: one new detection + its write-up per week. Aim for 12–15 documented detections by November.

## A note on tradecraft

Keep these rules tied to public knowledge (ATT&CK, vendor docs, open log-source references). Do not commit anything specific to an employer's environment — no internal hostnames, IP ranges, account names, real log samples, or detection logic that maps to a specific company's infrastructure. This repo is a portfolio of your skills, built entirely from public information.
