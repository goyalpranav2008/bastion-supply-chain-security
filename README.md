# bastion-supply-chain-security
Detects supply chain and third-party risk: dependency CVE and typosquatting scanner, ML-based vendor behavior anomaly detection, and a risk scoring dashboard.
# Bastion: Supply Chain & Third-Party Risk Detection

Most big breaches today don't break in through the front door. SolarWinds, Log4Shell and the XZ Utils backdoor all came through software and vendors that victims already trusted.

Bastion is my attempt to guard that trust boundary.

> **Status:** In progress. Building Module 1 first.

## What it will do

1. **Dependency scanner** (`scanner/`)
   Reads a project's dependency files, generates a software bill of materials (SBOM), checks packages against known vulnerabilities, and flags lookalike (typosquatted) package names.

2. **Vendor behavior anomaly detection** (`anomaly/`)
   Uses machine learning on vendor access logs to flag unusual behavior, such as odd login hours, sudden large data downloads, or access to systems a vendor never touched before.

3. **Risk scoring engine** (`risk_engine/`)
   Combines scanner findings and anomaly scores into a single risk score per vendor and maps findings to MITRE ATT&CK (T1195 Supply Chain Compromise, T1199 Trusted Relationship).

4. **Dashboard** (`dashboard/`)
   A Streamlit dashboard showing vendor risk, alerts and the dependency graph, with suggested responses.

## Planned demo

A simulated SolarWinds-style attack: a compromised vendor update brings in a malicious dependency, then the vendor account starts exfiltrating data. Bastion should flag the dependency, detect the behavior change, raise the vendor's risk score and recommend containment.

## Tech stack

Python, scikit-learn, Pandas, Streamlit, SQLite, OSV API, NetworkX

## Project structure

```
scanner/       dependency scan, CVE check, typosquatting
anomaly/       ML for vendor behavior
risk_engine/   risk scoring
dashboard/     Streamlit app
data/          synthetic logs only
docs/          architecture diagram, screenshots
```

## Roadmap

- [ ] Parse dependency files and list packages
- [ ] CVE lookup using OSV
- [ ] Typosquatting detection
- [ ] Generate synthetic vendor logs with injected attacks
- [ ] Train and evaluate anomaly model
- [ ] Risk scoring
- [ ] Dashboard
- [ ] Demo video and write-up

## Notes

All data in this repo is synthetic. This is a learning project and not production security software.

## Author

Pranav Goyal. I'm a student learning cybersecurity by building in public. Progress updates on X: [https://x.com/GoyaprnvGoyal]
