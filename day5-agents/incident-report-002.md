
---

### `day5-windows-nmap/incident-report-002.md`

```markdown
# Incident Report #002 - Network Reconnaissance Detection

**Date**: 2026-06-06
**Analyst**: [Ton nom]
**Status**: Closed - Lab Exercise
**Severity**: Low
**Category**: Reconnaissance / Discovery

## Executive Summary

Network reconnaissance activity detected against Windows endpoint (10.0.0.100) from internal IP 10.0.0.50. Activity identified as Nmap service scanning and OS fingerprinting. No successful intrusion or data exfiltration occurred. Incident contained within isolated lab environment.

## Timeline

| Time (UTC+2) | Event | Source |
|--------------|-------|--------|
| 02:15:00 | Nmap scan initiated | Kali Linux (10.0.0.50) |
| 02:15:03 | TCP SYN packets detected on ports 135, 139, 445 | Windows 10 (10.0.0.100) |
| 02:15:05 | Wazuh alert triggered (rule 1002) | Wazuh Manager (10.0.0.13) |
| 02:15:10 | OS fingerprinting attempt detected | Windows Event Log |
| 02:16:00 | Analyst notified via Wazuh dashboard | SOC Lab |
| 02:20:00 | Investigation initiated | SOC Analyst |
| 02:30:00 | Incident classified as reconnaissance, no compromise | SOC Analyst |

## Technical Details

### Attack Vector
- **Tool**: Nmap 7.94
- **Command**: `nmap -sV -O 10.0.0.100`
- **Source**: Kali Linux (10.0.0.50)
- **Target**: Windows 10 Enterprise (10.0.0.100)
- **Network**: Internal SOC Lab (VMnet1)

### Scanned Ports
| Port | Protocol | Service | State |
|------|----------|---------|-------|
| 135 | TCP | MSRPC | Open |
| 139 | TCP | NetBIOS-SSN | Open |
| 445 | TCP | Microsoft-DS | Open |

### Wazuh Alert Details
```json
{
  "timestamp": "2026-06-06T02:15:05.234+0000",
  "rule": {
    "id": "1002",
    "level": 5,
    "description": "Unknown problem somewhere in the system",
    "groups": ["syslog", "errors"]
  },
  "agent": {
    "id": "003",
    "name": "Windows10",
    "ip": "10.0.0.100"
  },
  "manager": {
    "name": "wazuh-aio"
  }
}