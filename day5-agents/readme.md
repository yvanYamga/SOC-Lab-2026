# Day 5 - Windows Agent + Nmap Detection

**Date**: 2026-06-06
**Status**: Complete

## Objectives
- [x] Deploy Windows 10 victim VM
- [x] Install Wazuh agent on Windows
- [x] Troubleshoot agent connection
- [x] Execute Nmap scan from Kali
- [x] Automatic webhook alerting (pending debug)

## Architecture

## VMs Deployed

| VM | IP | OS | Role | Status |
|----|-----|-----|------|--------|
| Win10-Victim | 10.0.0.100 | Windows 10 Pro | Victim | Agent Active |
| Kali-Attacker | 10.0.0.50 | Kali Linux 2024 | Attacker | Operational |
| Ubuntu-Victim | 10.0.0.101 | Ubuntu 22.04 | Victim | Agent Active |
| Wazuh-AIO | 10.0.0.13 | Ubuntu 22.04 | SIEM | Operational |

## Troubleshooting Log

### Issue 1: Windows Agent "Never Connected"
**Symptom**: Agent visible in Wazuh dashboard but status "Never connected"
**Cause**: Windows Firewall blocking ICMP (ping) from Wazuh manager
**Solution**:
```powershell
New-NetFirewallRule -DisplayName "Allow ICMPv4" -Direction Inbound -Protocol ICMPv4 -Action Allow

