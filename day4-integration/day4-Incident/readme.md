What we already have

================================================
Component    IP           Status
pfSense      10.0.0.10    ✅
Wazuh        10.0.0.13    ✅
TheHive      10.0.0.20    ❌ Abandoned
================================================

Today’s objective
* Configure Wazuh to send alerts (email/webhook)
* Create an Ubuntu victim VM (10.0.0.101)
* Simulate an SSH brute force attack
* Document the incident in a Markdown report
================================================

| Test                    | Status     | Details                         |
| ----------------------- | ---------- | ------------------------------- |
| Manual script execution | ✅ Success | HTTP 200 returned               |
| Alert parsing           | ✅ Success | Multi-line JSON handled         |
| Brute force detection   | ✅ Success | Rule 5763, level 10             |
| Automatic triggering    | 🔄 Pending | Level threshold tuning required |

================================================

## Progress

| Day | Date | Objective | Status |
|-----|------|-----------|--------|
| 1 | 2026-06-01 | pfSense + Network Setup | ✅ |
| 2 | 2026-06-02 | Wazuh AIO Deployment | ✅ |
| 3 | 2026-06-03 | TheHive + Cortex (Docker, abandoned) | ⚠️ |
| 4 | 2026-06-04 | Webhook Integration + Incident Report #001 | ✅ |
| 5 | 2026-06-05 | Windows Agent + Nmap Detection | ⏳ |
| 6 | 2026-06-06 | Ransomware Simulation + Full IR Playbook | ⏳ |
| 7 | 2026-06-07 | Portfolio Finalization + LinkedIn Post | ⏳ |

=================================================
