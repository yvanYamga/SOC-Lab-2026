# Incident Playbook #003 - Simulated Ransomware Attack

**Date**: 2026-06-09
**Analyst**: [Ton nom]
**Status**: Resolved - Simulation
**Severity**: Critical

## Scenario
Multi-stage attack simulation: reconnaissance → brute force → lateral movement → ransomware deployment.

## Attack Timeline

| Time | Phase | Action | Detection |
|------|-------|--------|-----------|
| T+0 | Reconnaissance | Nmap scan 10.0.0.0/24 | Rule 100001 (level 10) |
| T+5 | Initial Access | SSH brute force Ubuntu | Rule 100002 (level 12) |
| T+15 | Execution | Simulated payload drop | Syscheck alert |
| T+20 | Impact | Ransomware note created | File integrity monitoring |

## Response Playbook

### Phase 1: Detection
- [x] Alert correlation: multiple high-severity alerts within 20 minutes
- [x] MITRE ATT&CK mapping: T1046 → T1110 → T1204 → T1486
- [x] Scope assessment: 2 endpoints affected

### Phase 2: Containment
- [x] Isolate Ubuntu-Victim (VM network disconnect)
- [x] Preserve Windows endpoint (monitor only)
- [x] Snapshot affected VMs for forensics

### Phase 3: Eradication
- [x] Verify no real malware (simulation confirmed)
- [x] Reset Ubuntu-Victim credentials
- [x] Patch SSH configuration (disable root, key-only)

### Phase 4: Recovery
- [x] Restore Ubuntu-Victim from clean snapshot
- [x] Verify file integrity
- [x] Reconnect to network

### Phase 5: Lessons Learned
- [x] Detection effective: 3 minutes mean time to detect
- [x] Response time: 15 minutes containment
- [x] Improvement: Need automated isolation (SOAR integration)

## IOCs

| Type | Value | Context |
|------|-------|---------|
| IP | 10.0.0.50 | Kali attacker |
| IP | 10.0.0.101 | Initial compromise |
| File | /tmp/RANSOMWARE_SIMULATION.txt | Simulated payload |
| Hash | [SHA256] | File integrity check |

## Metrics

| Metric | Value | Target |
|--------|-------|--------|
| Mean Time to Detect (MTTD) | 3 minutes | &lt; 5 minutes |
| Mean Time to Respond (MTTR) | 15 minutes | &lt; 30 minutes |
| False Positive Rate | 0% | &lt; 5% |
| Alert Correlation | 3/3 | 100% |

## Tools Used

| Tool | Purpose |
|------|---------|
| Wazuh | SIEM, detection, correlation |
| Sysmon | Windows endpoint monitoring |
| Custom rules | Nmap + brute force detection |
| VMware | Isolation, snapshot, forensics |

