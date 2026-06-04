# Incident Report #001 - SSH Brute Force Attempt

**Date**: 2026-06-04
**Analyst**: [Ton nom]
**Status**: Closed - Lab Exercise

## Executive Summary
SSH brute force attack detected on Ubuntu victim (10.0.0.101) from Kali attacker (10.0.0.50). Attack was detected by Wazuh SIEM with rule 5763 (level 10). No successful compromise.

## Timeline
| Time (UTC) | Event |
|------------|-------|
| 11:40:22 | Hydra brute force started from 10.0.0.50 |
| 11:40:22 | Wazuh triggered alert 5763 (level 10) |
| 11:42:15 | Second alert triggered (8 failed attempts) |
| 11:53:01 | Analyst investigation started |

## Technical Details

### Wazuh Alert
```json
{
  "rule": {
    "id": "5763",
    "level": 10,
    "description": "sshd: brute force trying to get access to the system. Authentication failed."
  },
  "agent": {
    "id": "001",
    "name": "linux",
    "ip": "10.0.0.101"
  },
  "data": {
    "srcip": "10.0.0.17",
    "dstuser": "root"
  }
}
=====================================================
MITRE ATT&CK
    Tactic: Credential Access
    Technique: T1110 - Brute Force

=====================================================

Impact Assessment
    Confidentiality: None
    Integrity: None
    Availability: None

=====================================================
Response Actions
[x] Alert confirmed in Wazuh dashboard
[x] Source IP identified: 10.0.0.50 (Kali lab machine)
[x] No successful login detected
