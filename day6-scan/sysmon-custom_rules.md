# Day 6 - Sysmon + Custom Wazuh Rules

**Date**: 2026-06-08
**Status**: Complete

## Objectives
- [x] Deploy Sysmon on Windows endpoint
- [x] Configure Wazuh to ingest Sysmon logs
- [x] Create custom Wazuh rule for Nmap detection (level 10)
- [x] Create custom Wazuh rule for SSH brute force (level 12)
- [x] Test both rules with live attacks

## Sysmon Configuration

| Component | Value |
|-----------|-------|
| Version | Sysmon 64-bit |
| Config | SwiftOnSecurity sysmonconfig-export.xml |
| Service | Sysmon64 |
| Logs | Microsoft-Windows-Sysmon/Operational |

## Custom Rules

### Rule 100001 - Nmap Scan Detection
```xml
<<rule id="100001" level="10">
  <if_sid>1002</if_sid>
  <match>nmap|scan|portscan</match>
  <description>Nmap scan detected on endpoint</description>
  <mitre>
    <id>T1046</id>
  </mitre>
</rule>