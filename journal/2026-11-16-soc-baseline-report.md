# SOC Baseline Report — Kali Workstation

**Date:** 2026-11-16
**Analyst:** kali-analyst (agent 001)
**Manager:** 10.10.10.1 (Wazuh 4.9.0, Docker)

## Scope
Continuous monitoring of Kali Linux (10.10.10.179) — the analyst
workstation. Events collected: authentication, sudo, package
management, file integrity, system inventory.

## Event Volume (baseline period)
Total alerts indexed: 301

## Notable Event Types
| Rule | Description | Frequency |
|------|-------------|-----------|
| 5501 | PAM: Login session opened | multiple |
| 5502 | PAM: Login session closed | multiple |
| 5402 | Successful sudo to ROOT | multiple |
| 2902 | New dpkg package installed | 1+ |

## MITRE ATT&CK Coverage
- T1078 — Valid Accounts (PAM sessions)
- T1548.003 — Abuse Elevation (sudo)
- T1072 — Software Deployment Tools (dpkg)

## Observations
- All sudo events are expected (analyst work)
- Package install (`sl`) is expected baseline noise
- No anomalies requiring investigation in this baseline

## Next Steps
1. Add an Ubuntu 22.04 "monitored server" VM at 10.10.20.60
2. Enable SSH brute-force detection rules on that host
3. Run detection validation exercises:
   - 5 failed SSH logins → expect rule 5760
   - `useradd` in monitored file → expect rule 550
4. Build a Grafana dashboard for visual trend analysis
