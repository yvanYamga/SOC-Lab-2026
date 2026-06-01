# Day 1 - Network Architecture

## Physical Host
- MacBook Pro, Intel Core i7 9th Gen, 2.6GHz
- 30GB RAM, 200GB HDD
- Windows 11 via Boot Camp
- VMware Workstation 17 Pro

## VMware Network Configuration

### Virtual Network Editor
| VMnet | Type | Subnet | DHCP VMware | Usage |
|-------|------|--------|-------------|-------|
| VMnet0 | Bridged | Auto | N/A | pfSense WAN → Internet |
| VMnet1 | Host-Only | 10.0.0.0/24 | **Disabled** | SOC LAN (all VMs) |

### Why Disable VMware DHCP?
pfSense acts as the sole DHCP server for the SOC network. Enabling VMware DHCP on VMnet1 would create IP conflicts.

## pfSense Configuration

| Interface | VMware Adapter | IP | Role |
|-----------|---------------|-----|------|
| WAN (em0) | Bridged (VMnet0) | DHCP from home router | Internet access |
| LAN (em1) | Host-Only (VMnet1) | **10.0.0.10/24** | Internal SOC network |

### DHCP Range
- Start: **10.0.0.5**
- End: **10.0.0.50**
- Gateway: **10.0.0.10**
- DNS: 8.8.8.8, 1.1.1.1

## IP Allocation Table

| VM | IP | Role |
|----|-----|------|
| pfSense LAN | **10.0.0.10** | Gateway/DHCP/DNS |
| Kali Linux | 10.0.0.5 | Attacker/Pentest (DHCP) |
| Wazuh AIO | 10.0.0.11 | SIEM/EDR (static) |
| TheHive + Cortex | 10.0.0.20 | Case Management (static) |
| Cortex Analyzers | 10.0.0.21 | Threat Intelligence (static) |
| Windows 10 Victim | 10.0.0.100 | Windows endpoint (static) |
| Ubuntu Server Victim | 10.0.0.101 | Linux endpoint/Syslog (static) |

## Diagram
