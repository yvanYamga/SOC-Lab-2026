
---

### `day5-windows-nmap/debugging-agents.md`

```markdown
# Debugging Agent Connection Issues

## Problem Statement
Multiple agent connection failures during Windows endpoint deployment.

## Diagnostic Timeline

| Time | Observation | Action |
|------|-------------|--------|
| 01:07 | Windows agent "Never connected" | Checked Windows Firewall |
| 01:15 | Linux agent also "Disconnected" | Expanded investigation |
| 01:25 | IP config verified correct | Eliminated network issue |
| 01:30 | Firewall verified inactive | Eliminated firewall issue |
| 01:35 | Manager ports not listening | Checked manager status |
| 01:38 | XML config error found | Fixed ossec.conf syntax |
| 01:40 | Both agents "Active" | Confirmed resolution |

## Root Cause Analysis

### Primary Cause
XML syntax error in `/var/ossec/etc/ossec.conf` from webhook integration configuration.

### Error Details
```xml
<!-- INCORRECT -->
<<hook_url>https://webhook.site/...</hook_url>

<!-- CORRECT -->
<<hook_url>https://webhook.site/...</hook_url>